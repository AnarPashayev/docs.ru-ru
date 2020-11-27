---
title: Практическое руководство. Создание службы, для которой требуются сеансы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 13287d0d5c989fc3a5dc95c6df5d548bca9df4d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286361"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="c3d10-102">Практическое руководство. Создание службы, для которой требуются сеансы</span><span class="sxs-lookup"><span data-stu-id="c3d10-102">How to: Create a Service That Requires Sessions</span></span>

<span data-ttu-id="c3d10-103">Сеансы создают общее состояние между двумя и более конечными точками, что обеспечивает полезные функции, такие как обратные вызовы, безопасность по всем участкам передачи и ассоциации между клиентами и экземплярами служб.</span><span class="sxs-lookup"><span data-stu-id="c3d10-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="c3d10-104">Дополнительные сведения о сеансах в приложениях Windows Communication Foundation (WCF) см. в разделе [использование сеансов](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="c3d10-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="c3d10-105">Указание требования контракта о необходимости поддержки сеанса его привязкой</span><span class="sxs-lookup"><span data-stu-id="c3d10-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="c3d10-106">Создайте контракт службы как минимум с одной операцией.</span><span class="sxs-lookup"><span data-stu-id="c3d10-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="c3d10-107">Пример создания контракта службы см. [в разделе как определить контракт службы](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="c3d10-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="c3d10-108">Измените элемент <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>, объявляющий контракт, присвоив свойству <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="c3d10-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="c3d10-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, если требуется, чтобы этот контракт выполнялся в сеансе.</span><span class="sxs-lookup"><span data-stu-id="c3d10-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="c3d10-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>, если этот контракт может выполняться в сеансе.</span><span class="sxs-lookup"><span data-stu-id="c3d10-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="c3d10-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>, если требуется, чтобы этот контракт не выполнялся в сеансе.</span><span class="sxs-lookup"><span data-stu-id="c3d10-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="c3d10-112">Настройте конечную точку службы так, чтобы она использовала привязку, поддерживающую сеансы.</span><span class="sxs-lookup"><span data-stu-id="c3d10-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="c3d10-113">В следующем примере конфигурации показано использование привязки <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, поддерживающей сеанс WS`-`ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="c3d10-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="c3d10-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c3d10-114">Example</span></span>  

 <span data-ttu-id="c3d10-115">В следующем примере кода демонстрируется указание требования сеанса на уровне контракта и использование файла конфигурации для поддержки этого требования с помощью привязки <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3d10-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="c3d10-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c3d10-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
