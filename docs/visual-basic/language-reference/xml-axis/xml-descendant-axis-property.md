---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400257"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="03a86-102">Свойство дочерней оси XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03a86-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="03a86-103">Предоставляет доступ к потомкам следующих объектов: <xref:System.Xml.Linq.XElement> объекту, <xref:System.Xml.Linq.XDocument> объекту, коллекции <xref:System.Xml.Linq.XElement> объектов или коллекции <xref:System.Xml.Linq.XDocument> объектов.</span><span class="sxs-lookup"><span data-stu-id="03a86-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="03a86-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03a86-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="03a86-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="03a86-105">Parts</span></span>

<span data-ttu-id="03a86-106">`object` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="03a86-106">`object` Required.</span></span> <span data-ttu-id="03a86-107">Объект <xref:System.Xml.Linq.XElement>, объект <xref:System.Xml.Linq.XDocument>, коллекция объектов <xref:System.Xml.Linq.XElement> или коллекция объектов <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="03a86-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="03a86-108">`...<` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="03a86-108">`...<` Required.</span></span> <span data-ttu-id="03a86-109">Обозначает начало свойства дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="03a86-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="03a86-110">`descendant` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="03a86-110">`descendant` Required.</span></span> <span data-ttu-id="03a86-111">Имя узлов-потомков для доступа к форме [ `prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="03a86-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="03a86-112">Часть</span><span class="sxs-lookup"><span data-stu-id="03a86-112">Part</span></span>|<span data-ttu-id="03a86-113">Описание</span><span class="sxs-lookup"><span data-stu-id="03a86-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="03a86-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="03a86-114">Optional.</span></span> <span data-ttu-id="03a86-115">Префикс пространства имен XML для узла-потомка.</span><span class="sxs-lookup"><span data-stu-id="03a86-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="03a86-116">Должно быть глобальным пространством имен XML, которое определяется с помощью `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="03a86-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="03a86-117">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="03a86-117">Required.</span></span> <span data-ttu-id="03a86-118">Локальное имя дочернего узла.</span><span class="sxs-lookup"><span data-stu-id="03a86-118">Local name of the descendant node.</span></span> <span data-ttu-id="03a86-119">См. [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="03a86-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="03a86-120">`>` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="03a86-120">`>` Required.</span></span> <span data-ttu-id="03a86-121">Обозначает конец свойства дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="03a86-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="03a86-122">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="03a86-122">Return Value</span></span>

<span data-ttu-id="03a86-123">Коллекция объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="03a86-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="03a86-124">Комментарии</span><span class="sxs-lookup"><span data-stu-id="03a86-124">Remarks</span></span>

<span data-ttu-id="03a86-125">Свойство дочерней оси XML можно использовать для доступа к узлам-потомкам по имени из <xref:System.Xml.Linq.XElement> объекта или или <xref:System.Xml.Linq.XDocument> из коллекции <xref:System.Xml.Linq.XElement> объектов или <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="03a86-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="03a86-126">Используйте свойство XML `Value` для доступа к значению первого узла-потомка в возвращаемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="03a86-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="03a86-127">Дополнительные сведения см. в разделе [свойство значения XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="03a86-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="03a86-128">Компилятор Visual Basic преобразует свойства оси потомков в вызовы <xref:System.Xml.Linq.XContainer.Descendants%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="03a86-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="03a86-129">Пространства имен XML</span><span class="sxs-lookup"><span data-stu-id="03a86-129">XML Namespaces</span></span>

<span data-ttu-id="03a86-130">Имя в свойстве дочерней оси может использовать только пространства имен XML, объявленные глобально с помощью `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="03a86-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="03a86-131">Нельзя использовать пространства имен XML, объявленные локально в литералах XML-элементов.</span><span class="sxs-lookup"><span data-stu-id="03a86-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="03a86-132">Дополнительные сведения см. в разделе [оператор Imports (пространство имен XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="03a86-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="03a86-133">Пример</span><span class="sxs-lookup"><span data-stu-id="03a86-133">Example</span></span>

<span data-ttu-id="03a86-134">В следующем примере показано, как получить доступ к значению первого узла-потомка с именем `name` и значения всех узлов-потомков, названных `phone` из `contacts` объекта.</span><span class="sxs-lookup"><span data-stu-id="03a86-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="03a86-135">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="03a86-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="03a86-136">Пример</span><span class="sxs-lookup"><span data-stu-id="03a86-136">Example</span></span>

<span data-ttu-id="03a86-137">В следующем примере `ns` объявляется как префикс пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="03a86-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="03a86-138">Затем он использует префикс пространства имен, чтобы создать XML-литерал и получить доступ к значению первого дочернего узла с полным именем `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="03a86-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="03a86-139">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="03a86-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="03a86-140">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="03a86-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="03a86-141">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="03a86-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="03a86-142">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="03a86-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="03a86-143">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03a86-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="03a86-144">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="03a86-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
