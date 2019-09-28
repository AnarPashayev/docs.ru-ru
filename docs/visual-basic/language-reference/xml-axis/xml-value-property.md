---
title: Свойство значения XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592007"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="95997-102">Свойство значения XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95997-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="95997-103">Предоставляет доступ к значению первого элемента коллекции объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95997-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="95997-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95997-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="95997-105">Части</span><span class="sxs-lookup"><span data-stu-id="95997-105">Parts</span></span>

|<span data-ttu-id="95997-106">Термин</span><span class="sxs-lookup"><span data-stu-id="95997-106">Term</span></span>|<span data-ttu-id="95997-107">Определение</span><span class="sxs-lookup"><span data-stu-id="95997-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="95997-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="95997-108">Required.</span></span> <span data-ttu-id="95997-109">Коллекция объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95997-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="95997-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="95997-110">Return Value</span></span>

 <span data-ttu-id="95997-111">Объект `String`, содержащий значение первого элемента коллекции, или `Nothing`, если коллекция пуста.</span><span class="sxs-lookup"><span data-stu-id="95997-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="95997-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="95997-112">Remarks</span></span>

 <span data-ttu-id="95997-113">Свойство <xref:System.Xml.Linq.XElement.Value%2A> упрощает доступ к значению первого элемента в коллекции объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95997-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="95997-114">Это свойство сначала проверяет, содержит ли коллекция хотя бы один объект.</span><span class="sxs-lookup"><span data-stu-id="95997-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="95997-115">Если коллекция пуста, это свойство возвращает значение `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="95997-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="95997-116">В противном случае это свойство возвращает значение свойства <xref:System.Xml.Linq.XElement.Value%2A> первого элемента в коллекции.</span><span class="sxs-lookup"><span data-stu-id="95997-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="95997-117">При доступе к значению атрибута XML с помощью идентификатора "\@" значение атрибута возвращается как `String`, и вам не нужно явно указывать свойство <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="95997-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="95997-118">Для доступа к другим элементам в коллекции можно использовать свойство индексатора расширения XML.</span><span class="sxs-lookup"><span data-stu-id="95997-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="95997-119">Дополнительные сведения см. в разделе [свойство индексатора расширения](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="95997-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="95997-120">Наследование</span><span class="sxs-lookup"><span data-stu-id="95997-120">Inheritance</span></span>

 <span data-ttu-id="95997-121">Большинству пользователей не придется реализовывать <xref:System.Collections.Generic.IEnumerable%601>, поэтому этот раздел можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="95997-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="95997-122">Свойство <xref:System.Xml.Linq.XElement.Value%2A> является свойством расширения для типов, реализующих `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="95997-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="95997-123">Привязка этого свойства расширения похожа на привязку методов расширения: Если тип реализует один из интерфейсов и определяет свойство с именем "value", это свойство имеет приоритет над свойством расширения.</span><span class="sxs-lookup"><span data-stu-id="95997-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="95997-124">Иными словами, это свойство <xref:System.Xml.Linq.XElement.Value%2A> может быть переопределено путем определения нового свойства в классе, реализующем `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="95997-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="95997-125">Пример</span><span class="sxs-lookup"><span data-stu-id="95997-125">Example</span></span>

 <span data-ttu-id="95997-126">В следующем примере показано, как использовать свойство <xref:System.Xml.Linq.XElement.Value%2A> для доступа к первому узлу в коллекции объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95997-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="95997-127">В примере свойство дочерней оси используется для получения коллекции всех дочерних узлов с именем `phone`, которые находятся в объекте `contact`.</span><span class="sxs-lookup"><span data-stu-id="95997-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="95997-128">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="95997-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="95997-129">Пример</span><span class="sxs-lookup"><span data-stu-id="95997-129">Example</span></span>

 <span data-ttu-id="95997-130">В следующем примере показано, как получить значение атрибута XML из коллекции объектов <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="95997-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="95997-131">В примере свойство оси атрибута используется для вывода значения атрибута `type` для всех элементов `phone`.</span><span class="sxs-lookup"><span data-stu-id="95997-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="95997-132">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="95997-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="95997-133">См. также</span><span class="sxs-lookup"><span data-stu-id="95997-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="95997-134">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="95997-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="95997-135">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="95997-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="95997-136">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95997-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="95997-137">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="95997-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="95997-138">Свойство индексатора расширения</span><span class="sxs-lookup"><span data-stu-id="95997-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="95997-139">Свойство дочерней оси XML</span><span class="sxs-lookup"><span data-stu-id="95997-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="95997-140">Свойство оси атрибута XML</span><span class="sxs-lookup"><span data-stu-id="95997-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
