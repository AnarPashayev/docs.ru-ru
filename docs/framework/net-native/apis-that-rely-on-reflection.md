---
title: API-интерфейсы, основанные на отражении
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a32e12b593f273c8b812390306c81b311da7c2a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624699"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="2e48a-102">API-интерфейсы, основанные на отражении</span><span class="sxs-lookup"><span data-stu-id="2e48a-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="2e48a-103">В некоторых случаях использование отражения в коде не очевидно, и цепочка инструментов [!INCLUDE[net_native](../../../includes/net-native-md.md)] не сохраняет метаданные, необходимые во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2e48a-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="2e48a-104">В этом разделе рассматриваются некоторые общие интерфейсы API или распространенные шаблоны программирования, которые не считаются частью API-интерфейса отражения, однако используют отражение для успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="2e48a-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="2e48a-105">При их использовании в исходном коде можно добавить сведения о них в файл директив среды выполнения (. rd.xml), чтобы вызовы этих интерфейсов API не создавали исключений [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) или других исключений во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2e48a-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="2e48a-106">Метод Type.MakeGenericType</span><span class="sxs-lookup"><span data-stu-id="2e48a-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="2e48a-107">Можно динамически создать экземпляр универсального типа `AppClass<T>` путем вызова метода <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="2e48a-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="2e48a-108">Для успешной работы кода во время выполнения необходимы несколько элементов метаданных.</span><span class="sxs-lookup"><span data-stu-id="2e48a-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="2e48a-109">Во-первых, метаданные `Browse` для универсального типа без экземпляров, `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="2e48a-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="2e48a-110">Это позволяет вызову метода <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> завершиться успешно и вернуть допустимый объект <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="2e48a-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="2e48a-111">Но даже при добавлении метаданных для универсального типа без экземпляров вызов метода <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> приводит к исключению [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md):</span><span class="sxs-lookup"><span data-stu-id="2e48a-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="2e48a-112">Можно добавить следующую директиву времени выполнения в файл директив среды выполнения, чтобы добавить метаданные `Activate` для конкретного экземпляра, созданного над `AppClass<T>` из <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="2e48a-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="2e48a-113">Каждый другой экземпляр над `AppClass<T>` требует отдельной директивы, если он создается с помощью метода <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> и не используется статически.</span><span class="sxs-lookup"><span data-stu-id="2e48a-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="2e48a-114">Метод MethodInfo.MakeGenericMethod</span><span class="sxs-lookup"><span data-stu-id="2e48a-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="2e48a-115">Определенный класс `Class1` с универсальным методом `GetMethod<T>(T t)`, `GetMethod` можно вызывать с помощью отражения, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="2e48a-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="2e48a-116">Для успешного выполнения этого кода необходимо несколько элементов метаданных:</span><span class="sxs-lookup"><span data-stu-id="2e48a-116">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="2e48a-117">Метаданные `Browse` для типа, метод которого необходимо вызвать.</span><span class="sxs-lookup"><span data-stu-id="2e48a-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="2e48a-118">Метаданные `Browse` для метода, который требуется вызвать.</span><span class="sxs-lookup"><span data-stu-id="2e48a-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="2e48a-119">Если это открытый метод, добавление открытых метаданных `Browse` для содержащего типа включает и сам метод.</span><span class="sxs-lookup"><span data-stu-id="2e48a-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="2e48a-120">Динамические метаданные для метода, который необходимо вызвать, для того, чтобы делегат вызова отражения не удалялся цепочкой инструментов [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e48a-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="2e48a-121">В случае отсутствия динамических метаданных для метода создается следующее исключение <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType>, когда вызывается метод:</span><span class="sxs-lookup"><span data-stu-id="2e48a-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="2e48a-122">Следующие директивы среды выполнения гарантируют доступность всех необходимых метаданных:</span><span class="sxs-lookup"><span data-stu-id="2e48a-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="2e48a-123">Директива `MethodInstantiation`  обязательна для каждого отдельного экземпляра метода, который вызывается динамически, а элемент `Arguments` обновляется для отображения аргумента каждого отдельного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="2e48a-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="2e48a-124">Методы метода Array.CreateInstance и Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="2e48a-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="2e48a-125">В следующем примере вызываются методы <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> и <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> на типе `Class1`.</span><span class="sxs-lookup"><span data-stu-id="2e48a-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="2e48a-126">При отсутствии метаданных массива возникает следующая ошибка:</span><span class="sxs-lookup"><span data-stu-id="2e48a-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="2e48a-127">метаданные `Browse` для типа массива требуются для динамического создания его экземпляра.</span><span class="sxs-lookup"><span data-stu-id="2e48a-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="2e48a-128">Следующая директива среды выполнения позволяет создать динамический экземпляр `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="2e48a-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e48a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="2e48a-129">See also</span></span>

- [<span data-ttu-id="2e48a-130">Начало работы</span><span class="sxs-lookup"><span data-stu-id="2e48a-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="2e48a-131">Справочник по конфигурационному файлу директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="2e48a-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
