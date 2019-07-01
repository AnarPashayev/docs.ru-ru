---
title: Элемент <applicationPool> (веб-параметры)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: d6c931ec904e9a7e58d5b747c74898208863b8e9
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486724"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="d5108-102">\<пул приложений > элемент (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="d5108-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="d5108-103">Задает параметры конфигурации, которые используются платформой ASP.NET для управления поведением всего процесса, когда приложение ASP.NET выполняется в режиме интеграции с IIS 7.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="d5108-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5108-104">Этот элемент и компонент поддерживает работает только если приложения ASP.NET, размещенного на IIS 7.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="d5108-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
 <span data-ttu-id="d5108-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d5108-105">\<configuration></span></span>  
<span data-ttu-id="d5108-106">\<System.Web > элемент (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="d5108-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="d5108-107">\<пул приложений > элемент (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="d5108-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5108-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5108-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5108-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d5108-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d5108-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d5108-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5108-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d5108-111">Attributes</span></span>  
  
|<span data-ttu-id="d5108-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d5108-112">Attribute</span></span>|<span data-ttu-id="d5108-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d5108-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="d5108-114">Указывает, какое количество одновременных запросов, позволяет ASP.NET на один ЦП.</span><span class="sxs-lookup"><span data-stu-id="d5108-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="d5108-115">Указывает, сколько потоков может выполняться для пула приложений для каждого ЦП.</span><span class="sxs-lookup"><span data-stu-id="d5108-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="d5108-116">Это обеспечивает альтернативный способ управления параллелизмом ASP.NET, так как можно ограничить число управляемых потоков, которые могут использоваться для обслуживания запросов на один ЦП.</span><span class="sxs-lookup"><span data-stu-id="d5108-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="d5108-117">По умолчанию этот параметр является 0, означающее, что ASP.NET не ограничивает количество потоков, которые могут быть созданы на ЦП, несмотря на то, что пул потоков CLR также ограничивает количество потоков, которые могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="d5108-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="d5108-118">Указывает максимальное количество запросов, которые могут быть поставлены в очередь для ASP.NET в одном процессе.</span><span class="sxs-lookup"><span data-stu-id="d5108-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="d5108-119">Когда два или более приложения ASP.NET выполняются в одном пуле приложений, этот параметр относится к общему набору запросов к любому приложению в пуле приложений.</span><span class="sxs-lookup"><span data-stu-id="d5108-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5108-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d5108-120">Child Elements</span></span>  
 <span data-ttu-id="d5108-121">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d5108-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5108-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d5108-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d5108-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="d5108-123">Element</span></span>|<span data-ttu-id="d5108-124">Описание</span><span class="sxs-lookup"><span data-stu-id="d5108-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5108-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="d5108-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="d5108-126">Содержит сведения о взаимодействии ASP.NET с ведущими приложениями.</span><span class="sxs-lookup"><span data-stu-id="d5108-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5108-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="d5108-127">Remarks</span></span>  
 <span data-ttu-id="d5108-128">При запуске в режиме интеграции с IIS 7.0 или более поздней версии, это сочетание элементов позволяет настроить, как ASP.NET управляет потоков и очереди запросов, когда приложение размещается в пуле приложений IIS.</span><span class="sxs-lookup"><span data-stu-id="d5108-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="d5108-129">При использовании IIS 6 или запуск служб IIS 7.0 в классическом режиме или режиме ISAPI, эти параметры игнорируются.</span><span class="sxs-lookup"><span data-stu-id="d5108-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="d5108-130">`applicationPool` Параметры применяются для всех пулов приложений, работающих на определенной версии платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5108-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="d5108-131">Параметры содержатся в файле aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="d5108-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="d5108-132">Имеется версия этого файла для версий 2.0 и 4.0 платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5108-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="d5108-133">(Версии 3.0 и 3.5 платформы .NET Framework, передайте файл aspnet.config в версии 2.0).</span><span class="sxs-lookup"><span data-stu-id="d5108-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5108-134">При запуске IIS 7.0 на [!INCLUDE[win7](../../../../../includes/win7-md.md)], можно настроить отдельные файлы ASPNET.config для каждого пула приложений.</span><span class="sxs-lookup"><span data-stu-id="d5108-134">If you run IIS 7.0 on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="d5108-135">Это позволяет настраивать производительность потоков для каждого пула приложений.</span><span class="sxs-lookup"><span data-stu-id="d5108-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="d5108-136">Для `maxConcurrentRequestsPerCPU` параметр, значение по умолчанию «5000» в .NET Framework 4 эффективно отключает регулирование запросов, которые управляются ASP.NET, если у вас фактически нет 5000 или несколько запросов на один ЦП.</span><span class="sxs-lookup"><span data-stu-id="d5108-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="d5108-137">Значение по умолчанию вместо зависит от пула потоков CLR автоматически управлять параллелизмом для каждого ЦП.</span><span class="sxs-lookup"><span data-stu-id="d5108-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="d5108-138">Приложения, более широко использовать обработку асинхронного запроса, или в которых много долго выполняющихся запросов, заблокированных в сетевых операций ввода-вывода, смогут воспользоваться ограничение повышение по умолчанию в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d5108-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="d5108-139">Параметр `maxConcurrentRequestsPerCPU` ноль отключается использование управляемых потоков для обработки запросов ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d5108-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="d5108-140">Если приложение выполняется в пуле приложений IIS, запросы остаются в потоке ввода-вывода IIS, и таким образом, параллелизм регулируется параметрами потоков IIS.</span><span class="sxs-lookup"><span data-stu-id="d5108-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="d5108-141">`requestQueueLimit` Параметр работает так же, как `requestQueueLimit` атрибут [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) элемент, который задается в файлах Web.config для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d5108-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="d5108-142">Тем не менее `requestQueueLimit` переопределяет параметр в файле aspnet.config `requestQueueLimit` настройки в файле Web.config.</span><span class="sxs-lookup"><span data-stu-id="d5108-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="d5108-143">Другими словами Если заданы оба атрибута (по умолчанию это значение равно true), `requestQueueLimit` приоритет имеет параметр в файле aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="d5108-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5108-144">Пример</span><span class="sxs-lookup"><span data-stu-id="d5108-144">Example</span></span>  
 <span data-ttu-id="d5108-145">В следующем примере показано, как настроить поведение всего процесса ASP.NET в файле aspnet.config в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="d5108-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="d5108-146">Приложение размещается в пуле приложений IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d5108-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="d5108-147">В режиме интеграции с управлением IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d5108-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="d5108-148">Приложение использует .NET Framework 3.5 SP1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="d5108-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
 <span data-ttu-id="d5108-149">В примере значения являются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d5108-149">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="d5108-150">Сведения об элементе</span><span class="sxs-lookup"><span data-stu-id="d5108-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5108-151">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="d5108-151">Namespace</span></span>||  
|<span data-ttu-id="d5108-152">Имя схемы</span><span class="sxs-lookup"><span data-stu-id="d5108-152">Schema Name</span></span>||  
|<span data-ttu-id="d5108-153">Файл проверки</span><span class="sxs-lookup"><span data-stu-id="d5108-153">Validation File</span></span>||  
|<span data-ttu-id="d5108-154">Может быть пустым</span><span class="sxs-lookup"><span data-stu-id="d5108-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d5108-155">См. также</span><span class="sxs-lookup"><span data-stu-id="d5108-155">See also</span></span>

- [<span data-ttu-id="d5108-156">Элемент \<system.web> (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="d5108-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
