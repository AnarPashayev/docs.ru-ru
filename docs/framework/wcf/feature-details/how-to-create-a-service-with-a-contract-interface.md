---
title: Практическое руководство. Создание службы с помощью интерфейса контракта
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597167"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="8257f-102">Практическое руководство. Создание службы с помощью интерфейса контракта</span><span class="sxs-lookup"><span data-stu-id="8257f-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="8257f-103">Предпочтительный способ создания контракта Windows Communication Foundation (WCF) — использование интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8257f-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="8257f-104">Такой контракт определяет набор и структуру сообщений, необходимых для доступа к операциям, предлагаемым службой.</span><span class="sxs-lookup"><span data-stu-id="8257f-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="8257f-105">Этот интерфейс определяет типы входных и выходных данных путем применения класса <xref:System.ServiceModel.ServiceContractAttribute> к интерфейсу и класса <xref:System.ServiceModel.OperationContractAttribute> к методам, которые требуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="8257f-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="8257f-106">Дополнительные сведения о контрактах служб см. в разделе [Разработка контрактов служб](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8257f-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="8257f-107">Создание контракта WCF с интерфейсом</span><span class="sxs-lookup"><span data-stu-id="8257f-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="8257f-108">Создайте новый интерфейс, используя Visual Basic, C# или любой другой язык среды CLR.</span><span class="sxs-lookup"><span data-stu-id="8257f-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="8257f-109">Примените класс <xref:System.ServiceModel.ServiceContractAttribute> к интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="8257f-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="8257f-110">Определите методы интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8257f-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="8257f-111">Примените <xref:System.ServiceModel.OperationContractAttribute> класс к каждому методу, который должен быть предоставлен как часть общедоступного контракта WCF.</span><span class="sxs-lookup"><span data-stu-id="8257f-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8257f-112">Пример</span><span class="sxs-lookup"><span data-stu-id="8257f-112">Example</span></span>  
 <span data-ttu-id="8257f-113">В следующем примере кода показан интерфейс, определяющий контракт службы.</span><span class="sxs-lookup"><span data-stu-id="8257f-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="8257f-114">Методы, к которым применен класс <xref:System.ServiceModel.OperationContractAttribute>, по умолчанию используют шаблон обмена сообщениями «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="8257f-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="8257f-115">Дополнительные сведения об этом шаблоне сообщений см. [в разделе как создать контракт типа "запрос-ответ"](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8257f-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="8257f-116">Кроме того, можно создать и использовать другие шаблоны сообщений путем задания свойств атрибута.</span><span class="sxs-lookup"><span data-stu-id="8257f-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="8257f-117">Дополнительные примеры см. [в разделе как создать односторонний контракт](how-to-create-a-one-way-contract.md) и [как создать дуплексный контракт](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8257f-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8257f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8257f-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
