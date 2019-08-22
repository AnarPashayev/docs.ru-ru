---
title: Элемент <webProxyScript> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659037"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="8dccd-102">\<Элемент > Вебпроксискрипт (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="8dccd-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="8dccd-103">Настраивает характеристики сценария, используемого для обнаружения веб-прокси.</span><span class="sxs-lookup"><span data-stu-id="8dccd-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="8dccd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8dccd-104">\<configuration></span></span>  
<span data-ttu-id="8dccd-105">\<> System. NET</span><span class="sxs-lookup"><span data-stu-id="8dccd-105">\<system.net></span></span>  
<span data-ttu-id="8dccd-106">\<> параметров</span><span class="sxs-lookup"><span data-stu-id="8dccd-106">\<settings></span></span>  
<span data-ttu-id="8dccd-107">\<Вебпроксискрипт ></span><span class="sxs-lookup"><span data-stu-id="8dccd-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dccd-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8dccd-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dccd-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8dccd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8dccd-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8dccd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dccd-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8dccd-111">Attributes</span></span>  
  
|<span data-ttu-id="8dccd-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8dccd-112">Attribute</span></span>|<span data-ttu-id="8dccd-113">Описание</span><span class="sxs-lookup"><span data-stu-id="8dccd-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="8dccd-114">Указывает максимальное время загрузки скрипта в часах, минутах и секундах.</span><span class="sxs-lookup"><span data-stu-id="8dccd-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="8dccd-115">Значение по умолчанию — одна минута.</span><span class="sxs-lookup"><span data-stu-id="8dccd-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dccd-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8dccd-116">Child Elements</span></span>  
 <span data-ttu-id="8dccd-117">Нет.</span><span class="sxs-lookup"><span data-stu-id="8dccd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8dccd-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8dccd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8dccd-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="8dccd-119">Element</span></span>|<span data-ttu-id="8dccd-120">Описание</span><span class="sxs-lookup"><span data-stu-id="8dccd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dccd-121">Параметры</span><span class="sxs-lookup"><span data-stu-id="8dccd-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="8dccd-122">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="8dccd-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dccd-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="8dccd-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8dccd-124">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="8dccd-124">Configuration Files</span></span>  
 <span data-ttu-id="8dccd-125">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8dccd-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dccd-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8dccd-126">See also</span></span>

- [<span data-ttu-id="8dccd-127">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="8dccd-127">Network Settings Schema</span></span>](index.md)
