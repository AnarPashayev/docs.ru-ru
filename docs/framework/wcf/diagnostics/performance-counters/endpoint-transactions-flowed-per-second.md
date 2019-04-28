---
title: 'Конечная точка: Количество поступивших транзакций в секунду'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916257"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="89d24-102">Конечная точка: Количество поступивших транзакций в секунду</span><span class="sxs-lookup"><span data-stu-id="89d24-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="89d24-103">Имя счетчика: Количество поступивших транзакций в секунду.</span><span class="sxs-lookup"><span data-stu-id="89d24-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="89d24-104">Описание</span><span class="sxs-lookup"><span data-stu-id="89d24-104">Description</span></span>  
 <span data-ttu-id="89d24-105">Количество транзакций, поступивших в операции в этой конечной точке в секунду.</span><span class="sxs-lookup"><span data-stu-id="89d24-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="89d24-106">Значение этого счетчика увеличивается каждый раз, когда в сообщении, отправленном в эту конечную точку, содержится идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="89d24-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="89d24-107">Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.</span><span class="sxs-lookup"><span data-stu-id="89d24-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="89d24-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="89d24-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
