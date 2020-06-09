---
title: Пример DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 4aa0ee679ae424251000b14abfbacf0590a6ccd3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592038"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="1b98f-102">Пример DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="1b98f-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="1b98f-103">Этот пример предназначен для <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="1b98f-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="1b98f-104">В большинстве сценариев, в которых участвует сериализация и десериализация JSON, мы рекомендуем использовать интерфейсы API в [пространстве имен System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b98f-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="1b98f-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> поддерживает те же типы, что и <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1b98f-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1b98f-106">Формат данных JSON бывает особенно полезен при написании веб-приложений AJAX (Asynchronous JavaScript and XML).</span><span class="sxs-lookup"><span data-stu-id="1b98f-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="1b98f-107">Поддержка AJAX в Windows Communication Foundation (WCF) оптимизирована для использования с ASP.NET AJAX через элемент управления ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="1b98f-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="1b98f-108">Примеры использования Windows Communication Foundation (WCF) с ASP.NET AJAX см. в разделе [примеры AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="1b98f-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="1b98f-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="1b98f-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="1b98f-110">В этом образце для демонстрации сериализации и десериализации используется контракт данных `Person`.</span><span class="sxs-lookup"><span data-stu-id="1b98f-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="1b98f-111">Чтобы сериализовать экземпляр типа `Person` в формат JSON, создайте объект <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> и с помощью метода `WriteObject` запишите данные JSON в поток.</span><span class="sxs-lookup"><span data-stu-id="1b98f-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="1b98f-112">Поток памяти содержит допустимые данные JSON.</span><span class="sxs-lookup"><span data-stu-id="1b98f-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="1b98f-113">В этом образце показана десериализация данных JSON в объект.</span><span class="sxs-lookup"><span data-stu-id="1b98f-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="1b98f-114">Для этого необходимо перемотать назад поток и вызвать метод `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="1b98f-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="1b98f-115">Проверка объекта `p2` позволяет понять, что данные JSON были десериализованы правильно.</span><span class="sxs-lookup"><span data-stu-id="1b98f-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1b98f-116">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1b98f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1b98f-117">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1b98f-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1b98f-118">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1b98f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b98f-119">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1b98f-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1b98f-120">Настройка, построение и выполнение примера</span><span class="sxs-lookup"><span data-stu-id="1b98f-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="1b98f-121">Создайте решение Жсонсериализатион. sln, как описано в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b98f-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="1b98f-122">Запустите получившееся консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="1b98f-122">Run the resulting console application.</span></span>  
