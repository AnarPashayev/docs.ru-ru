---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c34eba2614a354f1753d8da077f8653f2c260a97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165897"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="ef0d3-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="ef0d3-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="ef0d3-103">Представляет корневой элемент для раздела пространства имен <xref:System.Runtime.Serialization> и содержит элементы для установки параметров <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ef0d3-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="ef0d3-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="ef0d3-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef0d3-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef0d3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ef0d3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ef0d3-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ef0d3-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef0d3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ef0d3-108">Attributes</span></span>  
 <span data-ttu-id="ef0d3-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ef0d3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef0d3-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ef0d3-110">Child Elements</span></span>  
  
|<span data-ttu-id="ef0d3-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="ef0d3-111">Element</span></span>|<span data-ttu-id="ef0d3-112">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0d3-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ef0d3-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="ef0d3-114">Включает добавление известных типов при десериализации.</span><span class="sxs-lookup"><span data-stu-id="ef0d3-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef0d3-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ef0d3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ef0d3-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="ef0d3-116">Element</span></span>|<span data-ttu-id="ef0d3-117">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0d3-118">\<Конфигурация > элемент</span><span class="sxs-lookup"><span data-stu-id="ef0d3-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ef0d3-119">Элемент конфигурации верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="ef0d3-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef0d3-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ef0d3-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="ef0d3-121">Использование контрактов данных</span><span class="sxs-lookup"><span data-stu-id="ef0d3-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="ef0d3-122">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="ef0d3-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
