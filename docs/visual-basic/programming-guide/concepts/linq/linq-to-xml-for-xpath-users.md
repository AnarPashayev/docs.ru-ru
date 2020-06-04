---
title: LINQ to XML для пользователей XPath
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 7942d33831644875f390e9128965fe1c36433808
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368794"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML для пользователей XPath (Visual Basic)

В данном ряде разделов показаны несколько выражений XPath и их эквиваленты [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Во всех примерах используются функции XPath, поддерживаемые технологией [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], доступ к которым предоставляется с помощью методов расширения в <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. В этих примерах происходит выполнение и выражения XPath, и выражения [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Затем в каждом примере сравниваются результаты обоих запросов для проверки того, что выражение XPath является функционально эквивалентным запросу [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Так как оба типа запросов возвращают узлы из одного XML-дерева, сравнение результатов запросов выполняется с помощью ссылочного идентификатора.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Сравнительные характеристики XPath и LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Содержит общие сведения о подобиях и различиях между XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Как найти дочерний элемент (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-child-element-xpath-linq-to-xml.md)|Сравнивает ось дочернего элемента XPath с [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> методом.<br /><br /> Связанным выражением XPath является `"DeliveryNotes"`.|  
|[Как найти список дочерних элементов (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Сравнивает ось дочерних элементов XPath с [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> осью.<br /><br /> Связанное выражение XPath:`"./*"`|  
|[Руководство. поиск корневого элемента (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-root-element-xpath-linq-to-xml.md)|Сравнивает способы получения корневого элемента при помощи XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"/PurchaseOrders"`|  
|[Руководство. Поиск элементов-потомков (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendant-elements-xpath-linq-to-xml.md)|Сравнивает способы получения элементов-потомков с определенным именем при помощи XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"//Name"`|  
|[Как выполнить фильтрацию по атрибуту (XPath-LINQ to XML) (Visual Basic)](how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Сравнивает способы получения элементов-потомков с указанным именем и атрибутом с заданным значением с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"./Address[@Type='Shipping']"`|  
|[Пошаговое руководство. Поиск связанных элементов (XPath-LINQ to XML) (Visual Basic)](how-to-find-related-elements-xpath-linq-to-xml.md)|Сравнивает способы получения элемента по атрибуту, на который ссылается значение другого элемента, с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Пошаговое руководство. Поиск элементов в пространстве имен (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-in-a-namespace.md)|Сравнивает использование <xref:System.Xml.XmlNamespaceManager> класса XPath со [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> свойством <xref:System.Xml.Linq.XName> класса для работы с пространствами имен XML.<br /><br /> Связанное выражение XPath:`"./aw:*"`|  
|[Руководство. Поиск предшествующих одноуровневых элементов (XPath-LINQ to XML) (Visual Basic)](how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Сравнивает ось `preceding-sibling` XPath с дочерней по отношению к [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] осью <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>.<br /><br /> Связанное выражение XPath:`"preceding-sibling::*"`|  
|[Руководство. Поиск потомков дочернего элемента (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Сравнивает способы получения элементов-потомков дочернего элемента с определенным именем при помощи XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"./Paragraph//Text/text()"`|  
|[Как найти объединение двух путей расположения (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-union-of-two-location-paths-xpath.md)|Сравнивает использование оператора объединения <code>&#124;</code> в XPath со стандартным оператором запросов <xref:System.Linq.Enumerable.Concat%2A> в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:<code>"//Category&#124;//Price"</code>|  
|[Руководство. Поиск узлов того же уровня (XPath-LINQ to XML) (Visual Basic)](how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Сравнивает способы нахождения с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] всех одноуровневых объектов узла с указанным именем.<br /><br /> Связанное выражение XPath:`"../Book"`|  
|[Как найти атрибут родителя (XPath-LINQ to XML) (Visual Basic)](how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Сравнивает способы перехода к родительскому элементу и поиска связанного атрибута с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"../@id"`|  
|[Как найти атрибуты одноуровневых элементов с указанным именем (XPath-LINQ to XML) (Visual Basic)](how-to-find-attributes-of-siblings-with-a-specific-name.md)|Сравнивает способы поиска определенных атрибутов одноуровневых объектов контекстного узла при помощи XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"../Book/@id"`|  
|[Пошаговое руководство. Поиск элементов с указанным атрибутом (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-with-a-specific-attribute.md)|Сравнивает способы получения всех элементов, содержащих определенный атрибут, с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"./*[@Select]"`|  
|[Пошаговое руководство. Поиск дочерних элементов по положению (XPath-LINQ to XML) (Visual Basic)](how-to-find-child-elements-based-on-position.md)|Сравнивает способы поиска элемента на основе его относительного расположения с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"Test[position() >= 2 and position() <= 4]"`|  
|[Как найти ближайший предшествующий элемент того же уровня (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Сравнивает способы нахождения ближайшего предшествующего одноуровневого элемента узла с помощью XPath и [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Связанное выражение XPath:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Выполнение запросов к деревьям XML (Visual Basic)](querying-xml-trees.md)
- [Обработка XML-данных с использованием модели данных XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
