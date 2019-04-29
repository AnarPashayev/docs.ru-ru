---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666837"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="e1822-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="e1822-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="e1822-103">При закрытии подключений в этом пуле подключений возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="e1822-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e1822-104">Описание</span><span class="sxs-lookup"><span data-stu-id="e1822-104">Description</span></span>  
 <span data-ttu-id="e1822-105">Эта трассировка уровня ошибки указывает, что произошла ошибка при закрытии пулов подключений, используемый в соединении Windows Communication Foundation (WCF), функцию пулов.</span><span class="sxs-lookup"><span data-stu-id="e1822-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="e1822-106">Эта ошибка может быть вызвана тем, что не удалось закрыть подключение (или набор подключений) из пула в течение времени ожидания (CloseTimeout).</span><span class="sxs-lookup"><span data-stu-id="e1822-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="e1822-107">При выдаче этого исключения все оставшиеся незакрытые подключения из этого пула прерываются. Незакрытые подключения из других пулов оставляются.</span><span class="sxs-lookup"><span data-stu-id="e1822-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1822-108">См. также</span><span class="sxs-lookup"><span data-stu-id="e1822-108">See also</span></span>

- [<span data-ttu-id="e1822-109">Трассировка</span><span class="sxs-lookup"><span data-stu-id="e1822-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e1822-110">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="e1822-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e1822-111">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="e1822-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
