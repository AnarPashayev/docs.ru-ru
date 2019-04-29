---
title: 'Служба: Количество поступивших транзакций в секунду'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: cb41abe74568c3e9641443b81fce3fb6eb6e41bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939416"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="d8d6a-102">Служба: Количество поступивших транзакций в секунду</span><span class="sxs-lookup"><span data-stu-id="d8d6a-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="d8d6a-103">Имя счетчика: Количество поступивших транзакций в секунду.</span><span class="sxs-lookup"><span data-stu-id="d8d6a-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8d6a-104">Описание</span><span class="sxs-lookup"><span data-stu-id="d8d6a-104">Description</span></span>  
 <span data-ttu-id="d8d6a-105">Количество транзакций в операциях для данной службы в секунду.</span><span class="sxs-lookup"><span data-stu-id="d8d6a-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="d8d6a-106">Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.</span><span class="sxs-lookup"><span data-stu-id="d8d6a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8d6a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d8d6a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
