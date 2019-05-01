---
title: Практическое руководство. Использование ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047260"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="5aa33-102">Практическое руководство. Использование ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="5aa33-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="5aa33-103">Универсальный класс <xref:System.ServiceModel.ChannelFactory%601> используется в сложных сценариях, требующих создания фабрики каналов, которая может использоваться для создания нескольких каналов.</span><span class="sxs-lookup"><span data-stu-id="5aa33-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="5aa33-104">Создание и использование класса ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="5aa33-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="5aa33-105">Постройте и запустите службу Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5aa33-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="5aa33-106">Дополнительные сведения см. в разделе [проектирование и реализация служб](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Настройка служб](../../../../docs/framework/wcf/configuring-services.md), и [размещение служб](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="5aa33-106">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2. <span data-ttu-id="5aa33-107">Используйте [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) для создания контракта (интерфейс) для клиента.</span><span class="sxs-lookup"><span data-stu-id="5aa33-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="5aa33-108">В коде клиента для создания нескольких прослушивателей конечной точки используйте класс <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="5aa33-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa33-109">Пример</span><span class="sxs-lookup"><span data-stu-id="5aa33-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
