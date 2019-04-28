---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760692"
---
# <a name="knowntype"></a><span data-ttu-id="3c81b-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="3c81b-101">\<knownType></span></span>
<span data-ttu-id="3c81b-102">Задает тип, используемый <xref:System.Runtime.Serialization.DataContractSerializer> во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="3c81b-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="3c81b-103">Элемент задает «известный тип», возвращаемый полем или свойством «объявленного типа».</span><span class="sxs-lookup"><span data-stu-id="3c81b-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="3c81b-104">Дополнительные сведения см. в разделе [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3c81b-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="3c81b-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3c81b-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="3c81b-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3c81b-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="3c81b-107">\<declaredTypes > элемент</span><span class="sxs-lookup"><span data-stu-id="3c81b-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="3c81b-108">\<Добавить > из \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="3c81b-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="3c81b-109">\<knownType > элемент</span><span class="sxs-lookup"><span data-stu-id="3c81b-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c81b-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c81b-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="3c81b-111">Тип</span><span class="sxs-lookup"><span data-stu-id="3c81b-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c81b-112">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3c81b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3c81b-113">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3c81b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c81b-114">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3c81b-114">Attributes</span></span>  
  
|<span data-ttu-id="3c81b-115">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3c81b-115">Attribute</span></span>|<span data-ttu-id="3c81b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="3c81b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c81b-117">type</span><span class="sxs-lookup"><span data-stu-id="3c81b-117">type</span></span>|<span data-ttu-id="3c81b-118">Задает тип (в том числе пространство имен), имя сборки, версию, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3c81b-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c81b-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3c81b-119">Child Elements</span></span>  
  
|<span data-ttu-id="3c81b-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="3c81b-120">Element</span></span>|<span data-ttu-id="3c81b-121">Описание</span><span class="sxs-lookup"><span data-stu-id="3c81b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c81b-122">\<Параметр ></span><span class="sxs-lookup"><span data-stu-id="3c81b-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="3c81b-123">Задает индекс параметра в том случае, если объявленный тип является универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="3c81b-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c81b-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3c81b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3c81b-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="3c81b-125">Element</span></span>|<span data-ttu-id="3c81b-126">Описание</span><span class="sxs-lookup"><span data-stu-id="3c81b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c81b-127">\<add></span><span class="sxs-lookup"><span data-stu-id="3c81b-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="3c81b-128">Добавляет объявленный тип в коллекцию объявленных типов.</span><span class="sxs-lookup"><span data-stu-id="3c81b-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c81b-129">Примечания</span><span class="sxs-lookup"><span data-stu-id="3c81b-129">Remarks</span></span>  
 <span data-ttu-id="3c81b-130">Дополнительные сведения об известных типах см. в разделе [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) и <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3c81b-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3c81b-131">См. в разделе [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) пример использования этого элемента.</span><span class="sxs-lookup"><span data-stu-id="3c81b-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c81b-132">Пример</span><span class="sxs-lookup"><span data-stu-id="3c81b-132">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="3c81b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="3c81b-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="3c81b-134">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="3c81b-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="3c81b-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3c81b-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="3c81b-136">\<add></span><span class="sxs-lookup"><span data-stu-id="3c81b-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
