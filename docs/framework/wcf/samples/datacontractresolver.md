---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 981b70011979e1e0fbd8fc6b22ba54774c824342
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325180"
---
# <a name="datacontractresolver"></a><span data-ttu-id="c2435-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="c2435-102">DataContractResolver</span></span>
<span data-ttu-id="c2435-103">В этом образце показано, как можно настроить процессы сериализации и десериализации с помощью класса <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="c2435-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="c2435-104">Этот образец демонстрирует применение класса DataContractResolver для сопоставления типов CLR с представлением xsi:type во время сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="c2435-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="c2435-105">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="c2435-105">Sample Details</span></span>
 <span data-ttu-id="c2435-106">В образце определяются следующие типы CLR.</span><span class="sxs-lookup"><span data-stu-id="c2435-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="c2435-107">Образец загружает сборку, извлекает каждый из следующих типов, а затем сериализует и десериализует их.</span><span class="sxs-lookup"><span data-stu-id="c2435-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="c2435-108">Как показано в следующем примере, класс <xref:System.Runtime.Serialization.DataContractResolver> участвует в процессе сериализации, передавая экземпляр производного класса <xref:System.Runtime.Serialization.DataContractResolver> в конструктор <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c2435-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="c2435-109">Затем образец сериализует типы CLR, как показано в следующем примере программного кода.</span><span class="sxs-lookup"><span data-stu-id="c2435-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="c2435-110">Затем образец десериализует типы xsi:type, как показано в следующем примере программного кода.</span><span class="sxs-lookup"><span data-stu-id="c2435-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="c2435-111">Поскольку пользовательский класс <xref:System.Runtime.Serialization.DataContractResolver> передается в конструктор <xref:System.Runtime.Serialization.DataContractSerializer>, во время сериализации вызывается метод <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>, чтобы сопоставить тип CLR с эквивалентным элементом `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="c2435-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="c2435-112">Аналогично во время десериализации вызывается метод <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>, чтобы сопоставить элемент `xsi:type` с эквивалентным типом CLR.</span><span class="sxs-lookup"><span data-stu-id="c2435-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="c2435-113">В этом образце <xref:System.Runtime.Serialization.DataContractResolver> определен, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c2435-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="c2435-114">В следующем примере кода представлен класс, являющийся производным от <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="c2435-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="c2435-115">Будучи частью образца, проект «Type» создает сборку со всеми типами, которые используются в этом образце.</span><span class="sxs-lookup"><span data-stu-id="c2435-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="c2435-116">Используйте этот проект для добавления, удаления или изменения типов, которые будут сериализованы.</span><span class="sxs-lookup"><span data-stu-id="c2435-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="c2435-117">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="c2435-117">To use this sample</span></span>

1. <span data-ttu-id="c2435-118">Откройте файл решения DCRSample.sln в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c2435-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="c2435-119">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="c2435-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="c2435-120">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c2435-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2435-121">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="c2435-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2435-122">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="c2435-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2435-123">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="c2435-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="c2435-124">См. также</span><span class="sxs-lookup"><span data-stu-id="c2435-124">See also</span></span>

- [<span data-ttu-id="c2435-125">Использование арбитра контрактов данных</span><span class="sxs-lookup"><span data-stu-id="c2435-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
