---
title: Modèle asynchrone basé sur les événements (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052773c615bcc4ddb5b735ae8164d44ed70bd935
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513488"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Modèle asynchrone basé sur les événements (EAP)

Il existe plusieurs façons d’exposer des fonctionnalités asynchrones à du code client. Le modèle asynchrone basé sur les événements recommande une méthode pour obtenir des classes un comportement asynchrone.  
  
> [!NOTE]
> À compter du .NET Framework 4, la bibliothèque parallèle de tâches propose un nouveau modèle pour la programmation asynchrone et parallèle. Pour plus d’informations, consultez [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md) et [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>Dans cette section

 [Vue d’ensemble du modèle asynchrone basé sur les événements](event-based-asynchronous-pattern-overview.md)  
 Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.  
  
 [Implémentation du modèle asynchrone basé sur les événements](implementing-the-event-based-asynchronous-pattern.md)  
 Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.  
  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Décrit les exigences liées à l’exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.  
  
 [Choix du moment auquel implémenter le modèle asynchrone basé sur les événements](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Explique comment savoir quand vous devez implémenter le modèle asynchrone basé sur les événements au lieu du modèle <xref:System.IAsyncResult> représenté par le [ modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md).
  
 [Guide pratique pour implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Décrit comment créer un composant qui implémente le modèle asynchrone basé sur les événements. Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.  

 [Guide pratique pour implémenter un client du modèle asynchrone basé sur des événements](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Décrit comment créer un client qui utilise un composant implémentant le modèle asynchrone basé sur les événements.
  
 [Guide pratique pour utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.  
  
## <a name="reference"></a>Référence

 <xref:System.ComponentModel.AsyncOperation>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.  
  
## <a name="related-sections"></a>Rubriques connexes

 [La bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md)  
 Décrit un modèle de programmation pour les opérations asynchrones et parallèles.  
  
 [Thread](../../../docs/standard/threading/index.md)  
 Décrit les fonctionnalités de multithreading dans .NET.  
  
## <a name="see-also"></a>Voir aussi

- [Bonnes pratiques de threading géré](../threading/managed-threading-best-practices.md)
- [Événements](../events/index.md)
- [Modèles de conception de la programmation asynchrone](index.md)
