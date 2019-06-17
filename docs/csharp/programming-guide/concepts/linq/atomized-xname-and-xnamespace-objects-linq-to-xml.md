---
title: Атомарные объекты XName и XNamespace (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 0d21397e6885b892f6ac1904e38bd85a78ae07ab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487596"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Атомарные объекты XName и XNamespace (LINQ to XML) (C#)
Объекты <xref:System.Xml.Linq.XName> и <xref:System.Xml.Linq.XNamespace> являются *атомарными*; иными словами, если они имеют идентичное полное имя, они ссылаются на один и тот же объект. Это способствует повышению производительности при использовании запросов. При сравнении двух атомарных имен для проверки их равенства соответствующий промежуточный язык должен определить, ссылаются ли они на один и тот же объект. Эта операция используется в промежуточном коде вместо более длительной операции сравнения строк.  
  
## <a name="atomization-semantics"></a>Семантика атомизации  
 Атомизация означает, что два объекта <xref:System.Xml.Linq.XName> имеющие идентичное локальное имя и находящиеся в одном пространстве имен, совместно используют один и тот же экземпляр. Аналогично, если два объекта <xref:System.Xml.Linq.XNamespace> имеют идентичный идентификатор URI пространства имен, то они совместно используют один и тот же экземпляр.  
  
 Чтобы разрешить создание атомарных объектов класса, необходимо, чтобы конструктор класса был закрытым, а не открытым. Это требование основано на том, что если бы конструктор был открытым, можно было бы создавать неатомарные объекты. Классы <xref:System.Xml.Linq.XName> и <xref:System.Xml.Linq.XNamespace> реализуют неявный оператор преобразования строки в объект <xref:System.Xml.Linq.XName> или <xref:System.Xml.Linq.XNamespace>. Экземпляры этих объектов могут быть получены только таким способом. Создание экземпляров с помощью конструктора невозможно, так как конструктор недоступен.  
  
 Классы <xref:System.Xml.Linq.XName> и<xref:System.Xml.Linq.XNamespace> также реализуют операторы для проверки равенства и неравенства, определяющие, ссылаются ли два сравниваемых объекта на один и тот же экземпляр.  
  
## <a name="example"></a>Пример  
 Следующий код создает объекты <xref:System.Xml.Linq.XElement> и демонстрирует, что идентичные имена совместно используют один и тот же экземпляр.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 В этом примере выводятся следующие данные:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Как отмечалось выше, преимущество атомарных объектов заключается в том, что при использовании одного из методов оси, принимающих в качестве параметра <xref:System.Xml.Linq.XName>, этому методу оси для выбора необходимых элементов достаточно определить, что два имени совместно используют один и тот же экземпляр.  
  
 В следующем примере объект <xref:System.Xml.Linq.XName> передается при вызове метода <xref:System.Xml.Linq.XContainer.Descendants%2A>, производительность которого выше за счет использования атомизации.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
