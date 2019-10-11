---
title: Пример DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 1711c826397dfb8b54ecedee08e88e67cb58d2a4
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180231"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="28d9c-102">Пример DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="28d9c-102">DataContractJsonSerializer sample</span></span>
<span data-ttu-id="28d9c-103">В этом образце показано, как с помощью объекта <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> сериализовать и десериализовать данные в формате JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="28d9c-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="28d9c-104">Этот модуль сериализации преобразует данные JSON в экземпляры типов .NET Framework и обратно в данные JSON.</span><span class="sxs-lookup"><span data-stu-id="28d9c-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="28d9c-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> поддерживает те же типы, что и <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28d9c-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="28d9c-106">Формат данных JSON бывает особенно полезен при написании веб-приложений AJAX (Asynchronous JavaScript and XML).</span><span class="sxs-lookup"><span data-stu-id="28d9c-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="28d9c-107">Поддержка AJAX в Windows Communication Foundation (WCF) оптимизирована для использования с ASP.NET AJAX через элемент управления ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="28d9c-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="28d9c-108">Примеры использования Windows Communication Foundation (WCF) с ASP.NET AJAX см. в разделе [примеры AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="28d9c-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28d9c-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="28d9c-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="28d9c-110">В этом образце для демонстрации сериализации и десериализации используется контракт данных `Person`.</span><span class="sxs-lookup"><span data-stu-id="28d9c-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="28d9c-111">Чтобы сериализовать экземпляр типа `Person` в формат JSON, создайте объект <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> и с помощью метода `WriteObject` запишите данные JSON в поток.</span><span class="sxs-lookup"><span data-stu-id="28d9c-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="28d9c-112">Поток памяти содержит допустимые данные JSON.</span><span class="sxs-lookup"><span data-stu-id="28d9c-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="28d9c-113">В этом образце показана десериализация данных JSON в объект.</span><span class="sxs-lookup"><span data-stu-id="28d9c-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="28d9c-114">Для этого необходимо перемотать назад поток и вызвать метод `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="28d9c-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="28d9c-115">Проверка объекта `p2` позволяет понять, что данные JSON были десериализованы правильно.</span><span class="sxs-lookup"><span data-stu-id="28d9c-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28d9c-116">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="28d9c-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28d9c-117">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="28d9c-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="28d9c-118">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28d9c-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28d9c-119">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="28d9c-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28d9c-120">Настройка, построение и выполнение примера</span><span class="sxs-lookup"><span data-stu-id="28d9c-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="28d9c-121">Создайте решение Жсонсериализатион. sln, как описано в разделе [Создание примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28d9c-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="28d9c-122">Запустите получившееся консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="28d9c-122">Run the resulting console application.</span></span>  
