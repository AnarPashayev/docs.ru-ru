---
title: Просмотр сведений о типах
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e658b2c86eecdbc45a9adde8d28cfb890dd591b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956662"
---
# <a name="viewing-type-information"></a><span data-ttu-id="baf61-102">Просмотр сведений о типах</span><span class="sxs-lookup"><span data-stu-id="baf61-102">Viewing Type Information</span></span>
<span data-ttu-id="baf61-103">Класс <xref:System.Type?displayProperty=nameWithType> является центральной частью отражения.</span><span class="sxs-lookup"><span data-stu-id="baf61-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="baf61-104">Среда CLR создает объект **Type** для загруженного типа, когда он запрашивается отражением.</span><span class="sxs-lookup"><span data-stu-id="baf61-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="baf61-105">Используя методы, поля, свойства и вложенные классы объекта **Type**, можно получить полные сведения об этом типе.</span><span class="sxs-lookup"><span data-stu-id="baf61-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="baf61-106">Используйте <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> для получения объектов **Type** из сборок, которые не были загружены, передавая имя необходимого типа или типов.</span><span class="sxs-lookup"><span data-stu-id="baf61-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="baf61-107">Используйте <xref:System.Type.GetType%2A?displayProperty=nameWithType> для получения объектов **Type** из уже загруженной сборки.</span><span class="sxs-lookup"><span data-stu-id="baf61-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="baf61-108">Используйте <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> и <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> для получения объектов **Type** модуля.</span><span class="sxs-lookup"><span data-stu-id="baf61-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baf61-109">Если следует проверить универсальные типы и методы и управлять ими, ознакомьтесь с дополнительными сведениями, приведенными в разделах [Отражение и универсальные типы](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) и [Практическое руководство. Изучение универсальных типов и создание их экземпляров при помощи отражения](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="baf61-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="baf61-110">В приведенном ниже примере показан синтаксис для получения объекта <xref:System.Reflection.Assembly> и модуля сборки.</span><span class="sxs-lookup"><span data-stu-id="baf61-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="baf61-111">В приведенном ниже примере показано, как получать объекты **Type** из загруженной сборки.</span><span class="sxs-lookup"><span data-stu-id="baf61-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="baf61-112">После получения объекта **Type** сведения о членах этого типа можно получить разными способами.</span><span class="sxs-lookup"><span data-stu-id="baf61-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="baf61-113">Например, можно узнать о всех членах этого типа посредством вызова метода <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>, который получает массив объектов <xref:System.Reflection.MemberInfo>, где описываются все члены текущего типа.</span><span class="sxs-lookup"><span data-stu-id="baf61-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="baf61-114">Методы класса **Type** можно также использовать для получения сведений об одном конструкторе или нескольких конструкторах, методах, событиях, полях или свойствах, заданных по имени.</span><span class="sxs-lookup"><span data-stu-id="baf61-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="baf61-115">Например, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> инкапсулирует определенный конструктор текущего класса.</span><span class="sxs-lookup"><span data-stu-id="baf61-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="baf61-116">Если имеется объект **Type**, вы можете использовать свойство <xref:System.Type.Module%2A?displayProperty=nameWithType> для получения объекта, который инкапсулирует модуль, содержащий этот тип.</span><span class="sxs-lookup"><span data-stu-id="baf61-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="baf61-117">Используйте свойство <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> для обнаружения объекта, который инкапсулирует сборку, содержащую модуль.</span><span class="sxs-lookup"><span data-stu-id="baf61-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="baf61-118">Вы можете напрямую получить сборку, которая инкапсулирует тип, с помощью свойства <xref:System.Type.Assembly%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="baf61-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="baf61-119">System.Type и ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="baf61-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="baf61-120">В приведенном ниже примере показано, как получить список конструкторов класса, в этом случае для класса <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="baf61-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="baf61-121">MemberInfo, MethodInfo, FieldInfo и PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="baf61-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="baf61-122">Для получения сведений о методах, свойствах, событиях и полях типа используйте объекты <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo> и <xref:System.Reflection.PropertyInfo>.</span><span class="sxs-lookup"><span data-stu-id="baf61-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="baf61-123">В приведенном ниже примере используется объект **MemberInfo** для вывода количества членов в классе **System.IO.File** и свойство <xref:System.Type.IsPublic%2A> для определения степени доступности этого класса.</span><span class="sxs-lookup"><span data-stu-id="baf61-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="baf61-124">В приведенном ниже примере анализируется тип указанного члена.</span><span class="sxs-lookup"><span data-stu-id="baf61-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="baf61-125">Выполняется отражение члена класса **MemberInfo** и выводятся сведения о его типе.</span><span class="sxs-lookup"><span data-stu-id="baf61-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="baf61-126">В приведенном ниже примере используются все классы отражения **\*Info** вместе с классом <xref:System.Reflection.BindingFlags> для получения сведений о всех членах (конструкторах, полях, свойствах, событиях и методах) указанного класса, причем статические члены выводятся отдельно от членов экземпляров.</span><span class="sxs-lookup"><span data-stu-id="baf61-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="baf61-127">См. также</span><span class="sxs-lookup"><span data-stu-id="baf61-127">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="baf61-128">Отражение и универсальные типы</span><span class="sxs-lookup"><span data-stu-id="baf61-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
