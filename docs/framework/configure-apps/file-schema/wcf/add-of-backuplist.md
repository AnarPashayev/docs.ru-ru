---
title: <add> из <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850550"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="db610-102">\<add> из \<backupList></span><span class="sxs-lookup"><span data-stu-id="db610-102">\<add> of \<backupList></span></span>
<span data-ttu-id="db610-103">Представляет элемент конфигурации, в котором задается элемент резервной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="db610-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="db610-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db610-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db610-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="db610-105">Attributes and Elements</span></span>  
 <span data-ttu-id="db610-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="db610-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db610-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="db610-107">Attributes</span></span>  
  
|<span data-ttu-id="db610-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="db610-108">Attribute</span></span>|<span data-ttu-id="db610-109">Описание</span><span class="sxs-lookup"><span data-stu-id="db610-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db610-110">name</span><span class="sxs-lookup"><span data-stu-id="db610-110">name</span></span>|<span data-ttu-id="db610-111">Строка, задающая имя резервной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="db610-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db610-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="db610-112">Child Elements</span></span>  
 <span data-ttu-id="db610-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="db610-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db610-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="db610-114">Parent Elements</span></span>  
  
|<span data-ttu-id="db610-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="db610-115">Element</span></span>|<span data-ttu-id="db610-116">Описание</span><span class="sxs-lookup"><span data-stu-id="db610-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="db610-117">Содержит список конечных точек, которые служба маршрутизации будет использовать, если основная конечная точка недоступна.</span><span class="sxs-lookup"><span data-stu-id="db610-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db610-118">См. также</span><span class="sxs-lookup"><span data-stu-id="db610-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
