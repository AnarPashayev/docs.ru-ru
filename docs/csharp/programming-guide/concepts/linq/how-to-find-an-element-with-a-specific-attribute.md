---
title: Практическое руководство. Поиск элементов с определенным атрибутом (C#)
description: Сведения о поиске элемента, имеющего атрибут с определенным значением. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 44875ca2104e7a8f83e83da983af49ef85c89f0a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303287"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a>Практическое руководство. Поиск элементов с определенным атрибутом (C#)
В этом разделе показан поиск элемента, имеющего атрибут с определенным значением.  
  
## <a name="example"></a>Пример  
 В примере показано, как выполнить поиск элемента `Address`, имеющего атрибут `Type` со значением «Billing».  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Типичный заказ на покупку (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 Этот код выводит следующие результаты:  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует тот же запрос XML, что и в пространстве имен. Дополнительные сведения см. в статье [Обзор пространств имен DFS (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Типичный заказ на покупку в пространстве имен](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 Этот код выводит следующие результаты:  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Общие сведения о стандартных операторах запроса (C#)](./standard-query-operators-overview.md)
- [Операции проекции (C#)](./projection-operations.md)
