---
title: Практическое руководство. Прослушивание запросов на отмену, содержащих дескрипторы ожидания
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 74b32144a1c49fe6adfc5aa1fbdcf5dc9c8a4dd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728502"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Практическое руководство. Прослушивание запросов на отмену, содержащих дескрипторы ожидания

Если метод блокируется на время ожидания сигнала события, он не может проверить значение токена отмены и своевременно отреагировать на него. Первый пример демонстрирует, как эту проблему можно решить для таких событий, как <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, которые не реализуют поддержку унифицированной инфраструктуры отмены. Второй пример демонстрирует более простой подход с применением <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, который поддерживает унифицированную отмену.  
  
> [!NOTE]
> Если включен режим "Только мой код", Visual Studio иногда прерывает выполнение программы на строке, в которой создается исключение, и выводит сообщение об ошибке "Исключение, которое не может быть обработано пользовательским кодом". Эта ошибка не является критической. Вы можете нажать клавишу F5, чтобы продолжить выполнение программы и увидеть поведение системы при обработке этого исключения, которое продемонстрировано в примерах ниже. Чтобы выполнение программы не прерывалось после первой ошибки в Visual Studio, снимите флажок "Только мой код" в меню **Сервис > Параметры > Отладка > Общие**.  
  
## <a name="example"></a>Пример  

 Следующий пример с помощью <xref:System.Threading.ManualResetEvent> демонстрирует, как разблокировать дескрипторы ожидания, не поддерживающие унифицированную отмену.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Пример  

 Следующий пример с помощью <xref:System.Threading.ManualResetEventSlim> демонстрирует, как разблокировать примитивы координации, поддерживающие унифицированную отмену. Этот же подход можно использовать для других простых примитивов координации, таких как <xref:System.Threading.Semaphore>`Slim` и <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>См. также раздел

- [Отмена в управляемых потоках](cancellation-in-managed-threads.md)
