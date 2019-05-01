---
title: Сериализация XML и SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028243"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="177a1-102">Сериализация XML и SOAP</span><span class="sxs-lookup"><span data-stu-id="177a1-102">XML and SOAP Serialization</span></span>

<span data-ttu-id="177a1-103">При сериализации XML открытые поля и свойства объекта или параметры и возвращаемые значения методов преобразуются (сериализуются) в поток XML в соответствии со специальным документом, составленном на языке XSD (язык определения схемы XML).</span><span class="sxs-lookup"><span data-stu-id="177a1-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="177a1-104">XML-сериализация приводит к образованию строго типизированных классов с открытыми свойствами и полями, которые преобразуются в серийный формат (в данном случае - XML) для хранения и передачи.</span><span class="sxs-lookup"><span data-stu-id="177a1-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="177a1-105">Поскольку стандарт XML является открытым, поток XML может обработать любое необходимое приложение независимо от платформы.</span><span class="sxs-lookup"><span data-stu-id="177a1-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="177a1-106">Например, XML-веб-службы, созданные с помощью ASP.NET, используют класс <xref:System.Xml.Serialization.XmlSerializer>, чтобы создавать потоки XML, которые передают данные между приложениями веб-службы XML через Интернет или интрасети.</span><span class="sxs-lookup"><span data-stu-id="177a1-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="177a1-107">И наоборот, при десериализации используется такой поток и воссоздается объект.</span><span class="sxs-lookup"><span data-stu-id="177a1-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="177a1-108">XML-сериализация может также использоваться для сериализации объектов в потоки XML, которые соответствуют спецификации SOAP.</span><span class="sxs-lookup"><span data-stu-id="177a1-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="177a1-109">SOAP - это протокол, основанный на XML и созданный специально для передачи вызовов процедур с использованием XML.</span><span class="sxs-lookup"><span data-stu-id="177a1-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="177a1-110">Чтобы сериализовать и десериализовать объекты, используйте класс <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="177a1-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="177a1-111">Чтобы создать классы для их последующей сериализации, используйте инструмент определения схемы XML.</span><span class="sxs-lookup"><span data-stu-id="177a1-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="177a1-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="177a1-112">In This Section</span></span>

