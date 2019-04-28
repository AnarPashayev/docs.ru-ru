---
title: Элемент <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec411039363cfb118fee06dff88daf50bbc97a86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704938"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="bb474-102">\<alwaysFlowImpersonationPolicy > элемента</span><span class="sxs-lookup"><span data-stu-id="bb474-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="bb474-103">Указывает, что удостоверение Windows всегда проходит через асинхронные точки, независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="bb474-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="bb474-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bb474-104">\<configuration></span></span>  
<span data-ttu-id="bb474-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="bb474-105">\<runtime></span></span>  
<span data-ttu-id="bb474-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="bb474-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb474-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb474-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb474-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bb474-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bb474-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bb474-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb474-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bb474-110">Attributes</span></span>  
  
|<span data-ttu-id="bb474-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bb474-111">Attribute</span></span>|<span data-ttu-id="bb474-112">Описание</span><span class="sxs-lookup"><span data-stu-id="bb474-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bb474-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="bb474-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb474-114">Указывает, является ли удостоверение Windows проходит через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="bb474-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bb474-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="bb474-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bb474-116">Значение</span><span class="sxs-lookup"><span data-stu-id="bb474-116">Value</span></span>|<span data-ttu-id="bb474-117">Описание</span><span class="sxs-lookup"><span data-stu-id="bb474-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bb474-118">Windows, удостоверение не проходит через асинхронные точки, если олицетворение осуществляется с помощью управляемых методов, таких как <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb474-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="bb474-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bb474-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bb474-120">Удостоверение Windows всегда проходит через асинхронные точки, независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="bb474-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb474-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bb474-121">Child Elements</span></span>  
 <span data-ttu-id="bb474-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="bb474-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb474-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bb474-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb474-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="bb474-124">Element</span></span>|<span data-ttu-id="bb474-125">Описание</span><span class="sxs-lookup"><span data-stu-id="bb474-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb474-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb474-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bb474-127">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="bb474-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb474-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="bb474-128">Remarks</span></span>  
 <span data-ttu-id="bb474-129">В .NET Framework версий 1.0 и 1.1 удостоверение Windows не проходит через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="bb474-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="bb474-130">В платформе .NET Framework версии 2.0 есть <xref:System.Threading.ExecutionContext> объект, который содержит сведения о текущем потоке и он проходит через асинхронные точки в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="bb474-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="bb474-131"><xref:System.Security.Principal.WindowsIdentity> Также потоки как часть сведений, который проходит через асинхронные точки, если было выполнено олицетворение с помощью управляемых методов, таких как <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> и не с помощью других средств, таких как платформа вызова методам.</span><span class="sxs-lookup"><span data-stu-id="bb474-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="bb474-132">Этот элемент используется для указания, что удостоверение Windows проходит через асинхронные точки, независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="bb474-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="bb474-133">Можно изменить это поведение по умолчанию двумя способами:</span><span class="sxs-lookup"><span data-stu-id="bb474-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="bb474-134">В управляемом коде для каждого потока.</span><span class="sxs-lookup"><span data-stu-id="bb474-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="bb474-135">Поток для каждого потока можно отключить, изменив <xref:System.Threading.ExecutionContext> и <xref:System.Security.SecurityContext> параметры с помощью <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, или <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="bb474-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="bb474-136">В вызове неуправляемого интерфейса размещения для загрузки общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="bb474-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="bb474-137">Если неуправляемый интерфейс размещения (вместо простой управляемый исполняемый файл) используется для загрузки среды CLR, можно указать специальный флаг в вызове [функция CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="bb474-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="bb474-138">Чтобы включить режим совместимости для всего процесса, задайте `flags` параметр для [функция CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) для `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="bb474-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bb474-139">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="bb474-139">Configuration File</span></span>  
 <span data-ttu-id="bb474-140">В приложении .NET Framework этот элемент может использоваться только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="bb474-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="bb474-141">Для приложения ASP.NET поток олицетворения можно настроить в файле aspnet.config в \<папка Windows > \Microsoft.NET\Framework\vx.x.xxxx каталога.</span><span class="sxs-lookup"><span data-stu-id="bb474-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="bb474-142">ASP.NET по умолчанию отключает поток олицетворения в файле aspnet.config, используя следующие параметры конфигурации:</span><span class="sxs-lookup"><span data-stu-id="bb474-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="bb474-143">В ASP.NET Если вы хотите разрешить поток олицетворения, вместо этого необходимо явно использовать следующие параметры конфигурации:</span><span class="sxs-lookup"><span data-stu-id="bb474-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="bb474-144">Пример</span><span class="sxs-lookup"><span data-stu-id="bb474-144">Example</span></span>  
 <span data-ttu-id="bb474-145">Приведенный ниже показано, как указать, что удостоверение Windows проходит через асинхронные точки, даже в том случае, если олицетворение достигается с помощью средств, отличных от управляемых методов.</span><span class="sxs-lookup"><span data-stu-id="bb474-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb474-146">См. также</span><span class="sxs-lookup"><span data-stu-id="bb474-146">See also</span></span>

- [<span data-ttu-id="bb474-147">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="bb474-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="bb474-148">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="bb474-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="bb474-149">\<legacyImpersonationPolicy > элемент</span><span class="sxs-lookup"><span data-stu-id="bb474-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
