---
title: Пример слабо типизированных расширений
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 4d92f45382361c61fe9e7ac85ff5d604a2c87b27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592214"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="7e2a5-102">Пример слабо типизированных расширений</span><span class="sxs-lookup"><span data-stu-id="7e2a5-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="7e2a5-103">Объектная модель синдикации обеспечивает широкую поддержку работы с данными расширения - информацией, присутствующей в XML-представлении канала синдикации, но не предоставляемой в явном виде такими классами, как <xref:System.ServiceModel.Syndication.SyndicationFeed> и <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="7e2a5-104">Этот пример иллюстрирует основные приемы работы с данными расширения.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="7e2a5-105">В этом примере используется класс <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="7e2a5-106">Однако показанные в примере шаблоны можно использовать со всеми классами Syndication, которые поддерживают данные расширения:</span><span class="sxs-lookup"><span data-stu-id="7e2a5-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="7e2a5-107">Образец XML</span><span class="sxs-lookup"><span data-stu-id="7e2a5-107">Sample XML</span></span>  
 <span data-ttu-id="7e2a5-108">Для справки: в этом примере используется следующий XML-документ.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-108">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="7e2a5-109">Этот документ содержит следующие части данных расширения:</span><span class="sxs-lookup"><span data-stu-id="7e2a5-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="7e2a5-110">Атрибут `myAttribute` элемента `<feed>`.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="7e2a5-111">`<simpleString>` элемент.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="7e2a5-112">`<DataContractExtension>` элемент.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="7e2a5-113">`<XmlSerializerExtension>` элемент.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="7e2a5-114">`<xElementExtension>` элемент.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="7e2a5-115">Запись данных расширений</span><span class="sxs-lookup"><span data-stu-id="7e2a5-115">Writing Extension Data</span></span>  
 <span data-ttu-id="7e2a5-116">Расширения атрибутов создаются путем добавления записей в коллекцию <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="7e2a5-117">Расширения элементов создаются путем добавления записей в коллекцию <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="7e2a5-118">Эти расширения могут быть базовыми значениями, такими как строки, XML-сериализациями объектов платформы .NET Framework или XML-узлами, код которых написан вручную.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="7e2a5-119">В следующем примере кода создается элемент расширения с именем `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="7e2a5-120">Пространство имен XML для данного элемента является пустое пространство имен ("») и его значение является текстовый узел, содержащий строку «hello, world!».</span><span class="sxs-lookup"><span data-stu-id="7e2a5-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="7e2a5-121">Одним из способов создания расширений сложных элементов, содержащий много вложенных элементов, является использование для сериализации интерфейсов API платформы .NET Framework (поддерживаются как <xref:System.Runtime.Serialization.DataContractSerializer>, так и <xref:System.Xml.Serialization.XmlSerializer>), как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="7e2a5-122">В этом примере `DataContractExtension` и `XmlSerializerExtension` представляют собой пользовательские типы, созданные для использования с сериализатором.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="7e2a5-123">Класс <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> также может использоваться для создания расширений элементов из экземпляра <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="7e2a5-124">Это обеспечивает простую интеграцию с интерфейсами API, обрабатывающими XML, такими как <xref:System.Xml.Linq.XElement>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="7e2a5-125">Чтение данных расширений</span><span class="sxs-lookup"><span data-stu-id="7e2a5-125">Reading Extension Data</span></span>  
 <span data-ttu-id="7e2a5-126">Значения для расширений атрибутов можно получить, произведя поиск атрибута в коллекции <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> по его имени <xref:System.Xml.XmlQualifiedName>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="7e2a5-127">Для доступа к расширениям элементов служит метод `ReadElementExtensions<T>`.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="7e2a5-128">Можно также получить средство чтения `XmlReader` для расширений отдельных элементов с помощью метода <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e2a5-129">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="7e2a5-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7e2a5-130">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7e2a5-131">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7e2a5-132">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a5-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7e2a5-133">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e2a5-134">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7e2a5-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7e2a5-135">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e2a5-136">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7e2a5-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="7e2a5-137">См. также</span><span class="sxs-lookup"><span data-stu-id="7e2a5-137">See also</span></span>

- [<span data-ttu-id="7e2a5-138">Строго типизированные расширения</span><span class="sxs-lookup"><span data-stu-id="7e2a5-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="7e2a5-139">Синдикация WCF</span><span class="sxs-lookup"><span data-stu-id="7e2a5-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
