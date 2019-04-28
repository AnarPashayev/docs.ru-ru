---
title: Статически скомпилированные запросы (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ff708dd14d27b34be797f1630dabe27a56c5a219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908340"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Статически скомпилированные запросы (LINQ to XML) (Visual Basic)
Одним из важнейших преимуществ LINQ to XML перед <xref:System.Xml.XmlDocument> с точки зрения производительности является то, что в LINQ to XML запросы компилируются статически, тогда как запросы XPath интерпретируются во время выполнения. Это встроенная функция LINQ to XML, поэтому вам не нужно будет принимать какие-либо подготовительные меры для ее использования, однако, чтобы сделать обоснованный выбор той или другой технологии, важно понимать их различие. Данное различие описано в текущем разделе.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Сравнение статически скомпилированных запросов и языка XPath  
 В следующем примере показано, как получать элементы-потомки с указанным именем и атрибут с заданным значением.  
  
 Далее представлено эквивалентное выражение XPath.  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Компилятор переписывает выражение запроса из этого примера с использованием синтаксиса запросов, основанных на методах. Код в следующем примере имеет синтаксис запросов, основанных на методах и приводит к получению таких же результатов, что и предыдущий код.  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 Метод <xref:System.Linq.Enumerable.Where%2A> является методом расширения. Дополнительные сведения см. в статье [Методы расширения](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Поскольку используется метод расширения <xref:System.Linq.Enumerable.Where%2A>, представленный выше запрос компилируется так, как показано далее.  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Этот пример приводит к получению в точности таких же результатов, что и два предыдущих примера. Таким образом, демонстрируется возможность эффективной компиляции запросов в вызовы методов со статическими ссылками. В сочетании с семантикой отложенного выполнения итераторов это позволяет повысить производительность. Дополнительные сведения о семантике отложенного выполнения итераторов см. в разделе [отложенное выполнение и отложенное вычисление в LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  В этих примерах показаны образцы кода, который может быть составлен компилятором. Действительная реализация может несколько отличаться от этих примеров, однако производительность останется такой же или приблизительно такой же.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Выполнение выражений XPath с помощью XmlDocument  
 В следующем примере объект <xref:System.Xml.XmlDocument> используется для получения таких же результатов, что и в предыдущих примерах.  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 Этот запрос возвращает такие же выходные данные, что и в примерах на основе LINQ to XML, за исключением того, что запрос LINQ to XML расставляет отступы в результирующем файле XML, а запрос <xref:System.Xml.XmlDocument> - нет.  
  
 Однако производительность подхода на основе <xref:System.Xml.XmlDocument> в целом ниже, чем при использовании LINQ to XML, поскольку метод <xref:System.Xml.XmlNode.SelectNodes%2A> должен при каждом вызове выполнять следующие внутренние операции:  
  
- Анализирует строку, содержащую выражение XPath, и разбивает ее на лексемы.  
  
- Проверяет лексемы, чтобы подтвердить правильность выражения XPath.  
  
- Транслирует выражение во внутреннее дерево выражений.  
  
- Проходит по узлам, выбирает соответствующие узлы на основании оценки выражения и добавляет их в набор результатов.  
  
 При этом выполняется значительно больший объем работы, чем при использовании аналогичного запроса LINQ to XML. Конкретный выигрыш по производительности зависит от типа запроса, однако в общем случае запросы LINQ to XML выполняют меньше работы и поэтому более эффективны, чем операции по оценке выражений XPath с помощью <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>См. также

- [Производительность (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
