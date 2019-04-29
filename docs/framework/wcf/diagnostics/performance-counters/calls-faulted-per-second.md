---
title: Количество сбоев вызовов в секунду
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 5b7569b6a00757fbb863b90b25b44815a349ab07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797401"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="151ab-102">Количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="151ab-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="151ab-103">Имя счетчика: Количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="151ab-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="151ab-104">Описание</span><span class="sxs-lookup"><span data-stu-id="151ab-104">Description</span></span>  
 <span data-ttu-id="151ab-105">Число вызовов, возвращающих ошибки этой операции за секунду.</span><span class="sxs-lookup"><span data-stu-id="151ab-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="151ab-106">Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.</span><span class="sxs-lookup"><span data-stu-id="151ab-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="151ab-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="151ab-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="151ab-108">В приложениях Windows Communication Foundation (WCF) методы службы передают сведения об ошибке обработки с помощью сообщения об ошибках SOAP.</span><span class="sxs-lookup"><span data-stu-id="151ab-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="151ab-109">Сообщения об ошибках SOAP - это типы сообщений, которые включаются в метаданные, связанные с операцией службы, и таким образом создают контракт ошибок, который клиенты могут использовать для повышения надежности и интерактивности своей работы.</span><span class="sxs-lookup"><span data-stu-id="151ab-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="151ab-110">Поскольку сообщения об ошибках SOAP передаются клиентам в формате XML, они поддерживают возможность взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="151ab-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151ab-111">См. также</span><span class="sxs-lookup"><span data-stu-id="151ab-111">See also</span></span>

- [<span data-ttu-id="151ab-112">Указание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="151ab-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
