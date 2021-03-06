---
title: 'Procédure : Interroger un ArrayList avec LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: ed440a7970d0ef1a49af36fa56b1c7ca74715e5f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908165"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Procédure : Interroger un ArrayList avec LINQ (Visual Basic)
Quand vous utilisez LINQ pour interroger des collections <xref:System.Collections.IEnumerable> non génériques telles que <xref:System.Collections.ArrayList>, vous devez déclarer explicitement le type de la variable de portée pour qu’il reflète le type spécifique des objets de la collection. Par exemple, si vous avez un <xref:System.Collections.ArrayList> de `Student` objets, votre [Clause From](../../../../visual-basic/language-reference/queries/from-clause.md) doit ressembler à ceci :  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 En spécifiant le type de la variable de portée, vous effectuez un cast de chaque élément du `Student` en <xref:System.Collections.ArrayList>.  
  
 L’utilisation d’une variable de portée explicitement typée dans une expression de requête équivaut à appeler la méthode <xref:System.Linq.Enumerable.Cast%2A>. <xref:System.Linq.Enumerable.Cast%2A> lève une exception si le cast spécifié ne peut pas être effectué. <xref:System.Linq.Enumerable.Cast%2A> et <xref:System.Linq.Enumerable.OfType%2A> sont les deux méthodes d’opérateur de requête standard qui fonctionnent sur les types <xref:System.Collections.IEnumerable> non génériques. En Visual Basic, vous devez appeler explicitement la <xref:System.Linq.Enumerable.Cast%2A> méthode sur la source de données pour garantir un type de variable de plage spécifique. Pour plus d’informations, consultez [relations des types dans les opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une requête simple sur un <xref:System.Collections.ArrayList>. Notez que cet exemple utilise des initialiseurs d’objets quand le code appelle la méthode <xref:System.Collections.ArrayList.Add%2A>, mais cela n’est pas une obligation.  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
