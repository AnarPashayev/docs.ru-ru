---
title: Практическое руководство. Проецирование нового типа (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: bec4e7c7d87dffb90b49b76aa00a5de093d68436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593046"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Практическое руководство. Проецирование нового типа (LINQ to XML) (C#)

В других примерах данного раздела показаны запросы, возвращающие результаты в виде значений <xref:System.Collections.Generic.IEnumerable%601> типа <xref:System.Xml.Linq.XElement>, значений <xref:System.Collections.Generic.IEnumerable%601> типа `string` и значений <xref:System.Collections.Generic.IEnumerable%601> типа `int`. Это наиболее распространенные типы результатов, но подходят не для всех сценариев. Во многих случаях требуется, чтобы запросы возвращали <xref:System.Collections.Generic.IEnumerable%601> какого-то другого типа.

## <a name="example"></a>Пример

В данном примере показано, как создавать экземпляры объектов в предложении `select`. Сначала в коде определяется новый класс с помощью конструктора, а затем модифицируется инструкция `select`, чтобы это выражение представляло новый экземпляр нового класса.

В этом примере используется следующий XML-документ: [Пример XML-файла. Типичный заказ на покупку (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

```csharp
class NameQty 
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q; 
    }
};

class Program {
    public static void Main() 
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

В данном примере используется метод <xref:System.Xml.Linq.XContainer.Element%2A>, представленный в разделе [Практическое руководство. Извлечение одного дочернего элемента (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). В нем также используется приведение для получения значений элементов, возвращаемых методом <xref:System.Xml.Linq.XContainer.Element%2A>.  

В этом примере выводятся следующие данные:

```console
Lawnmower:1
Baby Monitor:2
```
