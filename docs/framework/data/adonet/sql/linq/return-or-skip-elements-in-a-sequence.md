---
title: "Comment : retourner ou ignorer des éléments d'une séquence"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: bedb6df564e4301ec8009992ec0ec5c51de729e0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910825"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Comment : retourner ou ignorer des éléments d'une séquence
Utilisez l'opérateur <xref:System.Linq.Queryable.Take%2A> pour retourner un nombre donné d'éléments dans une séquence et ignorer le reste.  
  
 Utilisez l'opérateur <xref:System.Linq.Queryable.Skip%2A> pour ignorer un nombre donné d'éléments dans une séquence et retourner le reste.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> sont soumis à certaines limites lorsqu'ils sont utilisés dans des requêtes SQL Server 2000. Pour plus d’informations, consultez l’entrée « Skip et Take des Exceptions dans SQL Server 2000 » dans [dépannage](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit <xref:System.Linq.Queryable.Skip%2A> à l’aide d’une sous-requête avec le code SQL `NOT EXISTS` clause. Cette traduction présente les limites suivantes :  
  
- L’argument doit être un jeu. Les multijeux ne sont pas pris en charge, même s'ils sont ordonnés.  
  
- La requête générée peut être beaucoup plus complexe que celle qui est générée pour la requête de base sur laquelle <xref:System.Linq.Queryable.Skip%2A> est appliqué. Cette complexité peut entraîner une dégradation des performances ou un délai d'expiration.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise `Take` pour sélectionner les cinq premiers `Employees` embauchés. Notez que la collection est d’abord triée par `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Queryable.Skip%2A> pour sélectionner tous les `Products` exceptés les dix produits les plus chers.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant combine les méthodes <xref:System.Linq.Queryable.Skip%2A> et <xref:System.Linq.Queryable.Take%2A> pour ignorer les cinquante premiers enregistrements et retourner les dix suivants.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 Les opérations <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont bien définies uniquement sur les jeux ordonnés. La sémantique des jeux ou des multijeux non ordonnés n'est pas définie.  
  
 Du fait des limitations de classement dans SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tente de déplacer le classement de l'argument de l'opérateur <xref:System.Linq.Queryable.Take%2A> ou <xref:System.Linq.Queryable.Skip%2A> vers le résultat de l'opérateur.  
  
> [!NOTE]
>  La traduction est différente pour [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] et [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Si vous envisagez d'utiliser <xref:System.Linq.Queryable.Skip%2A> avec une requête d'un niveau de complexité quelconque, utilisez [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Considérez la requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suivante pour [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] :  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] déplace le classement à la fin du code SQL, comme suit :  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 Lorsque <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont enchaînés, l'ensemble du classement spécifié doit être cohérent. Si ce n'est pas le cas, les résultats ne sont pas définis.  
  
 Pour les arguments intégraux constants non négatifs basés sur la spécification SQL, <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont bien définis.  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
