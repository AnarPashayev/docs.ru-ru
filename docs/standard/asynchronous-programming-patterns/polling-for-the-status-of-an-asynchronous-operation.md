---
title: Запрос состояния асинхронной операции
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: c4e8e7c66551e0a240eaa873513c3975703af946
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830315"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Запрос состояния асинхронной операции
Приложения, которые могут выполнять работу во время ожидания результатов асинхронной операции, не должны блокироваться до завершения этой операции. Используйте один из следующих вариантов, чтобы продолжить выполнение инструкций в период ожидания асинхронной операции.  
  
- Чтобы определить, завершена ли операция, используется свойство <xref:System.IAsyncResult.IsCompleted%2A> объекта <xref:System.IAsyncResult>, возвращаемого методом **Begin**_имя_операции_ асинхронной операции. Именно этот подход, именуемый стратегией опросов, демонстрируется в этой статье.  
  
- Используйте делегат <xref:System.AsyncCallback> для обработки результатов асинхронной операции в отдельном потоке. Пример, демонстрирующий этот подход, см. в разделе [Использование делегата AsyncCallback для завершения асинхронной операции](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода асинхронные методы класса <xref:System.Net.Dns> используются, чтобы получить из службы доменных имен сведения об указанном пользователем компьютере. Код примера запускает асинхронную операцию, а затем выводит в консоль точки (".") до завершения операции. Обратите внимание, что в параметрах <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> и <xref:System.Object> передается значение **NULL** (**Nothing** в Visual Basic), так как при таком подходе эти аргументы не являются обязательными.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>См. также

- [Асинхронная модель на основе событий (EAP)](event-based-asynchronous-pattern-eap.md)
- [Обзор асинхронной модели, основанной на событиях](event-based-asynchronous-pattern-overview.md)
