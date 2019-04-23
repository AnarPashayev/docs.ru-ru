---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 562399c1d45dc73c7c88bd165e9f95ee1bcfa19d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125086"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Подозрительное сообщение отклонено.  
  
## <a name="description"></a>Описание  
 Указывает, что было обнаружено и отклонено подозрительное сообщение. Возникает, если свойство `ReceiveErrorHandling` объекта NetMsmqBinding или MsmqIntegrationBinding имеет значение `Reject`. Отклоненное сообщение доставляется отправителя [очередь недоставленных сообщений](https://go.microsoft.com/fwlink/?LinkId=99544).  
  
 См. в разделе [обработка подозрительных сообщений](https://go.microsoft.com/fwlink/?LinkId=99546) узнать больше о при сообщения становятся подозрительными и как настроить службу для их правильной обработки. См. в разделе [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) Дополнительные сведения о значении отклоненных сообщений в MSMQ.  
  
## <a name="see-also"></a>См. также

- [Трассировка](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Использование трассировки для устранения неполадок приложения](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Администрирование и диагностика](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Обработка подозрительных сообщений](https://go.microsoft.com/fwlink/?LinkId=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)
