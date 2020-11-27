---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: e39ca97bdefafee840206036f89e8b165609516a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263013"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="47248-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="47248-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>

<span data-ttu-id="47248-103">Возникает при невозможности правильного закрытия службы или при прерывании службы.</span><span class="sxs-lookup"><span data-stu-id="47248-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47248-104">Описание</span><span class="sxs-lookup"><span data-stu-id="47248-104">Description</span></span>  

 <span data-ttu-id="47248-105">Данный код ошибки отображается только в файле журнала.</span><span class="sxs-lookup"><span data-stu-id="47248-105">This error code only appears in the log file.</span></span> <span data-ttu-id="47248-106">Как правило, он указывает на наличие программной ошибки, например при попытке закрыть службу после того, как был вызван метод Abort.</span><span class="sxs-lookup"><span data-stu-id="47248-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="47248-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="47248-107">Troubleshooting</span></span>  

 <span data-ttu-id="47248-108">Проверьте исходный код приложения.</span><span class="sxs-lookup"><span data-stu-id="47248-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47248-109">См. также</span><span class="sxs-lookup"><span data-stu-id="47248-109">See also</span></span>

- [<span data-ttu-id="47248-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="47248-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="47248-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="47248-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="47248-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="47248-112">Administration and Diagnostics</span></span>](../index.md)
