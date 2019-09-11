---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855199"
---
# <a name="filtertables"></a><span data-ttu-id="b50d9-101">\<Филтертаблес ></span><span class="sxs-lookup"><span data-stu-id="b50d9-101">\<filterTables></span></span>
<span data-ttu-id="b50d9-102">Представляет раздел конфигурации, в котором определены таблицы маршрутизации, содержащие сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при совпадении с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="b50d9-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="b50d9-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b50d9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b50d9-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b50d9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b50d9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> маршрутизации**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="b50d9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="b50d9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Филтертаблес >**</span><span class="sxs-lookup"><span data-stu-id="b50d9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50d9-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b50d9-107">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b50d9-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b50d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b50d9-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b50d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b50d9-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b50d9-110">Attributes</span></span>  
 <span data-ttu-id="b50d9-111">Нет.</span><span class="sxs-lookup"><span data-stu-id="b50d9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b50d9-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b50d9-112">Child Elements</span></span>  
  
|<span data-ttu-id="b50d9-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="b50d9-113">Element</span></span>|<span data-ttu-id="b50d9-114">Описание</span><span class="sxs-lookup"><span data-stu-id="b50d9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b50d9-115">\<Фильтры></span><span class="sxs-lookup"><span data-stu-id="b50d9-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="b50d9-116">Таблица маршрутизации, содержащая сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при условии совпадения с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="b50d9-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b50d9-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b50d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b50d9-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="b50d9-118">Element</span></span>|<span data-ttu-id="b50d9-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b50d9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b50d9-120">\<> маршрутизации</span><span class="sxs-lookup"><span data-stu-id="b50d9-120">\<routing></span></span>](routing.md)|<span data-ttu-id="b50d9-121">Раздел конфигурации, содержащий фильтры и таблицы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="b50d9-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b50d9-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b50d9-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
