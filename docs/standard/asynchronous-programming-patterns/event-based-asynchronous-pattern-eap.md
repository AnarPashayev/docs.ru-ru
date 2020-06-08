---
title: Асинхронная модель на основе событий (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 604e7a944579a284004817009b06c11b268d5daf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289438"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Асинхронная модель на основе событий (EAP)

Существует несколько способов предоставить асинхронные возможности клиентскому коду. Асинхронная модель на основе событий задает для классов рекомендуемый способ работы в асинхронном режиме.  
  
> [!NOTE]
> Начиная с версии .NET Framework 4 библиотека параллельных задач предоставляет новую модель для асинхронного и параллельного программирования. Дополнительные сведения см. в разделах [Библиотека параллельных задач (TPL)](../parallel-programming/task-parallel-library-tpl.md) и [Асинхронная модель на основе задач (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>Содержание

 [Обзор асинхронной модели, основанной на событиях](event-based-asynchronous-pattern-overview.md)  
 Описывает, как асинхронная модель на основе событий позволяет использовать преимущества многопоточных приложений и устраняет многие сложности, присущие многопоточности.  
  
 [Реализация асинхронной модели, основанной на событиях](implementing-the-event-based-asynchronous-pattern.md)  
 Описывает стандартизированный способ упаковки класса, имеющего асинхронные возможности.  
  
 [Рекомендации по реализации асинхронной модели, основанной на событиях](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Описывает требования для предоставления асинхронных возможностей в соответствии с асинхронной моделью на основе событий.  
  
 [Определение, когда следует реализовать асинхронную модель, основанную на событиях](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Описывает, в каких случаях следует реализовать асинхронную модель на основе событий вместо шаблона <xref:System.IAsyncResult>, представленного [асинхронной моделью программирования (APM)](asynchronous-programming-model-apm.md)
  
 [Практическое руководство. Реализация компонента, поддерживающего асинхронную модель на основе событий](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Описывает, как создать компонент, реализующий асинхронную модель на основе событий. Она реализуется с использованием вспомогательных классов из пространства имен <xref:System.ComponentModel?displayProperty=nameWithType>, что обеспечивает правильную работу компонента при любой модели приложения.  

 [Практическое руководство. Реализация клиента асинхронной модели на основе событий](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Описывает, как создать клиент, который использует компонент, реализующий асинхронную модель на основе событий.
  
 [Практическое руководство. Использование компонентов, поддерживающих асинхронную модель, основанную на событиях](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Описывает использование компонента, поддерживающего асинхронную модель на основе событий.  
  
## <a name="reference"></a>Справочник

 <xref:System.ComponentModel.AsyncOperation>  
 Описывает класс <xref:System.ComponentModel.AsyncOperation> и содержит ссылки на все его члены.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Описывает класс <xref:System.ComponentModel.AsyncOperationManager> и содержит ссылки на все его члены.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Описывает компонент <xref:System.ComponentModel.BackgroundWorker> и содержит ссылки на все его члены.  
  
## <a name="related-sections"></a>Связанные разделы

 [Библиотека параллельных задач (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Описание модели программирования для асинхронных и параллельных операций.  
  
 [Работа с потоками](../threading/index.md)  
 Описывает многопоточные функциональные возможности в .NET.  
  
## <a name="see-also"></a>См. также раздел

- [Рекомендации по работе с потоками](../threading/managed-threading-best-practices.md)
- [События](../events/index.md)
- [Шаблоны асинхронного программирования](index.md)
