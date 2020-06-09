---
title: Рекомендуемые параметры для трассировки и ведения журналов сообщений
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 9d2586570a3f590735c2a8e1ca176580886c8d92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578920"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="9e5cc-102">Рекомендуемые параметры для трассировки и ведения журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="9e5cc-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="9e5cc-103">Этот раздел содержит описание рекомендуемых параметров трассировки и регистрации сообщений для различных операционных сред.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="9e5cc-104">Параметры, рекомендуемые для рабочей среды</span><span class="sxs-lookup"><span data-stu-id="9e5cc-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="9e5cc-105">В рабочей среде, если используются источники трассировки WCF, рекомендуется в `switchValue` задать значение Warning.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="9e5cc-106">При использовании источника трассировки WCF `System.ServiceModel` рекомендуется задать в атрибуте `switchValue` значение `Warning`, а в атрибуте `propagateActivity` - значение `true`.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="9e5cc-107">При использовании источника трассировки, определенного пользователем, рекомендуется присвоить атрибуту `switchValue` значение `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="9e5cc-108">Это можно сделать вручную с помощью [средства редактора конфигурации (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9e5cc-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="9e5cc-109">Если в работе не ожидается резкого подъема производительности, во всех перечисленных выше случаях атрибуту `switchValue` можно присвоить значение `Information`, при котором генерируется достаточно большое количество данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="9e5cc-110">Следующий пример иллюстрирует задание описанных рекомендуемых параметров.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-110">The following example demonstrates these recommended settings.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="9e5cc-111">Параметры, рекомендуемые для развертывания или отладки</span><span class="sxs-lookup"><span data-stu-id="9e5cc-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="9e5cc-112">При работе в среде развертывания или отладки рекомендуется выбирать значения `Information` или `Verbose` наряду с `ActivityTracing` как для определенных пользователем, так и для заданных `System.ServiceModel` источников трассировки.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="9e5cc-113">Чтобы улучшить процесс отладки, к конфигурации необходимо добавить дополнительный источник трассировки (`System.ServiceModel.MessageLogging`) для активации функции регистрации сообщений.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="9e5cc-114">Обратите внимание, что атрибут `switchValue` не влияет на этот источник трассировки.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="9e5cc-115">Следующий пример иллюстрирует задание рекомендуемых параметров с помощью общего прослушивателя, использующего `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging
           logEntireMessage="true"
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="9e5cc-116">Изменение параметров с помощью инструментария WMI</span><span class="sxs-lookup"><span data-stu-id="9e5cc-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="9e5cc-117">Для изменения параметров конфигурации во время работы можно использовать инструментарий WMI (выполняется путем включения атрибута `wmiProviderEnabled` в конфигурации, как показано в предыдущем примере конфигурации).</span><span class="sxs-lookup"><span data-stu-id="9e5cc-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="9e5cc-118">Например, для изменения во время работы уровней источника трассировки с Warning на Information можно использовать инструментарий WMI в CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="9e5cc-119">Следует помнить о том, что такой способ отладки может значительно снизить производительность.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="9e5cc-120">Дополнительные сведения об использовании инструментария WMI см. в разделе [использование инструментарий управления Windows (WMI) для диагностики](../wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="9e5cc-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="9e5cc-121">Использование корреляции событий в трассировке ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9e5cc-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="9e5cc-122">События ASP.NET не получают корреляционный идентификатор (ActivityID), если не включена функция трассировки событий ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="9e5cc-123">Чтобы правильно просмотреть коррелированные события, необходимо включить трассировку событий ASP.NET с помощью следующей команды в командной консоли, которую можно вызвать, выполнив команду **Пуск**, **запустите** и введите **команду cmd**.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="9e5cc-124">Для отключения трассировки событий ASP.NET используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="9e5cc-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e5cc-125">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="9e5cc-125">See also</span></span>

- [<span data-ttu-id="9e5cc-126">Использование инструментарий управления Windows (WMI) для диагностики</span><span class="sxs-lookup"><span data-stu-id="9e5cc-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
