---
title: Практическое руководство. Вычисление промежуточных значений (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: cb619784d487ae12b1fb8bb3adc97acb0f767455
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827046"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a>Практическое руководство. Вычисление промежуточных значений (Visual Basic)
В этом примере показано, как вычислять промежуточные значения, которые используются в сортировке, фильтрации и выборке.  
  
## <a name="example"></a>Пример  
 В следующем примере используется предложение `Let`.  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Числовые данные (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 Этот код выводит следующие результаты:  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует тот же запрос XML, что и в пространстве имен. Дополнительные сведения см. в разделе [работа с пространствами имен XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Числовые данные в пространстве имен](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 Этот код выводит следующие результаты:  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a>См. также

- [Базовые запросы (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
