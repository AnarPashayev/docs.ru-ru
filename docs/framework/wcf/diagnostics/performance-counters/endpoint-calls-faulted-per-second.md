---
title: 'Конечная точка: количество сбоев вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 84dabf1215a02133874f3a0a55578c684a3308d9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319980"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="610cb-102">Конечная точка: количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="610cb-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="610cb-103">Имя счетчика: Calls Faulted Per Second.</span><span class="sxs-lookup"><span data-stu-id="610cb-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="610cb-104">Описание</span><span class="sxs-lookup"><span data-stu-id="610cb-104">Description</span></span>  
 <span data-ttu-id="610cb-105">Количество вызовов, которые возвратили сбой данной конечной точке в секунду.</span><span class="sxs-lookup"><span data-stu-id="610cb-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="610cb-106">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="610cb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="610cb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="610cb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="610cb-108">В приложениях Windows Communication Foundation (WCF) методы служб обмениваются сведениями об ошибках обработки с помощью сообщений о сбоях SOAP.</span><span class="sxs-lookup"><span data-stu-id="610cb-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="610cb-109">Сообщения об ошибках SOAP - это типы сообщений, которые включаются в метаданные, связанные с операцией службы, и таким образом создают контракт ошибок, который клиенты могут использовать для повышения надежности и интерактивности своей работы.</span><span class="sxs-lookup"><span data-stu-id="610cb-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="610cb-110">Поскольку сообщения об ошибках SOAP передаются клиентам в формате XML, они поддерживают возможность взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="610cb-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610cb-111">См. также</span><span class="sxs-lookup"><span data-stu-id="610cb-111">See also</span></span>

- [<span data-ttu-id="610cb-112">Указание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="610cb-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
