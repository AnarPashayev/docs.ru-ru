---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704145"
---
# <a name="datacontractserializer"></a><span data-ttu-id="50e96-101">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="50e96-101">\<dataContractSerializer></span></span>
<span data-ttu-id="50e96-102">Содержит данные конфигурации для <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="50e96-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="50e96-103">Этот элемент присутствует в двух разных иерархиях.</span><span class="sxs-lookup"><span data-stu-id="50e96-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="50e96-104">Одна из них указана в следующем разделе «Иерархия схемы», а другая - в разделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="50e96-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="50e96-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="50e96-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="50e96-106">\<варианты поведения ></span><span class="sxs-lookup"><span data-stu-id="50e96-106">\<behaviors></span></span>  
<span data-ttu-id="50e96-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="50e96-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="50e96-108">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="50e96-108">\<behavior></span></span>  
<span data-ttu-id="50e96-109">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="50e96-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e96-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50e96-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50e96-111">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="50e96-111">Attributes and Elements</span></span>  
 <span data-ttu-id="50e96-112">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="50e96-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50e96-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="50e96-113">Attributes</span></span>  
  
|<span data-ttu-id="50e96-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="50e96-114">Element</span></span>|<span data-ttu-id="50e96-115">Описание</span><span class="sxs-lookup"><span data-stu-id="50e96-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50e96-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="50e96-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="50e96-117">Логическое значение, указывающее, пропускать ли данные, предоставленные конечной точкой при ее сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="50e96-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="50e96-118">Этот атрибут можно задать только в `<dataContractSerializer>` в элементе `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="50e96-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="50e96-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="50e96-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="50e96-120">Целое число, указывающее максимальное количество элементов для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="50e96-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="50e96-121">Этот атрибут имеет значение 65 536.</span><span class="sxs-lookup"><span data-stu-id="50e96-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50e96-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="50e96-122">Child Elements</span></span>  
 <span data-ttu-id="50e96-123">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="50e96-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50e96-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="50e96-124">Parent Elements</span></span>  
  
|<span data-ttu-id="50e96-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="50e96-125">Element</span></span>|<span data-ttu-id="50e96-126">Описание</span><span class="sxs-lookup"><span data-stu-id="50e96-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50e96-127">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="50e96-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="50e96-128">Коллекция параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="50e96-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="50e96-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="50e96-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="50e96-130">Представляет корневой элемент для раздела пространства имен <xref:System.Runtime.Serialization> и содержит элементы для установки параметров <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="50e96-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e96-131">Примечания</span><span class="sxs-lookup"><span data-stu-id="50e96-131">Remarks</span></span>  
 <span data-ttu-id="50e96-132">Как уже говорилось в начале этого раздела, это вторая иерархия, в которой \<X509Extension > происходит элемент.</span><span class="sxs-lookup"><span data-stu-id="50e96-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="50e96-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="50e96-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="50e96-134">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="50e96-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="50e96-135">Дополнительные сведения об известных типах см. в разделе <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="50e96-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e96-136">См. также</span><span class="sxs-lookup"><span data-stu-id="50e96-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="50e96-137">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="50e96-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="50e96-138">Передача данных и сериализация</span><span class="sxs-lookup"><span data-stu-id="50e96-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
