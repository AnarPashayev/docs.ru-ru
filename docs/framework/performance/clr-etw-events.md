---
title: События трассировки событий Windows в среде CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135867"
---
# <a name="clr-etw-events"></a>События трассировки событий Windows в среде CLR
В этом разделе описываются события трассировки событий Windows (ETW). С каждым событием связаны ключевое слово и уровень, которые описываются в разделе [Ключевые слова и уровни среды CLR (трассировка событий Windows)](../../../docs/framework/performance/clr-etw-keywords-and-levels.md). В среде CLR предусмотрены два поставщика событий:  
  
-   Поставщик среды выполнения вызывает события в зависимости от того, какие ключевые слова (категории событий) активированы. Поставщик среды выполнения CLR имеет GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   Поставщик очистки используется в особых случаях. Поставщик очистки среды CLR имеет GUID a669021c-c450-4609-a035-5af59af4df18.  
  
 Дополнительные сведения см. в разделе [Поставщики трассировки событий Windows в среде CLR](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [События сведений времени выполнения](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Захватывают информацию о среде выполнения, включая SKU, номер версии, способ активизации среды выполнения, параметры командной строки при ее запуске, GUID (если применимо) и другие релевантные данные.  
  
 [Событие ExceptionThrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Захватывает информацию о сгенерированных исключениях.  
  
 [События конфликтов](../../../docs/framework/performance/contention-etw-events.md)  
 Захватывают информацию о конкуренции за блокировки мониторинга или неуправляемые блокировки, используемые исполняющей средой.  
  
 [События пула потоков](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Захватывают информацию о пулах рабочих потоков и пулах потоков ввода-вывода.  
  
 [События загрузчика](../../../docs/framework/performance/loader-etw-events.md)  
 Захватывают информацию о загрузке и выгрузке доменов приложения, сборок и модулей.  
  
 [События методов](../../../docs/framework/performance/method-etw-events.md)  
 Захватывают информацию о методах среды CLR для разрешения символов.  
  
 [События сборки мусора](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Захватывают сведения, относящиеся к сборке мусора, в целях диагностики и отладки.  
  
 [События трассировки JIT-компилятора](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Захватывают информацию о JIT-подстановке (inlining) и концевых вызовах (tail calls).  
  
 [События взаимодействия](../../../docs/framework/performance/interop-etw-events.md)  
 Захватывают информацию о генерации и кэшировании заглушек MSIL.  
  
 [События ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Захватывают детализированную диагностическую информацию о состоянии домена приложения.  
  
 [События безопасности](../../../docs/framework/performance/security-etw-events.md)  
 Захватывают информацию о строгом имени и проверке Authenticode.  
  
 [События стека](../../../docs/framework/performance/stack-etw-event.md)  
 Захватывают информацию, которая используется совместно с другими событиями для генерации трассировок стека после возникновения какого-либо события.  
  
## <a name="see-also"></a>См. также

- [Улучшение отладки и настройки производительности с помощью ETW](https://go.microsoft.com/fwlink/?LinkId=179696)
- [Блог, посвященный производительности Windows](https://go.microsoft.com/fwlink/?LinkId=179509)
- [Контроль ведения журнала .NET Framework](../../../docs/framework/performance/controlling-logging.md)
- [Поставщики трассировки событий Windows в среде CLR](../../../docs/framework/performance/clr-etw-providers.md)
- [Ключевые слова и уровни среды CLR (трассировка событий Windows)](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [События в среде CLR (трассировка событий Windows)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
