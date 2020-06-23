---
title: Рекомендуемые параметры для трассировки и ведения журналов сообщений
description: Сведения о рекомендуемых параметрах трассировки и ведения журнала сообщений для различных операционных сред в WCF.
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 71067a4d6f4cec65a148a8162c40e44d82b85784
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245333"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Рекомендуемые параметры для трассировки и ведения журналов сообщений
Этот раздел содержит описание рекомендуемых параметров трассировки и регистрации сообщений для различных операционных сред.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Параметры, рекомендуемые для рабочей среды  
 В рабочей среде, если используются источники трассировки WCF, рекомендуется в `switchValue` задать значение Warning. При использовании источника трассировки WCF `System.ServiceModel` рекомендуется задать в атрибуте `switchValue` значение `Warning`, а в атрибуте `propagateActivity` - значение `true`. При использовании источника трассировки, определенного пользователем, рекомендуется присвоить атрибуту `switchValue` значение `Warning, ActivityTracing`. Это можно сделать вручную с помощью [средства редактора конфигурации (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md). Если в работе не ожидается резкого подъема производительности, во всех перечисленных выше случаях атрибуту `switchValue` можно присвоить значение `Information`, при котором генерируется достаточно большое количество данных трассировки. Следующий пример иллюстрирует задание описанных рекомендуемых параметров.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Параметры, рекомендуемые для развертывания или отладки  
 При работе в среде развертывания или отладки рекомендуется выбирать значения `Information` или `Verbose` наряду с `ActivityTracing` как для определенных пользователем, так и для заданных `System.ServiceModel` источников трассировки. Чтобы улучшить процесс отладки, к конфигурации необходимо добавить дополнительный источник трассировки (`System.ServiceModel.MessageLogging`) для активации функции регистрации сообщений. Обратите внимание, что атрибут `switchValue` не влияет на этот источник трассировки.  
  
 Следующий пример иллюстрирует задание рекомендуемых параметров с помощью общего прослушивателя, использующего `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Изменение параметров с помощью инструментария WMI  
 Для изменения параметров конфигурации во время работы можно использовать инструментарий WMI (выполняется путем включения атрибута `wmiProviderEnabled` в конфигурации, как показано в предыдущем примере конфигурации). Например, для изменения во время работы уровней источника трассировки с Warning на Information можно использовать инструментарий WMI в CIM Studio. Следует помнить о том, что такой способ отладки может значительно снизить производительность. Дополнительные сведения об использовании инструментария WMI см. в разделе [использование инструментарий управления Windows (WMI) для диагностики](../wmi/index.md) .  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Использование корреляции событий в трассировке ASP.NET  
 События ASP.NET не получают корреляционный идентификатор (ActivityID), если не включена функция трассировки событий ASP.NET. Чтобы правильно просмотреть коррелированные события, необходимо включить трассировку событий ASP.NET с помощью следующей команды в командной консоли, которую можно вызвать, выполнив команду **Пуск**, **запустите** и введите **команду cmd**.  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Для отключения трассировки событий ASP.NET используйте следующую команду.  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>См. также

- [Использование инструментарий управления Windows (WMI) для диагностики](../wmi/index.md)
