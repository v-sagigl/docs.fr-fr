---
title: La classe déléguée '<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803634"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Classe déléguée\<nom_classe >' n’a aucun méthode Invoke, donc une expression de ce type ne peut pas être la cible d’un appel de méthode
Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémentée sur la classe déléguée.  
  
 **ID d’erreur :** BC30220  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez qu’une instance de la classe déléguée a été créée avec un `Dim` instruction et qu’une procédure a été assignée à l’instance de délégué avec le `AddressOf` opérateur.  
  
2. Recherchez le code qui implémente la classe déléguée et vérifiez qu’il implémente la `Invoke` procédure.  
  
## <a name="see-also"></a>Voir aussi

- [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
