---
title: Практическое руководство. Извлечение значений атрибута (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 7cdd3e1f3e4c15d99511e944fd9bc2faac17dc5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054463"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="14b6a-102">Практическое руководство. Извлечение значений атрибута (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14b6a-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="14b6a-103">В этом разделе показано получение значений атрибутов.</span><span class="sxs-lookup"><span data-stu-id="14b6a-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="14b6a-104">Существует два основных способа. Можно привести <xref:System.Xml.Linq.XAttribute> к требуемому типу, после этого оператор явного преобразования преобразует содержимое элемента или атрибута в указанный тип.</span><span class="sxs-lookup"><span data-stu-id="14b6a-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="14b6a-105">Иначе можно использовать свойство <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="14b6a-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="14b6a-106">Однако приведение, как правило, является лучшим подходом.</span><span class="sxs-lookup"><span data-stu-id="14b6a-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="14b6a-107">В частности, становится проще написание кода, обеспечивающего получение значения атрибута, который может существовать или не существовать, после приведения атрибута к типу, допускающему значение NULL.</span><span class="sxs-lookup"><span data-stu-id="14b6a-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="14b6a-108">Примеры применения этого способа см. в разделе [Практическое руководство. Извлечение значений элемента (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="14b6a-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b6a-109">Пример</span><span class="sxs-lookup"><span data-stu-id="14b6a-109">Example</span></span>  
 <span data-ttu-id="14b6a-110">В Visual Basic для получения значения атрибута можно использовать встроенное свойство атрибута.</span><span class="sxs-lookup"><span data-stu-id="14b6a-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="14b6a-111">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="14b6a-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="14b6a-112">Пример</span><span class="sxs-lookup"><span data-stu-id="14b6a-112">Example</span></span>  
 <span data-ttu-id="14b6a-113">В Visual Basic для установки значения атрибута можно использовать встроенное свойство атрибута.</span><span class="sxs-lookup"><span data-stu-id="14b6a-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="14b6a-114">Далее в случае использования встроенного свойства атрибута для установки значения несуществующего атрибута этот атрибут будет создан.</span><span class="sxs-lookup"><span data-stu-id="14b6a-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="14b6a-115">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="14b6a-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="14b6a-116">Пример</span><span class="sxs-lookup"><span data-stu-id="14b6a-116">Example</span></span>  
 <span data-ttu-id="14b6a-117">В следующем примере показано, как получить значение атрибута, если атрибут находится в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="14b6a-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="14b6a-118">Дополнительные сведения см. в разделе [работа с пространствами имен XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="14b6a-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="14b6a-119">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="14b6a-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="14b6a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="14b6a-120">See also</span></span>

- [<span data-ttu-id="14b6a-121">Оси LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14b6a-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
