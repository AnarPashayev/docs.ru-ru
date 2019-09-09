---
title: Практическое руководство. Поиск потомков с определенным именем элемента (C#)
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 8c859c555109a6f68a6b4290c536b10114620f3d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253695"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="faf3d-102">Практическое руководство. Поиск потомков с определенным именем элемента (C#)</span><span class="sxs-lookup"><span data-stu-id="faf3d-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="faf3d-103">Иногда возникает необходимость найти всех потомков с определенным именем.</span><span class="sxs-lookup"><span data-stu-id="faf3d-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="faf3d-104">В таких случаях можно написать код для просмотра всех потомков, но проще использовать ось <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="faf3d-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf3d-105">Пример</span><span class="sxs-lookup"><span data-stu-id="faf3d-105">Example</span></span>  
 <span data-ttu-id="faf3d-106">В следующем примере показано, как находить потомков на основе имени элемента.</span><span class="sxs-lookup"><span data-stu-id="faf3d-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="faf3d-107">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="faf3d-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="faf3d-108">Пример</span><span class="sxs-lookup"><span data-stu-id="faf3d-108">Example</span></span>  
 <span data-ttu-id="faf3d-109">Следующий пример демонстрирует тот же запрос XML, что и в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="faf3d-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="faf3d-110">Дополнительные сведения см. в статье [Обзор пространств имен DFS (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="faf3d-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="faf3d-111">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="faf3d-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="faf3d-112">См. также</span><span class="sxs-lookup"><span data-stu-id="faf3d-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
