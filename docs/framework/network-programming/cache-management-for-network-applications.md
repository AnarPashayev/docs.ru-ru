---
title: Управление кэшем для сетевых приложений
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048872"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="8ba39-102">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="8ba39-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="8ba39-103">В этом разделе и его подразделах описывается кэширование ресурсов, полученных с помощью классов <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> и <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="8ba39-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="8ba39-104">Кэш обеспечивает временное хранение ресурсов, которые были запрошены приложением.</span><span class="sxs-lookup"><span data-stu-id="8ba39-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="8ba39-105">Если приложение запрашивает один и тот же ресурс несколько раз, он может быть возвращен из кэша. Это позволяет избежать лишнего расходования ресурсов, связанного с его повторным запросом с сервера.</span><span class="sxs-lookup"><span data-stu-id="8ba39-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="8ba39-106">Кэширование может повысить производительность приложения, ускоряя получение запрашиваемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8ba39-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="8ba39-107">Оно также может помочь уменьшить объем сетевого трафика, сокращая число обращений к серверу.</span><span class="sxs-lookup"><span data-stu-id="8ba39-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="8ba39-108">Хотя кэширование повышает производительность, также растет риск того, что возвращаемый приложению ресурс может оказаться устаревшим, то есть отличающимся от того ресурса, который был бы отправлен с сервера при отсутствии кэширования.</span><span class="sxs-lookup"><span data-stu-id="8ba39-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="8ba39-109">Из-за кэширования также возможен несанкционированный доступ к конфиденциальным данным со стороны пользователей или процессов.</span><span class="sxs-lookup"><span data-stu-id="8ba39-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="8ba39-110">Прошедший проверку подлинности ответ может быть получен из кэша без дополнительной авторизации.</span><span class="sxs-lookup"><span data-stu-id="8ba39-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="8ba39-111">Если кэширование включено, измените значение <xref:System.Net.WebRequest.CachePolicy%2A> на <xref:System.Net.Cache.RequestCacheLevel.BypassCache> или <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore>, чтобы отключить кэширование для запроса.</span><span class="sxs-lookup"><span data-stu-id="8ba39-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="8ba39-112">По соображениям безопасности кэширование **не** рекомендуется использовать в сценариях среднего уровня.</span><span class="sxs-lookup"><span data-stu-id="8ba39-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ba39-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="8ba39-113">In This Section</span></span>  
 [<span data-ttu-id="8ba39-114">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="8ba39-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="8ba39-115">Описывается, что такое политика кэша и как ее определить.</span><span class="sxs-lookup"><span data-stu-id="8ba39-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="8ba39-116">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="8ba39-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="8ba39-117">Описание каждого типа политики кэша на основе расположения для ресурсов HTTP и HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8ba39-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="8ba39-118">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="8ba39-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="8ba39-119">Описание условий, которые можно использовать для настройки политики кэша на основе времени.</span><span class="sxs-lookup"><span data-stu-id="8ba39-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="8ba39-120">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="8ba39-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="8ba39-121">Описываются программные способы создания политик кэша и запросов, для которых применяется кэширование.</span><span class="sxs-lookup"><span data-stu-id="8ba39-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8ba39-122">Справочник</span><span class="sxs-lookup"><span data-stu-id="8ba39-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="8ba39-123">Определение типов и перечислений, используемых для определения политик кэширования ресурсов, получаемых с помощью классов <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> и <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="8ba39-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
