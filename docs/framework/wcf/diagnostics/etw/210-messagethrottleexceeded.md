---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: a0da1c198700407d8cdf699d1b734247024717a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267745"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded

## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|ID|210|  
|Keywords|EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel|  
|Level|Предупреждение|  
|Канал|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Описание  

 Это событие создается при превышении одного из трех основных пределов регулирования службы. Обратите внимание, что это событие создается только в том случае, если предел регулирования превышен уже в исходной конфигурации. Например, если предел регулирования на число одновременных вызовов составляет 10, то при выполнении одиннадцатого вызова будет вызвано событие `MessageThrottleExceeded`. Выполнение двенадцатого вызова не приведет к созданию еще одного события. Если в рамках действия контролируемое значение незначительно изменилось в области предела регулирования, то новые сообщения не вызываются, что позволяет избежать формирования потока ложных сообщений. В этом примере завершение нескольких вызовов указывает на наличие 9 одновременных вызовов. Если последовательно получено еще два входящих вызова, то текущее значение снова будет равно 11. При этом еще одно событие вызвано не будет. Если текущее значение составляет 70 процентов от предела регулирования, то вызывается другое событие, указывающее на замедление выполнения действия. При выполнении последующих действий, которые приводят к превышению ограничения, вызывается другое событие `MessageThrottleExceeded`. В этом примере, если количество одновременных вызовов в определенный момент времени составляло 7, а затем достигло 11, вызывается еще одно событие `MessageThrottleExceeded`.  
  
## <a name="message"></a>Сообщение  

 Был достигнут предел ограничителя «%1» из «%2».  
  
## <a name="details"></a>Сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|Throttle Name|`xs:string`|Имя превышенного ограничителя. `MaxConcurrentCalls`, `MaxConcurrentInstances` либо `MaxConcurrentSessions`,|  
|Ограничение|`xs:long`|Заданный в данный момент предел ограничителя.|  
|HostReference|`xs:string`|Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии. Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName". Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".|  
|Домен приложения|`xs:string`|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
