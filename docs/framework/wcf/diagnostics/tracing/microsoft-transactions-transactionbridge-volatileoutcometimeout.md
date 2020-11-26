---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: bc2cdc2221ec522b44c36ef3320b77124d61850e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236706"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="24c6f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="24c6f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="24c6f-103">Истекло время ожидания службой протокола WS-AT ответа на результативное сообщение от неустойчивого участника.</span><span class="sxs-lookup"><span data-stu-id="24c6f-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="24c6f-104">При возвращении участника результат транзакции будет поставлен под сомнение.</span><span class="sxs-lookup"><span data-stu-id="24c6f-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="24c6f-105">Описание</span><span class="sxs-lookup"><span data-stu-id="24c6f-105">Description</span></span>  

 <span data-ttu-id="24c6f-106">Трассируется, когда неустойчивый участник принял решение зафиксировать или прервать транзакцию, однако не ответил на сообщение Commit или Rollback в течение заданного времени.</span><span class="sxs-lookup"><span data-stu-id="24c6f-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="24c6f-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="24c6f-107">Troubleshooting</span></span>  

 <span data-ttu-id="24c6f-108">Убедитесь, что все неустойчивые участники имеют возможность ответить в течение заданного времени.</span><span class="sxs-lookup"><span data-stu-id="24c6f-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="24c6f-109">Период времени по умолчанию - 180 секунд.</span><span class="sxs-lookup"><span data-stu-id="24c6f-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="24c6f-110">Если этого недостаточно, увеличьте значение политики таймера `VolatileOutcomeDelay` для протокола WS-AT.</span><span class="sxs-lookup"><span data-stu-id="24c6f-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c6f-111">См. также</span><span class="sxs-lookup"><span data-stu-id="24c6f-111">See also</span></span>

- [<span data-ttu-id="24c6f-112">Трассировка</span><span class="sxs-lookup"><span data-stu-id="24c6f-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="24c6f-113">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="24c6f-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="24c6f-114">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="24c6f-114">Administration and Diagnostics</span></span>](../index.md)
