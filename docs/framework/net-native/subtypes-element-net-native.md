---
title: <Subtypes> Элемент (машинный код .NET)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0ec1ed73148b319217a70cc3be99b486be2f8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208297"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="be59d-102">\<Подтипы > элемент (машинный код .NET)</span><span class="sxs-lookup"><span data-stu-id="be59d-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="be59d-103">Применяет политику среды выполнения для всех классов, унаследованных из содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="be59d-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be59d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be59d-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be59d-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="be59d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="be59d-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="be59d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be59d-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="be59d-107">Attributes</span></span>  
  
|<span data-ttu-id="be59d-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="be59d-108">Attribute</span></span>|<span data-ttu-id="be59d-109">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="be59d-109">Attribute type</span></span>|<span data-ttu-id="be59d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="be59d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="be59d-111">Отражение</span><span class="sxs-lookup"><span data-stu-id="be59d-111">Reflection</span></span>|<span data-ttu-id="be59d-112">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-112">Optional attribute.</span></span> <span data-ttu-id="be59d-113">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="be59d-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="be59d-114">Отражение</span><span class="sxs-lookup"><span data-stu-id="be59d-114">Reflection</span></span>|<span data-ttu-id="be59d-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-115">Optional attribute.</span></span> <span data-ttu-id="be59d-116">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="be59d-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="be59d-117">Отражение</span><span class="sxs-lookup"><span data-stu-id="be59d-117">Reflection</span></span>|<span data-ttu-id="be59d-118">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-118">Optional attribute.</span></span> <span data-ttu-id="be59d-119">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="be59d-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="be59d-120">Сериализация</span><span class="sxs-lookup"><span data-stu-id="be59d-120">Serialization</span></span>|<span data-ttu-id="be59d-121">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-121">Optional attribute.</span></span> <span data-ttu-id="be59d-122">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="be59d-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="be59d-123">Сериализация</span><span class="sxs-lookup"><span data-stu-id="be59d-123">Serialization</span></span>|<span data-ttu-id="be59d-124">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-124">Optional attribute.</span></span> <span data-ttu-id="be59d-125">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be59d-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="be59d-126">Сериализация</span><span class="sxs-lookup"><span data-stu-id="be59d-126">Serialization</span></span>|<span data-ttu-id="be59d-127">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-127">Optional attribute.</span></span> <span data-ttu-id="be59d-128">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be59d-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="be59d-129">Сериализация</span><span class="sxs-lookup"><span data-stu-id="be59d-129">Serialization</span></span>|<span data-ttu-id="be59d-130">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-130">Optional attribute.</span></span> <span data-ttu-id="be59d-131">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be59d-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="be59d-132">Interop</span><span class="sxs-lookup"><span data-stu-id="be59d-132">Interop</span></span>|<span data-ttu-id="be59d-133">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-133">Optional attribute.</span></span> <span data-ttu-id="be59d-134">Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.</span><span class="sxs-lookup"><span data-stu-id="be59d-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="be59d-135">Interop</span><span class="sxs-lookup"><span data-stu-id="be59d-135">Interop</span></span>|<span data-ttu-id="be59d-136">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-136">Optional attribute.</span></span> <span data-ttu-id="be59d-137">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="be59d-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="be59d-138">Interop</span><span class="sxs-lookup"><span data-stu-id="be59d-138">Interop</span></span>|<span data-ttu-id="be59d-139">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="be59d-139">Optional attribute.</span></span> <span data-ttu-id="be59d-140">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="be59d-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="be59d-141">Все атрибуты</span><span class="sxs-lookup"><span data-stu-id="be59d-141">All attributes</span></span>  
  
|<span data-ttu-id="be59d-142">Значение</span><span class="sxs-lookup"><span data-stu-id="be59d-142">Value</span></span>|<span data-ttu-id="be59d-143">Описание</span><span class="sxs-lookup"><span data-stu-id="be59d-143">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="be59d-144">policy_setting</span><span class="sxs-lookup"><span data-stu-id="be59d-144">policy_setting</span></span>*|<span data-ttu-id="be59d-145">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="be59d-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="be59d-146">Допустимые значения `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="be59d-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="be59d-147">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="be59d-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be59d-148">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="be59d-148">Child Elements</span></span>  
 <span data-ttu-id="be59d-149">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="be59d-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be59d-150">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="be59d-150">Parent Elements</span></span>  
  
|<span data-ttu-id="be59d-151">Элемент</span><span class="sxs-lookup"><span data-stu-id="be59d-151">Element</span></span>|<span data-ttu-id="be59d-152">Описание</span><span class="sxs-lookup"><span data-stu-id="be59d-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be59d-153">\<Тип ></span><span class="sxs-lookup"><span data-stu-id="be59d-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="be59d-154">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="be59d-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be59d-155">Примечания</span><span class="sxs-lookup"><span data-stu-id="be59d-155">Remarks</span></span>  
 <span data-ttu-id="be59d-156">Элемент `<Subtypes>` применяет политику ко всем подтипам его содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="be59d-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="be59d-157">Используется для применения различных политик для производных типов и их базовых классов.</span><span class="sxs-lookup"><span data-stu-id="be59d-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="be59d-158">Атрибуты отражения, сериализации и взаимодействия необязательны, несмотря на то, что по крайней мере один из них должен присутствовать.</span><span class="sxs-lookup"><span data-stu-id="be59d-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be59d-159">Пример</span><span class="sxs-lookup"><span data-stu-id="be59d-159">Example</span></span>  
 <span data-ttu-id="be59d-160">В следующем примере определяется класс с именем `BaseClass` и подкласс с именем `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="be59d-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="be59d-161">Как показано в следующем коде, файл директив среды выполнения явно задает политики `Dynamic` и `Activate` для `BaseClass` в `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="be59d-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="be59d-162">Из-за этого, объекты типа `BaseClass` не могут использоваться для динамического создания экземпляров или создания путем вызовов конструктора класса `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="be59d-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="be59d-163">Тем не менее, элемент `<Subtypes>` допускает использование классов, производных от `BaseClass`, для динамического создания экземпляров, а также для создания с помощью вызовов их конструкторов класса.</span><span class="sxs-lookup"><span data-stu-id="be59d-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="be59d-164">Благодаря директиве `<Subtypes>`, следующий код, динамически создающий экземпляр `Derived1` экземпляр путем вызова метода <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType>, выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="be59d-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="be59d-165">Здесь переменная блока представляет объект <xref:System.Windows.Controls.TextBlock> в пустом приложении для магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="be59d-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="be59d-166">См. также</span><span class="sxs-lookup"><span data-stu-id="be59d-166">See also</span></span>

- [<span data-ttu-id="be59d-167">\<Тип > элемент</span><span class="sxs-lookup"><span data-stu-id="be59d-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="be59d-168">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="be59d-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="be59d-169">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="be59d-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="be59d-170">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="be59d-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
