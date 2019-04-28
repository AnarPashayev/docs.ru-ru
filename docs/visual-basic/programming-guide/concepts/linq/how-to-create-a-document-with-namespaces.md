---
title: Практическое руководство. создать документ с пространствами имен (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: b65d22451d900f7b20226f25b61bb235241dd84f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855521"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="efa1c-102">Практическое руководство. создать документ с пространствами имен (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efa1c-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="efa1c-103">В этом разделе описано, как создать документ с пространствами имен в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efa1c-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="efa1c-104">При использовании литералов XML в Visual Basic пользователи могут задавать одно глобальное пространство имен XML.</span><span class="sxs-lookup"><span data-stu-id="efa1c-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="efa1c-105">Это пространство имен является пространством имен по умолчанию как для литералов, так и для свойств XML.</span><span class="sxs-lookup"><span data-stu-id="efa1c-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="efa1c-106">Пространство имен XML по умолчанию можно задать как на уровне проекта, так и на уровне файла.</span><span class="sxs-lookup"><span data-stu-id="efa1c-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="efa1c-107">Если оно задается на уровне файла, то оно переопределяет пространство имен по умолчанию, заданное на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="efa1c-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="efa1c-108">Можно также задавать другие пространства имен и указывать префиксы для них.</span><span class="sxs-lookup"><span data-stu-id="efa1c-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="efa1c-109">Как пространства имен по умолчанию, так и пространства имен с префиксами можно задавать при помощи ключа `Imports`.</span><span class="sxs-lookup"><span data-stu-id="efa1c-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="efa1c-110">Дополнительные сведения см. в разделе [Знакомство с литералами XML в Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="efa1c-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="efa1c-111">Обратите внимание, что пространство имен XML по умолчанию применимо только к элементам, а не к атрибутам.</span><span class="sxs-lookup"><span data-stu-id="efa1c-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="efa1c-112">Атрибуты по умолчанию никогда не находятся в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="efa1c-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="efa1c-113">Однако можно использовать префикс пространства имен, чтобы ввести атрибут в пространство имен.</span><span class="sxs-lookup"><span data-stu-id="efa1c-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efa1c-114">Пример</span><span class="sxs-lookup"><span data-stu-id="efa1c-114">Example</span></span>  
 <span data-ttu-id="efa1c-115">В этом примере создается документ, который содержит пространство имен.</span><span class="sxs-lookup"><span data-stu-id="efa1c-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="efa1c-116">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="efa1c-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="efa1c-117">Пример</span><span class="sxs-lookup"><span data-stu-id="efa1c-117">Example</span></span>  
 <span data-ttu-id="efa1c-118">В этом примере создается документ, который содержит два пространства имен, каждое из которых является пространством имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="efa1c-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="efa1c-119">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="efa1c-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="efa1c-120">Пример</span><span class="sxs-lookup"><span data-stu-id="efa1c-120">Example</span></span>  
 <span data-ttu-id="efa1c-121">В этом примере создается документ, который содержит несколько пространств имен с префиксами.</span><span class="sxs-lookup"><span data-stu-id="efa1c-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="efa1c-122">При сериализации XML-дерева [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] создает декларации пространства имен таким образом, чтобы каждый элемент находился в верном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="efa1c-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="efa1c-123">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="efa1c-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efa1c-124">См. также</span><span class="sxs-lookup"><span data-stu-id="efa1c-124">See also</span></span>

- [<span data-ttu-id="efa1c-125">Работа с пространствами имен XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efa1c-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