[<span data-ttu-id="177a1-113">Введение в сериализацию XML</span><span class="sxs-lookup"><span data-stu-id="177a1-113">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
<span data-ttu-id="177a1-114">Содержит общее определение сериализации, в особенности, XML-сериализации.</span><span class="sxs-lookup"><span data-stu-id="177a1-114">Provides a general definition of serialization, particularly XML serialization.</span></span>

[<span data-ttu-id="177a1-115">Практическое руководство. Сериализация объекта</span><span class="sxs-lookup"><span data-stu-id="177a1-115">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
<span data-ttu-id="177a1-116">Содержит пошаговые инструкции по сериализации объекта.</span><span class="sxs-lookup"><span data-stu-id="177a1-116">Provides step-by-step instructions for serializing an object.</span></span>

[<span data-ttu-id="177a1-117">Практическое руководство. Десериализация объекта</span><span class="sxs-lookup"><span data-stu-id="177a1-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  
<span data-ttu-id="177a1-118">Содержит пошаговые инструкции по десериализации объекта.</span><span class="sxs-lookup"><span data-stu-id="177a1-118">Provides step-by-step instructions for deserializing an object.</span></span>

[<span data-ttu-id="177a1-119">Примеры сериализации XML</span><span class="sxs-lookup"><span data-stu-id="177a1-119">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
<span data-ttu-id="177a1-120">Содержит примеры, демонстрирующие основные возможности XML-сериализации .</span><span class="sxs-lookup"><span data-stu-id="177a1-120">Provides examples that demonstrate the basics of XML serialization.</span></span>

[<span data-ttu-id="177a1-121">Инструмент определения схемы XML и сериализация XML</span><span class="sxs-lookup"><span data-stu-id="177a1-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)  
<span data-ttu-id="177a1-122">Содержит описание правил использования инструмента определения схемы XML для создания классов, которые соответствуют определенной схеме языка определения схемы XML (XSD), или создания схемы XML из файла DLL.</span><span class="sxs-lookup"><span data-stu-id="177a1-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>

[<span data-ttu-id="177a1-123">Управление сериализацией XML с использованием атрибутов</span><span class="sxs-lookup"><span data-stu-id="177a1-123">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)  
<span data-ttu-id="177a1-124">Содержит описание, как управлять сериализацией с помощью атрибутов.</span><span class="sxs-lookup"><span data-stu-id="177a1-124">Describes how to control serialization by using attributes.</span></span>

[<span data-ttu-id="177a1-125">Атрибуты управления сериализацией XML</span><span class="sxs-lookup"><span data-stu-id="177a1-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
<span data-ttu-id="177a1-126">Содержит список атрибутов, используемых для управления XML-сериализацией.</span><span class="sxs-lookup"><span data-stu-id="177a1-126">Lists the attributes that are used to control XML serialization.</span></span>

[<span data-ttu-id="177a1-127">Практическое руководство. Указание имени альтернативного элемента для XML Stream</span><span class="sxs-lookup"><span data-stu-id="177a1-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
<span data-ttu-id="177a1-128">Содержит сложный сценарий, в котором описывается, как создавать несколько потоков XML путем переопределения сериализации.</span><span class="sxs-lookup"><span data-stu-id="177a1-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>

[<span data-ttu-id="177a1-129">Практическое руководство. Управление сериализацией производных классов</span><span class="sxs-lookup"><span data-stu-id="177a1-129">How to: Control Serialization of Derived Classes</span></span>](how-to-control-serialization-of-derived-classes.md)  
<span data-ttu-id="177a1-130">Содержит пример, в котором показан способ управления сериализацией производных классов.</span><span class="sxs-lookup"><span data-stu-id="177a1-130">Provides an example of how to control the serialization of derived classes.</span></span>

[<span data-ttu-id="177a1-131">Практическое руководство. Квалификация элемента XML и имен атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="177a1-131">How to: Qualify XML Element and XML Attribute Names</span></span>](how-to-qualify-xml-element-and-xml-attribute-names.md)  
<span data-ttu-id="177a1-132">Содержит описание, как определять и управлять способом, с помощью которого в потоке XML используются пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="177a1-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>

[<span data-ttu-id="177a1-133">Сериализация XML с использованием XML-веб-служб</span><span class="sxs-lookup"><span data-stu-id="177a1-133">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)  
<span data-ttu-id="177a1-134">Содержит объяснение способов использования XML-сериализации в веб-службах XML.</span><span class="sxs-lookup"><span data-stu-id="177a1-134">Explains how XML serialization is used in XML Web services.</span></span>

[<span data-ttu-id="177a1-135">Практическое руководство. Сериализация объекта как Stream XML с кодировкой SOAP</span><span class="sxs-lookup"><span data-stu-id="177a1-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
<span data-ttu-id="177a1-136">Описывает использование <xref:System.Xml.Serialization.XmlSerializer> класс, чтобы создать закодированный SOAP XML потоки, которые соответствуют раздела 5 документа консорциума World Wide Web (W3C) [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span><span class="sxs-lookup"><span data-stu-id="177a1-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span></span>

[<span data-ttu-id="177a1-137">Практическое руководство. Переопределение сериализации XML с кодировкой SOAP</span><span class="sxs-lookup"><span data-stu-id="177a1-137">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
<span data-ttu-id="177a1-138">Содержит описание процесса переопределения XML-сериализации объектов как сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="177a1-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>

[<span data-ttu-id="177a1-139">Атрибуты управления сериализацией с кодировкой SOAP</span><span class="sxs-lookup"><span data-stu-id="177a1-139">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
<span data-ttu-id="177a1-140">Содержит список атрибутов, используемых для управления сериализацией с кодировкой SOAP.</span><span class="sxs-lookup"><span data-stu-id="177a1-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>

[<span data-ttu-id="177a1-141">Элемент \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="177a1-141">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)  
<span data-ttu-id="177a1-142">Элемент конфигурации верхнего уровня для управления XML-сериализацией.</span><span class="sxs-lookup"><span data-stu-id="177a1-142">The top-level configuration element for controlling XML serialization.</span></span>

[<span data-ttu-id="177a1-143">Элемент \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="177a1-143">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)  
<span data-ttu-id="177a1-144">Содержит информацию об управлении режимом сериализации объектов <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="177a1-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>

[<span data-ttu-id="177a1-145">Элемент \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="177a1-145">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)  
<span data-ttu-id="177a1-146">Содержит типы, используемые классом <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="177a1-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

[<span data-ttu-id="177a1-147">\<Добавить > элемент для \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="177a1-147">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)  
<span data-ttu-id="177a1-148">Добавляет типы, используемые классом <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="177a1-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

## <a name="related-sections"></a><span data-ttu-id="177a1-149">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="177a1-149">Related Sections</span></span>

<span data-ttu-id="177a1-150">[Веб-службы XML, созданные с помощью ASP.NET, и клиенты веб-служб с поддержкой XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="177a1-150">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>  
<span data-ttu-id="177a1-151">Содержит разделы с описаниями и объяснением программирования XML-веб-служб с помощью ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="177a1-151">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="177a1-152">См. также</span><span class="sxs-lookup"><span data-stu-id="177a1-152">See also</span></span>

- [<span data-ttu-id="177a1-153">Двоичная сериализация</span><span class="sxs-lookup"><span data-stu-id="177a1-153">Binary Serialization</span></span>](binary-serialization.md)
