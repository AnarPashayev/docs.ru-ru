---
title: <Parameter> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 7e812ab60eb0a89eb868346733a8ea74e2f76d3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287869"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="6f918-102">\<Parameter> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6f918-102">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="6f918-103">Применяет политику отражения к типу аргумента, переданного методу.</span><span class="sxs-lookup"><span data-stu-id="6f918-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f918-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6f918-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f918-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6f918-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6f918-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6f918-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f918-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6f918-107">Attributes</span></span>  
  
|<span data-ttu-id="6f918-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="6f918-108">Attribute</span></span>|<span data-ttu-id="6f918-109">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="6f918-109">Attribute type</span></span>|<span data-ttu-id="6f918-110">Описание</span><span class="sxs-lookup"><span data-stu-id="6f918-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6f918-111">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="6f918-111">General</span></span>|<span data-ttu-id="6f918-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-112">Required attribute.</span></span> <span data-ttu-id="6f918-113">Имя параметра.</span><span class="sxs-lookup"><span data-stu-id="6f918-113">The parameter name.</span></span> <span data-ttu-id="6f918-114">Например, сигнатура метода `String.CompareTo(Object value)`, значение `Name` — атрибут «value».</span><span class="sxs-lookup"><span data-stu-id="6f918-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="6f918-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="6f918-115">Reflection</span></span>|<span data-ttu-id="6f918-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-116">Optional attribute.</span></span> <span data-ttu-id="6f918-117">Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.</span><span class="sxs-lookup"><span data-stu-id="6f918-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6f918-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="6f918-118">Reflection</span></span>|<span data-ttu-id="6f918-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-119">Optional attribute.</span></span> <span data-ttu-id="6f918-120">Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6f918-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6f918-121">Отражение</span><span class="sxs-lookup"><span data-stu-id="6f918-121">Reflection</span></span>|<span data-ttu-id="6f918-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-122">Optional attribute.</span></span> <span data-ttu-id="6f918-123">Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.</span><span class="sxs-lookup"><span data-stu-id="6f918-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6f918-124">Сериализация</span><span class="sxs-lookup"><span data-stu-id="6f918-124">Serialization</span></span>|<span data-ttu-id="6f918-125">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-125">Optional attribute.</span></span> <span data-ttu-id="6f918-126">Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="6f918-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6f918-127">Сериализация</span><span class="sxs-lookup"><span data-stu-id="6f918-127">Serialization</span></span>|<span data-ttu-id="6f918-128">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-128">Optional attribute.</span></span> <span data-ttu-id="6f918-129">Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f918-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6f918-130">Сериализация</span><span class="sxs-lookup"><span data-stu-id="6f918-130">Serialization</span></span>|<span data-ttu-id="6f918-131">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-131">Optional attribute.</span></span> <span data-ttu-id="6f918-132">Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f918-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6f918-133">Сериализация</span><span class="sxs-lookup"><span data-stu-id="6f918-133">Serialization</span></span>|<span data-ttu-id="6f918-134">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-134">Optional attribute.</span></span> <span data-ttu-id="6f918-135">Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f918-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6f918-136">Interop</span><span class="sxs-lookup"><span data-stu-id="6f918-136">Interop</span></span>|<span data-ttu-id="6f918-137">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-137">Optional attribute.</span></span> <span data-ttu-id="6f918-138">Определяет политику для маршалинга ссылочных типов в WinRT и COM.</span><span class="sxs-lookup"><span data-stu-id="6f918-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6f918-139">Interop</span><span class="sxs-lookup"><span data-stu-id="6f918-139">Interop</span></span>|<span data-ttu-id="6f918-140">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-140">Optional attribute.</span></span> <span data-ttu-id="6f918-141">Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.</span><span class="sxs-lookup"><span data-stu-id="6f918-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6f918-142">Interop</span><span class="sxs-lookup"><span data-stu-id="6f918-142">Interop</span></span>|<span data-ttu-id="6f918-143">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6f918-143">Optional attribute.</span></span> <span data-ttu-id="6f918-144">Определяет политики для маршалинга типов значений в машинный код.</span><span class="sxs-lookup"><span data-stu-id="6f918-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6f918-145">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="6f918-145">Name attribute</span></span>  
  
|<span data-ttu-id="6f918-146">Значение</span><span class="sxs-lookup"><span data-stu-id="6f918-146">Value</span></span>|<span data-ttu-id="6f918-147">Описание</span><span class="sxs-lookup"><span data-stu-id="6f918-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f918-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="6f918-148">*parameter_name*</span></span>|<span data-ttu-id="6f918-149">Имя параметра метода, к которому применяется политика.</span><span class="sxs-lookup"><span data-stu-id="6f918-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="6f918-150">Например, сигнатура метода `String.CompareTo(Object value)`, значение `Name` — атрибут «value».</span><span class="sxs-lookup"><span data-stu-id="6f918-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6f918-151">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="6f918-151">All other attributes</span></span>  
  
|<span data-ttu-id="6f918-152">Значение</span><span class="sxs-lookup"><span data-stu-id="6f918-152">Value</span></span>|<span data-ttu-id="6f918-153">Описание</span><span class="sxs-lookup"><span data-stu-id="6f918-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f918-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6f918-154">*policy_setting*</span></span>|<span data-ttu-id="6f918-155">Параметр, применяемый для этого типа политики.</span><span class="sxs-lookup"><span data-stu-id="6f918-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="6f918-156">Допустимые значения: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6f918-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6f918-157">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6f918-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f918-158">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6f918-158">Child Elements</span></span>  

 <span data-ttu-id="6f918-159">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6f918-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f918-160">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6f918-160">Parent Elements</span></span>  
  
|<span data-ttu-id="6f918-161">Элемент</span><span class="sxs-lookup"><span data-stu-id="6f918-161">Element</span></span>|<span data-ttu-id="6f918-162">Описание</span><span class="sxs-lookup"><span data-stu-id="6f918-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="6f918-163">Применяет политику отражения среды выполнения к конструктору или методу.</span><span class="sxs-lookup"><span data-stu-id="6f918-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f918-164">Примечания</span><span class="sxs-lookup"><span data-stu-id="6f918-164">Remarks</span></span>  

 <span data-ttu-id="6f918-165">`<Parameter>`Элемент является дочерним по отношению к [\<Method>](method-element-net-native.md) элементу и используется для применения политики к конкретному параметру метода.</span><span class="sxs-lookup"><span data-stu-id="6f918-165">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="6f918-166">Конкретный параметр метода указывается по имени, а не по типу.</span><span class="sxs-lookup"><span data-stu-id="6f918-166">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="6f918-167">По крайней мере один атрибут, который представляет тип политики, такие как `Activate` или `Dynamic`, должен присутствовать.</span><span class="sxs-lookup"><span data-stu-id="6f918-167">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f918-168">См. также</span><span class="sxs-lookup"><span data-stu-id="6f918-168">See also</span></span>

- [<span data-ttu-id="6f918-169">\<Method> Элемент</span><span class="sxs-lookup"><span data-stu-id="6f918-169">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="6f918-170">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6f918-170">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6f918-171">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="6f918-171">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="6f918-172">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="6f918-172">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
