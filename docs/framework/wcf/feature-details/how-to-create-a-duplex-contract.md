---
title: Практическое руководство. Создание двухстороннего контракта
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598987"
---
# <a name="how-to-create-a-duplex-contract"></a>Практическое руководство. Создание двухстороннего контракта
В этом разделе приведены основные этапы создания методов, использующих дуплексные (двухсторонние) контракты. Дуплексный контракт позволяет клиентам и серверам взаимодействовать друг с другом независимо (клиент может инициировать вызовы сервера, а сервер - вызовы клиента). Дуплексный контракт — это один из трех шаблонов сообщений, доступных для служб Windows Communication Foundation (WCF). Две другие схемы обмена сообщениями - это односторонний обмен и запрос-ответ. Дуплексный контракт состоит из двух односторонних контрактов между клиентом и сервером, при этом не требуется корреляция между вызовами методов. Контракт этого типа следует использовать, если служба должна запрашивать у клиента дополнительную информацию или в явном виде создавать события в клиенте. Дополнительные сведения о создании клиентского приложения для дуплексного контракта см. в разделе [руководство. доступ к службам с помощью дуплексного контракта](how-to-access-services-with-a-duplex-contract.md). Рабочий пример см. в разделе [дуплексный](../samples/duplex.md) пример.  
  
### <a name="to-create-a-duplex-contract"></a>Создание двухстороннего контракта  
  
1. Создайте интерфейс, образующий серверную часть дуплексного контракта.  
  
2. Примените класс <xref:System.ServiceModel.ServiceContractAttribute> к интерфейсу.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Объявите в интерфейсе подписи методов.  
  
4. Примените класс <xref:System.ServiceModel.OperationContractAttribute> к каждой подписи метода, которая должна входить в открытый контракт.  
  
5. Создайте интерфейс обратного вызова, определяющий набор операций, которые служба может вызывать в клиенте.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Объявите подписи методов в интерфейсе обратного вызова.  
  
7. Примените класс <xref:System.ServiceModel.OperationContractAttribute> к каждой подписи метода, которая должна входить в открытый контракт.  
  
8. Объедините эти два интерфейса в дуплексный контракт, задав для свойства <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> в основном интерфейсе тип интерфейса обратного вызова.  
  
### <a name="to-call-methods-on-the-client"></a>Вызов методов в клиенте  
  
1. В реализации основного контракта на стороне службы объявите переменную для интерфейса обратного вызова.  
  
2. Присвойте переменной ссылку на объект, возвращаемый методом <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> класса <xref:System.ServiceModel.OperationContext>.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Вызовите методы, определенные в интерфейсе обратного вызова.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется дуплексное взаимодействие. Контракт службы содержит операции службы для перемещения вперед или назад. Контракт клиента содержит операцию службы для сообщения о положении.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- Применение атрибутов <xref:System.ServiceModel.ServiceContractAttribute> и <xref:System.ServiceModel.OperationContractAttribute> обеспечивает автоматическое создание определения контракта службы в языке описания служб (WSDL).  
  
- Используйте [средство служебной программы метаданных ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для получения документа WSDL и (необязательного) кода и конфигурации для клиента.  
  
- Конечные точки, предоставляющие дуплексные службы, должны быть безопасными. Когда служба получает дуплексное сообщение, она проверяет элемент ReplyTo входящего сообщения, чтобы определить, куда отправлять ответ. Если канал не является безопасным, ненадежный клиент может послать вредоносное сообщение с указанием компьютера для атаки в элементе ReplyTo, что приведет к атаке типа "отказ в обслуживании" на этот компьютер. В случае обычной передачи сообщений по схеме "запрос-ответ" это не является проблемой, так как элемент ReplyTo игнорируется, а ответное сообщение передается по тому каналу, по которому поступило исходное сообщение.  
  
## <a name="see-also"></a>Дополнительно

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Практическое руководство. Доступ к службам с дуплексным контрактом](how-to-access-services-with-a-duplex-contract.md)
- [Дуплекс](../samples/duplex.md)
- [Проектирование и реализация служб](../designing-and-implementing-services.md)
- [Практическое руководство. Определение контракта службы](../how-to-define-a-wcf-service-contract.md)
- [Session](../samples/session.md)
