---
title: Niveaux et mots clés ETW du CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a9061503ae4bf68903f35eb7624deed2f34c9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616610"
---
# <a name="clr-etw-keywords-and-levels"></a>Niveaux et mots clés ETW du CLR
<a name="top"></a> Les événements de suivi d'événements pour Windows (ETW) peuvent être filtrés par catégorie et par niveau. Les [Mots clés ETW du CLR](#keywords) d’événement permettent de filtrer les événements par catégorie. Ils sont utilisés sous forme de combinaisons pour les fournisseurs d’arrêt et de runtime. Les [niveaux d'événement](#levels) sont identifiés par des indicateurs.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>Mots clés ETW du CLR  
 Les mots clés sont des indicateurs qui peuvent être combinés pour générer des valeurs. Dans la pratique, vous utilisez les valeurs hexadécimales des mots clés au lieu de leurs noms lorsque vous appelez des utilitaires en ligne de commande.  
  
 Les mots clés sont décrits dans les tableaux suivants :  
  
- [Mots clés de runtime ETW du CLR](#runtime)  
  
- [Mots clés d’arrêt ETW du CLR](#rundown)  
  
- [Combinaisons de mots clés pour la résolution des symboles pour le fournisseur de runtime](#runtime_combo)  
  
- [Combinaisons de mots clés pour la résolution des symboles pour le fournisseur d’arrêt](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Mots clés de runtime ETW du CLR  
 Le tableau suivant répertorie les mots clés de runtime ETW du CLR, leurs valeurs et leur usage.  
  
|Nom du mot clé de runtime|Value|Objectif|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Active la collecte d' [événements de garbage collection](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Active la collecte d’ [événements de chargeur](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Active la collecte d’ [événements juste-à-temps (JIT)](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Active la collecte d'événements pour les méthodes d'images natives (méthodes traitées par le générateur d'images natives, Ngen.exe) ; utilisé avec `StartEnumerationKeyword` et `EndEnumerationKeyword`. Ce mot clé possède une charge mémoire élevée. Il génère des événements pour chaque méthode à l'intérieur de chaque module NGen chargé. Si possible, au lieu d'utiliser ce mot clé, nous vous recommandons d'utiliser les bases de données de programme (PDB) générées par les outils de profilage pour récupérer des informations sur les méthodes à partir des modules NGen. Voir aussi `OverrideAndSuppressNGenEventsKeyword` plus bas dans ce tableau.|  
|`StartEnumerationKeyword`|0x00000040|Active l'énumération de toutes les méthodes dans le runtime ; utilisé conjointement à `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Active l'énumération de toutes les méthodes détruites dans le runtime ; utilisé conjointement à `JITKeyword` et `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Active la collecte d’ [événements de sécurité](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Active la collecte d'événements d’analyse de ressource au niveau d'un domaine d'application.|  
|`JITTracingKeyword`|0x00001000|Active la collecte d’ [événements de traçage JIT](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Active la collecte d’ [événements d’interopérabilité](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Active la collecte d’ [événements de conflit](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Active la collecte d’ [événements d’exception](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Active la collecte d’ [événements de pool de threads](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Disponible dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et les versions ultérieures.) Supprime le mot clé de charge mémoire élevée `NGenKeyword` et empêche la génération d'événements pour les méthodes internes aux modules NGen. À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les outils de profilage doivent utiliser `OverrideAndSuppressNGenEventsKeyword` et `NGenKeyword` ensemble pour supprimer la génération des événements pour les méthodes dans les modules NGen. Cela permet à l'outil de profilage d’utiliser les fichiers PDB NGen plus efficaces pour obtenir des informations sur les méthodes dans les modules NGen. Le CLR dans le .NET Framework 4 et versions antérieures ne prend pas en charge la création de fichiers PDB NGen. Dans les versions antérieures, le CLR ne reconnaîtra pas `OverrideAndSuppressNGenEventsKeyword` et traitera `NGenKeyword` pour générer des événements pour les méthodes dans les modules NGen.|  
|`PerfTrackKeyWord`|0x2000000|Active la collecte des événements `ModuleLoad` et `ModuleRange` .|  
|`StackKeyword`|0x40000000|Active la collecte des [événements de trace de la pile](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Retour au début](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Mots clés d’arrêt ETW du CLR  
 Le tableau suivant répertorie les mots clés d’arrêt ETW du CLR, leurs valeurs et leur usage.  
  
|Nom du mot clé d’arrêt|Value|Objectif|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Active la collecte d’événements de chargeur quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Active la collecte des événements `DCStart` et `DCEnd` de méthode pour les méthodes compilées juste-à-temps (JIT) quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Active la collecte des événements `DCStart` et `DCEnd` de méthode pour les méthodes d’images natives NGen quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`. Ce mot clé possède une charge mémoire élevée. Il génère des événements pour chaque méthode à l'intérieur de chaque module NGen chargé. Si possible, au lieu d'utiliser ce mot clé, nous vous recommandons d'utiliser les bases de données de programme (PDB) générées par les outils de profilage pour récupérer des informations sur les méthodes à partir des modules NGen. Voir aussi `OverrideAndSuppressNGenEventsRundownKeyword` plus bas dans ce tableau.|  
|`StartRundownKeyword`|0x00000040|Active l'énumération de l'état du système pendant un arrêt de début.|  
|`EndRundownKeyword`|0x00000100|Active l'énumération de l'état du système pendant un arrêt de fin.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Active la collecte d'événements d'analyse de ressource à un niveau <xref:System.AppDomain> lorsqu'il est utilisé avec `StartRundownKeyword` ou `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Active la collecte d’événements de pool de threads.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Disponible dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et les versions ultérieures.) Supprime le mot clé de charge mémoire élevée `NGenRundownKeyword` et empêche la génération d'événements pour les méthodes internes aux modules NGen. À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les outils de profilage doivent utiliser `OverrideAndSuppressNGenEventsRundownKeyword` et `NGenRundownKeyword` ensemble pour supprimer la génération des événements pour les méthodes dans les modules NGen. Cela permet à l'outil de profilage d’utiliser les fichiers PDB NGen plus efficaces pour obtenir des informations sur les méthodes dans les modules NGen. Le CLR dans le .NET Framework 4 et versions antérieures ne prend pas en charge la création de fichiers PDB NGen. Dans les versions antérieures, le CLR ne reconnaîtra pas `OverrideAndSuppressNGenEventsRundownKeyword` et traitera `NGenRundownKeyword` pour générer des événements pour les méthodes dans les modules NGen.|  
|`PerfTrackKeyWord`|0x2000000|Active la collecte des événements `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`et `ModuleRangeDCEnd` .|  
  
 [Retour au début](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Combinaisons de mots clés pour la résolution des symboles pour le fournisseur de runtime  
  
|Mots clés et indicateurs|Domaine d'application, assembly, événements de chargement/déchargement de module|Événements de chargement/déchargement de méthode (sauf événements dynamiques)|Événements de chargement/destruction de méthode dynamique|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Événements de chargement et déchargement.|Aucun.|Aucun.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` n'ajoute rien)|Aucun.|Événements de chargement.|Événements de chargement et déchargement.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Aucun.|Événements de chargement et déchargement.|Événements de chargement et déchargement.|  
|`NGenKeyword`|Aucun.|Aucun(e).|Non applicable.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Aucun.|Événements de chargement.|Non applicable.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Aucun.|Événements de déchargement.|Non applicable.|  
  
 [Retour au début](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Combinaisons de mots clés pour la résolution des symboles pour le fournisseur d’arrêt  
  
|Mots clés et indicateurs|Domaine d'application, assembly, événements DCStart/DCEnd de module|Événements DCStart/DCEnd de méthode (y compris les événements de méthode dynamique)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|Événements`DCStart` .|Aucun.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|Événements`DCEnd` .|Aucun.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Aucun.|Événements`DCStart` .|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Aucun.|Événements`DCEnd` .|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Aucun.|Événements`DCStart` .|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Aucun.|Événements`DCEnd` .|  
  
 [Retour au début](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Niveaux d'événement ETW  
 Les événements ETW peuvent également être filtrés par niveau. Si le niveau est défini sur 0x5, les événements de tous les niveaux, y compris 0x5 et inférieurs (qui sont des événements qui appartiennent aux catégories activées via des mots clés), sont déclenchés. Si le niveau est défini sur 0x2, seuls les événements de niveau 0x2 et inférieurs sont déclenchés.  
  
 Les niveaux ont les significations suivantes :  
  
 0x5 - Détaillé  
  
 0x4 - Informatif  
  
 0x3 - Avertissement  
  
 0x2 - Erreur  
  
 0x1 - Critique  
  
 0x0 - Toujours journaliser  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs ETW du CLR](../../../docs/framework/performance/clr-etw-providers.md)
- [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
- [Événements ETW dans le Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
