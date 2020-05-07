---
title: Библиотека параллельных задач (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 74a6fc20e95e11bfdbec617742f304a940f3e769
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507563"
---
# <a name="task-parallel-library-tpl"></a>Библиотека параллельных задач (TPL)
Библиотека параллельных задач (TPL) представляет собой набор открытых типов и API-интерфейсов в пространствах имен <xref:System.Threading?displayProperty=nameWithType> и <xref:System.Threading.Tasks?displayProperty=nameWithType>. Цель TPL — повышение производительности труда разработчиков за счет упрощения процедуры добавления параллелизма в приложения. TPL динамически масштабирует степень параллелизма для наиболее эффективного использования всех доступных процессоров. Кроме того, в библиотеке параллельных задач осуществляется секционирование работы, планирование потоков в пуле <xref:System.Threading.ThreadPool>, поддержка отмены, управление состоянием и выполняются другие низкоуровневые задачи. Используя библиотеку параллельных задач, можно повысить производительность кода, сосредоточившись на работе, для которой предназначена программа.  
  
 Начиная с .NET Framework 4 библиотека параллельных задач представляет предпочтительный способ создания многопоточного и параллельного кода. Однако не всякий код подходит для параллелизации; например, если цикл за каждую итерацию выполняет небольшой объем работ или выполняется для небольшого числа итераций, из-за дополнительной нагрузки, которую параллелизация оказывает на систему, код может выполняться медленнее. Кроме того, параллелизация, как и любой многопоточный код, усложняет выполнение программы. Хотя библиотека параллельных задач упрощает многопоточные сценарии, рекомендуется иметь базовое понимание понятий потоков, например блокировки, взаимоблокировки и состояния гонки, чтобы эффективно использовать библиотеку параллельных задач.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-|-|  
|[Параллелизм данных](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Описание создания параллельных циклов `for` и `foreach` (`For` и `For Each` в Visual Basic).|  
|[Асинхронное программирование на основе задач](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Описание создания и запуска задач неявно с использованием перегрузки <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> или явно с использованием объектов <xref:System.Threading.Tasks.Task> напрямую.|  
|[Поток данных](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Описание использования компонентов потоков данных в библиотеке потоков данных TPL для обработки нескольких операций, которые должны взаимодействовать друг с другом, или для обработки данных, когда они становятся доступными.|  
|[Использование библиотеки параллельных задач с другими асинхронными моделями](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Описание использования библиотеки параллельных задач с другими асинхронными шаблонами в .NET.|  
|[Возможные ошибки, связанные с параллелизмом данных и задач](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Описание некоторых распространенных ошибок и способов их избежать.|  
|[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)|Описание способов достижения параллелизма данных с помощью запросов LINQ.|  
|[Параллельное программирование](../../../docs/standard/parallel-programming/index.md)|Узел верхнего уровня для параллельного программирования в .NET.|  
  
## <a name="see-also"></a>См. также

- [Примеры параллельного программирования в .NET Core и .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
