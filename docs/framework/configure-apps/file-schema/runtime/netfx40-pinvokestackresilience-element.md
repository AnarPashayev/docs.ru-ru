---
title: Элемент <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60fcdd902c6acf919e68806ff65e3b8142533280
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456382"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="48e17-102">\<NetFx40_PInvokeStackResilience > элемент</span><span class="sxs-lookup"><span data-stu-id="48e17-102">\<NetFx40_PInvokeStackResilience> Element</span></span>
<span data-ttu-id="48e17-103">Указывает, исправляет ли автоматически среда выполнения неправильные объявления вызова неуправляемого кода во время выполнения за счет скорости перехода между управляемыми и неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="48e17-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="48e17-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="48e17-104">\<configuration></span></span>  
<span data-ttu-id="48e17-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="48e17-105">\<runtime></span></span>  
<span data-ttu-id="48e17-106">< NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="48e17-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e17-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48e17-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48e17-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="48e17-108">Attributes and Elements</span></span>  
 <span data-ttu-id="48e17-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="48e17-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48e17-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="48e17-110">Attributes</span></span>  
  
|<span data-ttu-id="48e17-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="48e17-111">Attribute</span></span>|<span data-ttu-id="48e17-112">Описание</span><span class="sxs-lookup"><span data-stu-id="48e17-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="48e17-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="48e17-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="48e17-114">Указывает ли среда выполнения обнаруживает неверные объявления вызова неуправляемого кода и автоматически исправляет стека во время выполнения на 32-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="48e17-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="48e17-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="48e17-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="48e17-116">Значение</span><span class="sxs-lookup"><span data-stu-id="48e17-116">Value</span></span>|<span data-ttu-id="48e17-117">Описание</span><span class="sxs-lookup"><span data-stu-id="48e17-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="48e17-118">Среда выполнения использует быстрее маршалинга архитектуры, представленные в [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], который не удается обнаружить и исправить неправильные объявления вызова неуправляемого.</span><span class="sxs-lookup"><span data-stu-id="48e17-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="48e17-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="48e17-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="48e17-120">Среда выполнения использует медленнее переходы, которые обнаружить и исправить неверные объявления вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="48e17-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48e17-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="48e17-121">Child Elements</span></span>  
 <span data-ttu-id="48e17-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="48e17-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48e17-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="48e17-123">Parent Elements</span></span>  
  
|<span data-ttu-id="48e17-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="48e17-124">Element</span></span>|<span data-ttu-id="48e17-125">Описание</span><span class="sxs-lookup"><span data-stu-id="48e17-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48e17-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48e17-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="48e17-127">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="48e17-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e17-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="48e17-128">Remarks</span></span>  
 <span data-ttu-id="48e17-129">Этот элемент позволяет быстрее реализовывать маршалинг взаимодействия для вызова неуправляемого кода во время выполнения устойчивость к неверным.</span><span class="sxs-lookup"><span data-stu-id="48e17-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="48e17-130">Начиная с .NET Framework 4, архитектура упрощенного маршалинга взаимодействия обеспечивает значительное улучшение производительности для переходов из управляемого кода в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="48e17-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="48e17-131">В более ранних версиях платформы .NET Framework маршалинга обнаруживал неверные платформы неуправляемого кода на 32-разрядных платформах и автоматически исправлял стек.</span><span class="sxs-lookup"><span data-stu-id="48e17-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="48e17-132">Новая архитектура маршалинга устраняет этот шаг.</span><span class="sxs-lookup"><span data-stu-id="48e17-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="48e17-133">В результате переходы выполняются очень быстро, но неправильные объявления вызова неуправляемого может привести к сбою программы.</span><span class="sxs-lookup"><span data-stu-id="48e17-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="48e17-134">Для упрощения обнаружения неправильные объявления во время разработки были улучшены функции отладки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="48e17-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="48e17-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) помощник по отладке управляемого (кода MDA) уведомляет о неправильном объявления вызова неуправляемого кода при запуске приложения с подключенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="48e17-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="48e17-136">Для сценариев, где приложение использует компоненты, что невозможно перекомпилировать и что имеют неправильные объявления вызова неуправляемого, можно использовать `NetFx40_PInvokeStackResilience` элемент.</span><span class="sxs-lookup"><span data-stu-id="48e17-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="48e17-137">Добавление этого элемента в файле конфигурации приложения с `enabled="1"` переводит в режим совместимости с поведением более ранних версий платформы .NET Framework, за счет скорости перехода.</span><span class="sxs-lookup"><span data-stu-id="48e17-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="48e17-138">Сборки, которые были скомпилированы для более ранних версий платформы .NET Framework, автоматически переводятся в этот режим совместимости и этот элемент не обязательно.</span><span class="sxs-lookup"><span data-stu-id="48e17-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="48e17-139">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="48e17-139">Configuration File</span></span>  
 <span data-ttu-id="48e17-140">Этот элемент может использоваться только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="48e17-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e17-141">Пример</span><span class="sxs-lookup"><span data-stu-id="48e17-141">Example</span></span>  
 <span data-ttu-id="48e17-142">В следующем примере показан способ, чтобы обеспечить дополнительную устойчивость к неправильным объявлению вызовов неуправляемого приложения, за счет скорости перехода между управляемого и неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="48e17-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48e17-143">См. также</span><span class="sxs-lookup"><span data-stu-id="48e17-143">See also</span></span>

- [<span data-ttu-id="48e17-144">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="48e17-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="48e17-145">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="48e17-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="48e17-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="48e17-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
