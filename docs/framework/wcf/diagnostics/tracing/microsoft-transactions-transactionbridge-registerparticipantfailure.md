---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164298"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="55fc5-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="55fc5-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="55fc5-103">Службе протокола WS-AT не удалось зарегистрировать участника для протокола управления.</span><span class="sxs-lookup"><span data-stu-id="55fc5-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="55fc5-104">Описание</span><span class="sxs-lookup"><span data-stu-id="55fc5-104">Description</span></span>  
 <span data-ttu-id="55fc5-105">Отслеживается, обнаруживает ли MSDTC недопустимый запрос на регистрацию.</span><span class="sxs-lookup"><span data-stu-id="55fc5-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="55fc5-106">Это может происходить из-за множественных запросов на регистрацию завершения и внутренних ошибок.</span><span class="sxs-lookup"><span data-stu-id="55fc5-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="55fc5-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="55fc5-107">Troubleshooting</span></span>  
 <span data-ttu-id="55fc5-108">Не пытайтесь зарегистрировать завершение несколько раз.</span><span class="sxs-lookup"><span data-stu-id="55fc5-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="55fc5-109">Проверьте строку состояния в сообщении трассировки, чтобы определить, имеются ли элементы, с которыми можно произвести какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="55fc5-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fc5-110">См. также</span><span class="sxs-lookup"><span data-stu-id="55fc5-110">See also</span></span>

- [<span data-ttu-id="55fc5-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="55fc5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="55fc5-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="55fc5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="55fc5-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="55fc5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
