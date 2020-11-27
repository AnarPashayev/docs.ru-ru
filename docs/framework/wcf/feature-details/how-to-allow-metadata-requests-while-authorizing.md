---
title: 'Как выполнить: Разрешение запросов метаданных в процессе авторизации'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 9acc007ea7837f7b8e6c958fa81547fe4fa5b2c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257617"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="a8d24-102">Как выполнить: Разрешение запросов метаданных в процессе авторизации</span><span class="sxs-lookup"><span data-stu-id="a8d24-102">How To: Allow Metadata Requests While Authorizing</span></span>

<span data-ttu-id="a8d24-103">В процессе настраиваемой авторизации может потребоваться разрешить обработку запроса для метаданных.</span><span class="sxs-lookup"><span data-stu-id="a8d24-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="a8d24-104">Следующий раздел содержит пошаговое руководство для проверки такого запроса.</span><span class="sxs-lookup"><span data-stu-id="a8d24-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="a8d24-105">Дополнительные сведения об авторизации Windows Communication Foundation (WCF) см. в разделе [авторизация](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="a8d24-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="a8d24-106">Разрешение запросов метаданных в процессе авторизации</span><span class="sxs-lookup"><span data-stu-id="a8d24-106">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="a8d24-107">Создайте расширение класса <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="a8d24-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="a8d24-108">Переопределите метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d24-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="a8d24-109">Метод возвращает логическое значение `true` или `false`, в зависимости от того, разрешена ли авторизация.</span><span class="sxs-lookup"><span data-stu-id="a8d24-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="a8d24-110">Информация о текущей процедуре находится в классе <xref:System.ServiceModel.OperationContext> и передается как параметр методу.</span><span class="sxs-lookup"><span data-stu-id="a8d24-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="a8d24-111">При переопределении проверяются имя контракта, пространство имен и действие, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a8d24-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="a8d24-112">При выполнении этих условий возвращается логическое значение `true.`</span><span class="sxs-lookup"><span data-stu-id="a8d24-112">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="a8d24-113">Используйте точку расширения для использования класса.</span><span class="sxs-lookup"><span data-stu-id="a8d24-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="a8d24-114">Дополнительные сведения см. [в разделе инструкции. Создание настраиваемого диспетчера авторизации для службы](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="a8d24-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d24-115">Пример</span><span class="sxs-lookup"><span data-stu-id="a8d24-115">Example</span></span>  

 <span data-ttu-id="a8d24-116">В следующем примере показано переопределение метода <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d24-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a8d24-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a8d24-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="a8d24-118">Авторизация</span><span class="sxs-lookup"><span data-stu-id="a8d24-118">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="a8d24-119">Управление утверждениями и авторизацией с помощью модели удостоверения</span><span class="sxs-lookup"><span data-stu-id="a8d24-119">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
