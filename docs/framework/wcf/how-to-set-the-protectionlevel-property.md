---
title: Практическое руководство. Установка свойства ProtectionLevel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: ce9fc8549218db5a1446026421f1a7ba1e5a23aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089852"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Практическое руководство. Установка свойства ProtectionLevel
Уровень защиты можно задать, применив соответствующий атрибут и задав свойство. Защиту на уровне службы можно задать таким образом, чтобы она влияла на все части каждого сообщения, можно также задать защиту на более детализированных уровнях - от методов до частей сообщения. Дополнительные сведения о `ProtectionLevel` свойство, см. в разделе [уровень защиты понимание](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Уровни защиты можно задавать только в коде, а не в конфигурации.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Подписание всех сообщений для службы  
  
1.  Создайте интерфейс для службы.  
  
2.  Примените к службе атрибут <xref:System.ServiceModel.ServiceContractAttribute> и задайте значение <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.Sign>, как показано в следующем примере кода (уровень по умолчанию - <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Подписание всех частей сообщения для операции  
  
1.  Создайте интерфейс для службы и примените к нему атрибут <xref:System.ServiceModel.ServiceContractAttribute>.  
  
2.  Добавьте в интерфейс объявление метода.  
  
3.  Примените к методу атрибут <xref:System.ServiceModel.OperationContractAttribute> и задайте значение <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.Sign>, как показано в следующем примере кода.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Защита сообщений об ошибках  
 Создаваемые в службе исключения можно отправить клиенту в виде ошибок SOAP. Дополнительные сведения о создании строго типизированных ошибок, см. в разделе [задание и обработка сбоев в контрактах и службах](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) и [как: Объявление сбоев в контрактах служб](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Защита сообщения об ошибке  
  
1.  Создайте тип, представляющий сообщение об ошибке. В следующем примере описано создание класса, именуемого `MathFault`, с двумя полями.  
  
2.  Примените к типу атрибут <xref:System.Runtime.Serialization.DataContractAttribute>, а к каждому полю, которое должно быть сериализовано, - атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>, как показано в следующем примере кода.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  Примените атрибут <xref:System.ServiceModel.FaultContractAttribute> к методу, который будет возвращать ошибку, и настройте параметр `detailType` к типу класса ошибки в интерфейсе, который будет возвращать ошибку,  
  
4.  Задайте для свойства <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> значение <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> в конструкторе, как показано в следующем примере кода.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Защита частей сообщения  
 Для защиты частей сообщения следует использовать контракт сообщения. Дополнительные сведения о контрактах сообщений см. в разделе [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Защита тела сообщения  
  
1.  Создайте тип, представляющий сообщение. В следующем примере описано создание класса `Company` двумя полями: `CompanyName` и `CompanyID`.  
  
2.  Примените атрибут <xref:System.ServiceModel.MessageContractAttribute> к классу и задайте значение <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Примените атрибут <xref:System.ServiceModel.MessageHeaderAttribute> к полю, которое будет выражено как заголовок сообщения, и задайте значение `ProtectionLevel` для свойства <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Применить <xref:System.ServiceModel.MessageBodyMemberAttribute> к любому полю, которое будет выражено как часть текста сообщения и задайте `ProtectionLevel` свойства <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, как показано в следующем примере.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется, как задать свойство `ProtectionLevel` нескольких классов атрибута в разных местах службы.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В следующем примере кода показаны пространства имен, необходимые для компиляции примера кода.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Основные сведения об уровне защиты](../../../docs/framework/wcf/understanding-protection-level.md)
