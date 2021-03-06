---
title: Architecture Windows Workflow
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: d341ebd354d5324c5ad71436837cb85737f46c08
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605898"
---
# <a name="windows-workflow-architecture"></a>Architecture Windows Workflow
Windows Workflow Foundation (WF) déclenche le niveau d’abstraction pour le développement d’applications interactives de longs. Les unités de travail sont encapsulées comme activités. Les activités s’exécutent dans un environnement qui fournit les fonctions suivantes : contrôle de flux, gestion des exceptions, propagation d’erreur, persistance des données d’état, chargement et déchargement de flux de travail en cours depuis la mémoire, suivi et flux de transaction.  
  
## <a name="activity-architecture"></a>Architecture des activités  
 Les activités sont développées comme types CLR qui dérivent soit des objets <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> ou <xref:System.Activities.NativeActivity>, soit de leurs variantes <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> ou <xref:System.Activities.NativeActivity%601>. En développant des activités qui dérivent de l'objet <xref:System.Activities.Activity>, l'utilisateur peut assembler des activités préexistantes pour développer rapidement des unités de travail qui s'exécutent dans l'environnement de workflow. L'objet <xref:System.Activities.CodeActivity> permet quant à lui de créer la logique d'exécution en code managé, en utilisant l'objet <xref:System.Activities.CodeActivityContext> principalement pour accéder aux arguments d'activité. <xref:System.Activities.AsyncCodeActivity> est semblable à <xref:System.Activities.CodeActivity>, mais peut être utilisé pour implémenter des tâches asynchrones. En développant des activités qui dérivent de l'objet <xref:System.Activities.NativeActivity>, les utilisateurs peuvent accéder au runtime via l'objet <xref:System.Activities.NativeActivityContext> pour des fonctionnalités telles que la planification d'activités enfants, la création de signets, l'appel de travail asynchrone, l'enregistrement de transactions, etc.  
  
 La création d'activités qui dérivent de l'objet <xref:System.Activities.Activity> est déclarative et ces activités peuvent être créées en XAML. Dans l'exemple suivant, une activité appelée `Prompt` est créée à l'aide d'autres activités pour le corps d'exécution.  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>Contexte de l'activité  
 <xref:System.Activities.ActivityContext> est l'interface de l'auteur d'activité avec l'exécution du workflow. Elle permet d'accéder aux nombreuses fonctionnalités du runtime. L'exemple suivant consiste à définir une activité qui utilise le contexte d'exécution pour créer un signet (mécanisme qui permet à une activité d'enregistrer un point de continuation dans son exécution qui peut être reprise par un hôte passant des données dans l'activité).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Cycle de vie des activités  
 À l'origine, l'instance d'une activité est à l'état <xref:System.Activities.ActivityInstanceState.Executing>. À moins que des exceptions ne soient rencontrées, elle conserve cet état jusqu'à ce que l'exécution de toutes les activités enfants, ainsi que tout autre travail en attente (objets <xref:System.Activities.Bookmark>, par exemple) soient terminés, auquel cas elle passe à l'état <xref:System.Activities.ActivityInstanceState.Closed>. Le parent d'une instance d'activité peut demander qu'un enfant soit annulé. Si l'enfant est en mesure d'être annulé, il se termine et passe à l'état <xref:System.Activities.ActivityInstanceState.Canceled>. Si une exception est levée lors de l'exécution, le runtime passe l'activité à l'état objet <xref:System.Activities.ActivityInstanceState.Faulted> et propage l'exception en haut de la chaîne parente d'activités. Voici les trois états d'achèvement d'une activité :  
  
- **Fermé :** L’activité a terminé son travail et s’est arrêté.  
  
- **Annulée :** L’activité a correctement abandonné son travail et s’est arrêté. Le travail n'est pas restauré explicitement lorsque cet état est entré.  
  
- **A généré une erreur :** L’activité a rencontré une erreur et s’est arrêtée sans terminer son travail.  
  
 Les activités restent à l'état <xref:System.Activities.ActivityInstanceState.Executing> lorsqu'elles sont rendues persistantes ou sont déchargées.
