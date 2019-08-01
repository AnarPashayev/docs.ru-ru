---
title: Работа с глобальными пространствами имен (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710383"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="399b7-102">Работа с глобальными пространствами имен (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="399b7-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="399b7-103">Одной из основных функций литералов XML в Visual Basic является возможность объявлять пространства имен XML с помощью `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="399b7-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="399b7-104">Используя эту возможность, можно объявить либо пространство имен XML, использующее префикс, либо пространство имен XML по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="399b7-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="399b7-105">Данная возможность полезна в двух ситуациях.</span><span class="sxs-lookup"><span data-stu-id="399b7-105">This capability is useful in two situations.</span></span> <span data-ttu-id="399b7-106">Во-первых, пространства имен, объявленные в XML-литералах, не переносятся во внедренные выражения.</span><span class="sxs-lookup"><span data-stu-id="399b7-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="399b7-107">Применение деклараций глобальных пространств имен способствует снижению объема работы, которую необходимо выполнить в целях использования внедренных выражений с пространствами имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="399b7-108">Во-вторых, необходимо объявить глобальные пространства имен в целях использования пространств имен с XML-свойствами.</span><span class="sxs-lookup"><span data-stu-id="399b7-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="399b7-109">Глобальные пространства имен можно объявлять на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="399b7-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="399b7-110">Глобальные пространства имен можно также объявить на уровне модуля, что приводит к переопределению глобальных пространств имен уровня проекта.</span><span class="sxs-lookup"><span data-stu-id="399b7-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="399b7-111">Наконец, можно переопределить глобальные пространства имен в XML-литерале.</span><span class="sxs-lookup"><span data-stu-id="399b7-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="399b7-112">При использовании XML-литералов или XML-свойств, находящихся в пространствах имен, объявленных глобально, можно видеть развернутое имя XML-литералов или свойств при наведении на них курсора в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="399b7-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="399b7-113">Развернутое имя отобразится в подсказке.</span><span class="sxs-lookup"><span data-stu-id="399b7-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="399b7-114">С помощью метода <xref:System.Xml.Linq.XNamespace> можно вызвать объект `GetXmlNamespace`, соответствующий глобальному пространству имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="399b7-115">Примеры глобальных пространств имен</span><span class="sxs-lookup"><span data-stu-id="399b7-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="399b7-116">В следующем примере объявляется глобальное пространство имен по умолчанию с помощью инструкции `Imports`, а затем используется XML-литерал для инициализации объекта <xref:System.Xml.Linq.XElement> в данном пространстве имен:</span><span class="sxs-lookup"><span data-stu-id="399b7-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="399b7-117">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="399b7-118">В следующем примере объявляется глобальное пространство имен с префиксом, а затем используется XML-литерал для инициализации элемента:</span><span class="sxs-lookup"><span data-stu-id="399b7-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="399b7-119">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="399b7-120">Глобальные пространства имен и внедренные выражения</span><span class="sxs-lookup"><span data-stu-id="399b7-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="399b7-121">Пространства имен, объявленные в XML-литералах, не переносятся во внедренные выражения.</span><span class="sxs-lookup"><span data-stu-id="399b7-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="399b7-122">В следующем примере объявляется пространство имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="399b7-122">The following example declares a default namespace.</span></span> <span data-ttu-id="399b7-123">Затем в нем используется внедренное выражение для элемента `Child`.</span><span class="sxs-lookup"><span data-stu-id="399b7-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="399b7-124">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="399b7-125">Очевидно, что результирующий XML включает декларацию пространства имен по умолчанию, так что элемент `Child` находится вне пространства имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="399b7-126">Можно повторно объявить пространство имен во внедренном выражении следующим образом:</span><span class="sxs-lookup"><span data-stu-id="399b7-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="399b7-127">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="399b7-128">Однако это более сложный и менее выгодный способ по сравнению с использованием глобального пространства имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="399b7-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="399b7-129">При наличии глобального пространства имен по умолчанию при использовании XML-литералов можно не декларировать пространства имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="399b7-130">Результирующий XML будет находиться в пространстве имен, объявленном глобально.</span><span class="sxs-lookup"><span data-stu-id="399b7-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="399b7-131">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="399b7-132">Использование пространств имен с XML-свойствами</span><span class="sxs-lookup"><span data-stu-id="399b7-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="399b7-133">При работе с XML-деревом, находящимся в пространстве имен, и использовании XML-свойств необходимо использовать глобальное пространство имен, чтобы XML-свойства также находились в правильно заданном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="399b7-134">В следующем примере объявляется XML-дерево в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="399b7-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="399b7-135">Затем в нем происходит вывод на печать числа элементов `Child`.</span><span class="sxs-lookup"><span data-stu-id="399b7-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="399b7-136">Данный пример указывает на отсутствие элементов `Child`.</span><span class="sxs-lookup"><span data-stu-id="399b7-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="399b7-137">Выводятся следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="399b7-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="399b7-138">Однако после объявления глобального пространства имен по умолчанию в нем будут находиться и XML-литерал и XML-свойство.</span><span class="sxs-lookup"><span data-stu-id="399b7-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="399b7-139">Данный пример указывает на отсутствие одного элемента `Child`.</span><span class="sxs-lookup"><span data-stu-id="399b7-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="399b7-140">Выводятся следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="399b7-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="399b7-141">После объявления глобального пространства имен с префиксом можно использовать префикс как для XML-литералов, так и для XML-свойств.</span><span class="sxs-lookup"><span data-stu-id="399b7-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="399b7-142">XNamespace и глобальные пространства имен</span><span class="sxs-lookup"><span data-stu-id="399b7-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="399b7-143">Объект <xref:System.Xml.Linq.XNamespace> можно получить с помощью метода `GetXmlNamespace`:</span><span class="sxs-lookup"><span data-stu-id="399b7-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="399b7-144">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="399b7-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="399b7-145">См. также</span><span class="sxs-lookup"><span data-stu-id="399b7-145">See also</span></span>

- [<span data-ttu-id="399b7-146">Общие сведения о пространствах имен (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="399b7-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
