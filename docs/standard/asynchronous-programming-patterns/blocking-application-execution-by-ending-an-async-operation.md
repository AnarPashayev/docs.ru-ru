---
title: Блокировка выполнения приложения путем завершения асинхронной операции
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: 74976176acc0fbb948c514358b7bd323cc20c134
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289958"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Блокировка выполнения приложения путем завершения асинхронной операции
Приложения, которые не могут продолжать работу во время ожидания результатов асинхронной операции, должны блокироваться до завершения этой операции. Используйте один из следующих вариантов, чтобы блокировать основной поток приложения на период ожидания асинхронной операции.  
  
- Вызовите метод **End**_имя_операции_ асинхронной операции. Именно этот подход демонстрируется в этой статье.  
  
- Используйте свойство <xref:System.IAsyncResult.AsyncWaitHandle%2A> объекта <xref:System.IAsyncResult>, возвращаемого методом **Begin**_имя_операции_ асинхронной операции. Пример с демонстрацией этого подхода см. в статье [Блокирование выполнения приложения с помощью AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Приложения, использующие метод **End**_имя_операции_, чтобы блокировать выполнение до завершения асинхронной операции, обычно вызывают метод **Begin**_имя_операции_, затем выполняют все, что можно сделать без результатов этой операции и вызывают метод **End**_имя_операции_.  
  
## <a name="example"></a>Пример  
 В следующем примере кода асинхронные методы класса <xref:System.Net.Dns> используются, чтобы получить из службы доменных имен сведения об указанном пользователем компьютере. Обратите внимание, что в параметрах <xref:System.Net.Dns.BeginGetHostByName%2A>, `requestCallback` и `stateObject` передается значение `null` (`Nothing` в Visual Basic), так как при таком подходе эти аргументы не являются обязательными.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>См. также раздел

- [Асинхронная модель на основе событий (EAP)](event-based-asynchronous-pattern-eap.md)
- [Обзор асинхронной модели, основанной на событиях](event-based-asynchronous-pattern-overview.md)
