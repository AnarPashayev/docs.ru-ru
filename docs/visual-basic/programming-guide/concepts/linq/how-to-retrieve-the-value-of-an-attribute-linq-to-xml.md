---
title: Как получить значение атрибута (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6f9a5936c962111eb75a05f5e3704f7132618143
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320467"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="39656-102">Как получить значение атрибута (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39656-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="39656-103">В этом разделе показано получение значений атрибутов.</span><span class="sxs-lookup"><span data-stu-id="39656-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="39656-104">Существует два основных способа. Можно привести <xref:System.Xml.Linq.XAttribute> к требуемому типу, после этого оператор явного преобразования преобразует содержимое элемента или атрибута в указанный тип.</span><span class="sxs-lookup"><span data-stu-id="39656-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="39656-105">Иначе можно использовать свойство <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="39656-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="39656-106">Однако приведение, как правило, является лучшим подходом.</span><span class="sxs-lookup"><span data-stu-id="39656-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="39656-107">В частности, становится проще написание кода, обеспечивающего получение значения атрибута, который может существовать или не существовать, после приведения атрибута к типу, допускающему значение NULL.</span><span class="sxs-lookup"><span data-stu-id="39656-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="39656-108">Примеры использования этого метода см. [в разделе как получить значение элемента (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="39656-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39656-109">Пример</span><span class="sxs-lookup"><span data-stu-id="39656-109">Example</span></span>  
 <span data-ttu-id="39656-110">В Visual Basic для получения значения атрибута можно использовать встроенное свойство атрибута.</span><span class="sxs-lookup"><span data-stu-id="39656-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="39656-111">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="39656-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="39656-112">Пример</span><span class="sxs-lookup"><span data-stu-id="39656-112">Example</span></span>  
 <span data-ttu-id="39656-113">В Visual Basic для установки значения атрибута можно использовать встроенное свойство атрибута.</span><span class="sxs-lookup"><span data-stu-id="39656-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="39656-114">Далее в случае использования встроенного свойства атрибута для установки значения несуществующего атрибута этот атрибут будет создан.</span><span class="sxs-lookup"><span data-stu-id="39656-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="39656-115">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="39656-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="39656-116">Пример</span><span class="sxs-lookup"><span data-stu-id="39656-116">Example</span></span>  
 <span data-ttu-id="39656-117">В следующем примере показано, как получить значение атрибута, если атрибут находится в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="39656-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="39656-118">Дополнительные сведения см. в разделе [Общие сведения о пространствах имен (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="39656-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="39656-119">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="39656-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="39656-120">См. также</span><span class="sxs-lookup"><span data-stu-id="39656-120">See also</span></span>

- [<span data-ttu-id="39656-121">Оси LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39656-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
