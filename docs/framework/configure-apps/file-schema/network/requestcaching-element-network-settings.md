---
title: Элемент <requestCaching> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697824"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="e63bf-102">Элемент \<requestCaching> (сетевые параметры)</span><span class="sxs-lookup"><span data-stu-id="e63bf-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="e63bf-103">Управляет механизмом кэширования для сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="e63bf-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="e63bf-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e63bf-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e63bf-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e63bf-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="e63bf-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="e63bf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63bf-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e63bf-107">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e63bf-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e63bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e63bf-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e63bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e63bf-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e63bf-110">Attributes</span></span>  
  
|<span data-ttu-id="e63bf-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e63bf-111">Attribute</span></span>|<span data-ttu-id="e63bf-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e63bf-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="e63bf-113">Указывает, обеспечивает ли кэш изоляцию между данными разных пользователей.</span><span class="sxs-lookup"><span data-stu-id="e63bf-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="e63bf-114">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="e63bf-114">The default value is `true`.</span></span> <span data-ttu-id="e63bf-115">Для приложений среднего уровня это значение должно быть `false`.</span><span class="sxs-lookup"><span data-stu-id="e63bf-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="e63bf-116">Указывает, что кэширование отключено для всех веб-ответов и не может быть переопределено программным способом.</span><span class="sxs-lookup"><span data-stu-id="e63bf-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="e63bf-117">Одно из значений в перечислении <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="e63bf-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="e63bf-118">Значение по умолчанию — `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="e63bf-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="e63bf-119">Задает время по умолчанию, по истечении которого содержимое помечается как просроченное.</span><span class="sxs-lookup"><span data-stu-id="e63bf-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="e63bf-120">Атрибут Полицилевел</span><span class="sxs-lookup"><span data-stu-id="e63bf-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="e63bf-121">Значение</span><span class="sxs-lookup"><span data-stu-id="e63bf-121">Value</span></span>|<span data-ttu-id="e63bf-122">Описание</span><span class="sxs-lookup"><span data-stu-id="e63bf-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="e63bf-123">Возвращает кэшированный ресурс, если ресурс является актуальным, длина содержимого является точной, а атрибуты срока действия, изменения и длины содержимого существуют.</span><span class="sxs-lookup"><span data-stu-id="e63bf-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="e63bf-124">Возвращает ресурс с сервера.</span><span class="sxs-lookup"><span data-stu-id="e63bf-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="e63bf-125">Возвращает кэшированный ресурс, если длина содержимого имеется и соответствует размеру записи.</span><span class="sxs-lookup"><span data-stu-id="e63bf-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="e63bf-126">Возвращает кэшированный ресурс, если длина содержимого указана и соответствует размеру записи. в противном случае ресурс загружается с сервера и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="e63bf-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e63bf-127">Возвращает кэшированный ресурс, если метка времени кэшированного ресурса совпадает с меткой времени ресурса на сервере. в противном случае ресурс загружается с сервера, хранится в кэше, и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="e63bf-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="e63bf-128">Скачивает ресурс с сервера, сохраняет его в кэше и возвращает ресурс вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="e63bf-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="e63bf-129">Если кэшированный ресурс существует, он удаляется.</span><span class="sxs-lookup"><span data-stu-id="e63bf-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="e63bf-130">Ресурс загружается с сервера и возвращается вызывающему.</span><span class="sxs-lookup"><span data-stu-id="e63bf-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e63bf-131">Удовлетворяет запросу, используя кэшированную копию ресурса, если отметка времени совпадает с меткой времени ресурса на сервере. в противном случае ресурс загружается с сервера, представленного вызывающему объекту, и хранится в кэше.</span><span class="sxs-lookup"><span data-stu-id="e63bf-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e63bf-132">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e63bf-132">Child Elements</span></span>  
  
|<span data-ttu-id="e63bf-133">Элемент</span><span class="sxs-lookup"><span data-stu-id="e63bf-133">Element</span></span>|<span data-ttu-id="e63bf-134">Описание</span><span class="sxs-lookup"><span data-stu-id="e63bf-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e63bf-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="e63bf-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="e63bf-136">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e63bf-136">Optional element.</span></span><br /><br /> <span data-ttu-id="e63bf-137">Описывает, активно ли кэширование HTTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e63bf-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="e63bf-138">Элемент > @no__t 1defaultFtpCachePolicy (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="e63bf-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="e63bf-139">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e63bf-139">Optional element.</span></span><br /><br /> <span data-ttu-id="e63bf-140">Описывает, активно ли кэширование FTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e63bf-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e63bf-141">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e63bf-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e63bf-142">Элемент</span><span class="sxs-lookup"><span data-stu-id="e63bf-142">Element</span></span>|<span data-ttu-id="e63bf-143">Описание</span><span class="sxs-lookup"><span data-stu-id="e63bf-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e63bf-144">system.net</span><span class="sxs-lookup"><span data-stu-id="e63bf-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e63bf-145">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="e63bf-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e63bf-146">Пример</span><span class="sxs-lookup"><span data-stu-id="e63bf-146">Example</span></span>  
 <span data-ttu-id="e63bf-147">В следующем примере показано, как отключить все кэширование.</span><span class="sxs-lookup"><span data-stu-id="e63bf-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e63bf-148">См. также</span><span class="sxs-lookup"><span data-stu-id="e63bf-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="e63bf-149">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="e63bf-149">Network Settings Schema</span></span>](index.md)
