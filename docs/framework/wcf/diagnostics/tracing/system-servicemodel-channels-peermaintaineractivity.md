---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596081"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="69f8a-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="69f8a-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="69f8a-103">Модуль PeerMaintainer выполняет определенную операцию (подробности содержатся в теле сообщения трассировки).</span><span class="sxs-lookup"><span data-stu-id="69f8a-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="69f8a-104">Описание</span><span class="sxs-lookup"><span data-stu-id="69f8a-104">Description</span></span>  
 <span data-ttu-id="69f8a-105">Эта трассировка возникает в ходе различных операций модуля обслуживания PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="69f8a-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="69f8a-106">PeerMaintainer - это внутренний компонент узла PeerNode.</span><span class="sxs-lookup"><span data-stu-id="69f8a-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="69f8a-107">Каждую минуту или каждые 32 полученных сообщения он отправляет соседним узлам сообщение LinkUtility со статистическими данными о том, сколько сообщений было принято/отправлено и сколько из них полезны (не дубликаты, не подделаны).</span><span class="sxs-lookup"><span data-stu-id="69f8a-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="69f8a-108">Это позволяет определить значение LinkUtility определенного соседнего узла.</span><span class="sxs-lookup"><span data-stu-id="69f8a-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="69f8a-109">Приблизительно каждые пять минут модуль обслуживания проверяет состояние соединений с соседними узлами.</span><span class="sxs-lookup"><span data-stu-id="69f8a-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="69f8a-110">Если количество соединений с соседними узлами превышает идеальное число, модуль обслуживания урезает наименее полезные соединения.</span><span class="sxs-lookup"><span data-stu-id="69f8a-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="69f8a-111">Если соединений недостаточно, модуль обслуживания приобретает новые соединения.</span><span class="sxs-lookup"><span data-stu-id="69f8a-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f8a-112">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="69f8a-112">See also</span></span>

- [<span data-ttu-id="69f8a-113">Трассировка</span><span class="sxs-lookup"><span data-stu-id="69f8a-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="69f8a-114">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="69f8a-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="69f8a-115">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="69f8a-115">Administration and Diagnostics</span></span>](../index.md)
