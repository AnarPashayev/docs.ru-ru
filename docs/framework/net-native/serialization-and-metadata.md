---
title: Сериализация и метаданные
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e7a8e6509cea5f9035e3b8544aa37aa99681822
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650316"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="fe902-102">Сериализация и метаданные</span><span class="sxs-lookup"><span data-stu-id="fe902-102">Serialization and Metadata</span></span>
<span data-ttu-id="fe902-103">Если ваше приложение сериализует и десериализует объекты, может потребоваться добавить записи в файл директив среды выполнения (. rd.xml) файл, чтобы гарантировать наличие необходимых метаданных во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="fe902-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="fe902-104">Существует две категории сериализаторов, и каждый требует различной обработки в файла директив среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="fe902-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="fe902-105">Сериализиторы сторонних поставщиков на основе отражения.</span><span class="sxs-lookup"><span data-stu-id="fe902-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="fe902-106">Они требуют изменений в файле директив среды выполнения и рассматриваются в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="fe902-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="fe902-107">Сериализиторы без отражения содержатся в библиотеке классов платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe902-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="fe902-108">Они могут потребовать внесения изменений в файл директив среды выполнения и обсуждаются в разделе [Сериализаторы Майкрософт](#Microsoft).</span><span class="sxs-lookup"><span data-stu-id="fe902-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="fe902-109">Сериализаторы сторонних поставщиков</span><span class="sxs-lookup"><span data-stu-id="fe902-109">Third-party serializers</span></span>  
 <span data-ttu-id="fe902-110">Сериализаторы сторонних поставщиков, включая Newtonsoft.JSON, обычно основаны на отражении.</span><span class="sxs-lookup"><span data-stu-id="fe902-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="fe902-111">Учитывая большой двоичный объект (BLOB) из сериализованных данных, поля данных назначаются конкретному типу путем поиска полей типа целевого объекта по имени.</span><span class="sxs-lookup"><span data-stu-id="fe902-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="fe902-112">Как минимум, использование этих библиотек приводит к исключениям [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) для каждого объекта <xref:System.Type> при попытке сериализации или десериализации в коллекции `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="fe902-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="fe902-113">Самый простой способ решения проблем, вызванных отсутствующими метаданными для этих сериализаторов, состоит в сборе типов, которые будут использоваться при сериализации в одном пространстве имен (например, `App.Models`) и применить к нему директиву метаданных `Serialize`:</span><span class="sxs-lookup"><span data-stu-id="fe902-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="fe902-114">Информацию о синтаксисе, используемом в примере, см. в разделе [Элемент \<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="fe902-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="fe902-115">Сериализаторы Microsoft</span><span class="sxs-lookup"><span data-stu-id="fe902-115">Microsoft serializers</span></span>  
 <span data-ttu-id="fe902-116">Несмотря на то, что классы <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> и <xref:System.Xml.Serialization.XmlSerializer> не рассчитывают на отражение, они требуют создания кода на основе объекта для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="fe902-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="fe902-117">Перегруженные конструкторы для каждого сериализатора содержа параметр <xref:System.Type>, который задает тип для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="fe902-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="fe902-118">Способ указания этого типа в коде определяет действие, которое необходимо выполнить, как описано в следующих двух разделах.</span><span class="sxs-lookup"><span data-stu-id="fe902-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="fe902-119">TypeOf используется в конструкторе</span><span class="sxs-lookup"><span data-stu-id="fe902-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="fe902-120">Если вызвать конструктор этих классов сериализации и включить ключевое слово C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) в вызов метода **, не нужно прикладывать дополнительные усилия**.</span><span class="sxs-lookup"><span data-stu-id="fe902-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="fe902-121">Например, в каждом из следующих вызовов конструктора класса сериализации ключевое слово `typeof`используется как часть выражения, переданного в конструктор.</span><span class="sxs-lookup"><span data-stu-id="fe902-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="fe902-122">Компилятор [!INCLUDE[net_native](../../../includes/net-native-md.md)] автоматически будет обрабатывать этот код.</span><span class="sxs-lookup"><span data-stu-id="fe902-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="fe902-123">TypeOf, использованный за пределами конструктора</span><span class="sxs-lookup"><span data-stu-id="fe902-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="fe902-124">Если вызвать конструктор этих классов сериализации и использовать ключевое слово C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) за пределами выражения, предоставленного для параметра <xref:System.Type> конструктора, как в следующем коде, компилятор [!INCLUDE[net_native](../../../includes/net-native-md.md)] не может разрешить тип:</span><span class="sxs-lookup"><span data-stu-id="fe902-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="fe902-125">В этом случае необходимо указать тип в файле директив среды выполнения, добавив следующую запись:</span><span class="sxs-lookup"><span data-stu-id="fe902-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="fe902-126">Аналогичным образом, если вызвать конструктор <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> и предоставить массив дополнительных объектов <xref:System.Type> для сериализации, как показано в следующем коде, компилятору [!INCLUDE[net_native](../../../includes/net-native-md.md)] не удается разрешить эти типы.</span><span class="sxs-lookup"><span data-stu-id="fe902-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="fe902-127">Необходимо добавить следующие записи для каждого типа в файл директив среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="fe902-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="fe902-128">Информацию о синтаксисе, используемом в примере, см. в разделе [Элемент \<Type>](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="fe902-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe902-129">См. также</span><span class="sxs-lookup"><span data-stu-id="fe902-129">See also</span></span>

- [<span data-ttu-id="fe902-130">Справочник по конфигурационному файлу директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="fe902-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="fe902-131">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="fe902-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="fe902-132">\<Тип > элемент</span><span class="sxs-lookup"><span data-stu-id="fe902-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="fe902-133">Элемент \<Namespace></span><span class="sxs-lookup"><span data-stu-id="fe902-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
