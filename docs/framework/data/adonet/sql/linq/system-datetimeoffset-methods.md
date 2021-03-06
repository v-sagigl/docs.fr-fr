---
title: System.DateTimeOffset, méthodes
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 288a0d99feecdeccc0d215ec3c14ec31bb3ccb54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876900"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset, méthodes
Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler la plupart des méthodes, opérateurs et propriétés <xref:System.DateTimeOffset?displayProperty=nameWithType> à partir des requêtes LINQ to SQL.  
  
 Les seules méthodes non prises en charge sont celles héritées de <xref:System.Object?displayProperty=nameWithType> qui n'ont pas de sens dans le contexte des requêtes LINQ to SQL, telles que `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`. Ces méthodes ne sont pas prises en charge car LINQ to SQL ne peut pas les traduire à des fins d'exécution sur SQL Server.  
  
> [!NOTE]
>  La structure <xref:System.DateTimeOffset?displayProperty=nameWithType> CLR (Common Language Runtime), ainsi que la capacité à la mapper à une colonne `DATETIMEOFFSET` SQL à l'aide de LINQ to SQL, requiert le .NET Framework 3.5 SP1 ou version ultérieure. La colonne `DATETIMEOFFSET` SQL est uniquement disponible à partir de Microsoft SQL Server 2008.  
  
## <a name="sqlmethods-date-and-time-methods"></a>Méthodes de date et d'heure SQLMethods  
 Outre les méthodes proposées par la structure <xref:System.DateTimeOffset>, LINQ to SQL fournit également celles répertoriées dans le tableau suivant à partir de la classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> pour l'utilisation des données de date et d'heure.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mappage de type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
