---
title: Параметры XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282536"
---
# <a name="xslt-parameters"></a><span data-ttu-id="733c5-102">Параметры XSLT</span><span class="sxs-lookup"><span data-stu-id="733c5-102">XSLT Parameters</span></span>
<span data-ttu-id="733c5-103">Параметры XSLT добавляются в <xref:System.Xml.Xsl.XsltArgumentList> с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="733c5-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="733c5-104">В это время с объектом параметра связываются полное имя и URI-код пространства имен.</span><span class="sxs-lookup"><span data-stu-id="733c5-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="733c5-105">Использование параметра XSLT</span><span class="sxs-lookup"><span data-stu-id="733c5-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="733c5-106">Создайте объект <xref:System.Xml.Xsl.XsltArgumentList> и добавьте параметр с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="733c5-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="733c5-107">Вызовите параметр из таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="733c5-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="733c5-108">Передайте объект <xref:System.Xml.Xsl.XsltArgumentList> методу <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="733c5-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="733c5-109">Типы параметров</span><span class="sxs-lookup"><span data-stu-id="733c5-109">Parameter Types</span></span>  
 <span data-ttu-id="733c5-110">Объект параметра должен соответствовать типу W3C.</span><span class="sxs-lookup"><span data-stu-id="733c5-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="733c5-111">В следующей таблице показано соответствие типов W3C и классов (типов) Microsoft .NET. Также показано, является ли тип W3C типом XPath или типом XSLT.</span><span class="sxs-lookup"><span data-stu-id="733c5-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="733c5-112">Тип W3C</span><span class="sxs-lookup"><span data-stu-id="733c5-112">W3C type</span></span>|<span data-ttu-id="733c5-113">Эквивалентный класс (тип) .NET</span><span class="sxs-lookup"><span data-stu-id="733c5-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="733c5-114">Тип XPath или XSLT</span><span class="sxs-lookup"><span data-stu-id="733c5-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="733c5-115">XPath</span><span class="sxs-lookup"><span data-stu-id="733c5-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="733c5-116">XPath</span><span class="sxs-lookup"><span data-stu-id="733c5-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="733c5-117">XPath</span><span class="sxs-lookup"><span data-stu-id="733c5-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="733c5-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="733c5-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="733c5-119">XPath</span><span class="sxs-lookup"><span data-stu-id="733c5-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="733c5-120">**XPathNavigator[]**</span><span class="sxs-lookup"><span data-stu-id="733c5-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="733c5-121">XPath</span><span class="sxs-lookup"><span data-stu-id="733c5-121">XPath</span></span>|  
  
 <span data-ttu-id="733c5-122">\*Это эквивалентно набору узлов, содержащему единственный узел.</span><span class="sxs-lookup"><span data-stu-id="733c5-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="733c5-123">Если объект параметра не принадлежит ни к одному из приведенных выше классов, он преобразуется по следующим правилам.</span><span class="sxs-lookup"><span data-stu-id="733c5-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="733c5-124">Числовые типы среды CLR преобразуются в <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="733c5-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="733c5-125">Тип <xref:System.DateTime> преобразуется в тип <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="733c5-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="733c5-126">Типы <xref:System.Xml.XPath.IXPathNavigable> преобразуются в типы <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="733c5-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="733c5-127">**XPathNavigator[]** преобразуется в <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="733c5-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="733c5-128">Все другие типы вызывают ошибку.</span><span class="sxs-lookup"><span data-stu-id="733c5-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="733c5-129">Пример</span><span class="sxs-lookup"><span data-stu-id="733c5-129">Example</span></span>  
 <span data-ttu-id="733c5-130">В следующем примере используется метод <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> для создания параметра, хранящего вычисленную дату скидки.</span><span class="sxs-lookup"><span data-stu-id="733c5-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="733c5-131">Дата скидки вычисляется как 20 дней после даты заказа.</span><span class="sxs-lookup"><span data-stu-id="733c5-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="733c5-132">Входные данные</span><span class="sxs-lookup"><span data-stu-id="733c5-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="733c5-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="733c5-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="733c5-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="733c5-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="733c5-135">Вывод</span><span class="sxs-lookup"><span data-stu-id="733c5-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="733c5-136">См. также</span><span class="sxs-lookup"><span data-stu-id="733c5-136">See also</span></span>

- [<span data-ttu-id="733c5-137">Преобразования XSLT</span><span class="sxs-lookup"><span data-stu-id="733c5-137">XSLT Transformations</span></span>](xslt-transformations.md)
