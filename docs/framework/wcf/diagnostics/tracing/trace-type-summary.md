---
title: Сводка типов трассировок
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925155"
---
# <a name="trace-type-summary"></a><span data-ttu-id="11d44-102">Сводка типов трассировок</span><span class="sxs-lookup"><span data-stu-id="11d44-102">Trace Type Summary</span></span>
<span data-ttu-id="11d44-103">[Уровни источника](https://go.microsoft.com/fwlink/?LinkID=94943) определяются различные уровни трассировки: Критическое, ошибка, предупреждение, сведения и подробные сведения, а также приводится описание `ActivityTracing` флаг, служащего выходные данные границ трассировки и действие передачи событий.</span><span class="sxs-lookup"><span data-stu-id="11d44-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="11d44-104">Вы также можете просмотреть [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) для типов трассировок, которые могут выдаваться источником <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="11d44-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="11d44-105">В следующей таблице перечислены наиболее важные из них.</span><span class="sxs-lookup"><span data-stu-id="11d44-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="11d44-106">Тип трассировки</span><span class="sxs-lookup"><span data-stu-id="11d44-106">Trace Type</span></span>|<span data-ttu-id="11d44-107">Описание</span><span class="sxs-lookup"><span data-stu-id="11d44-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="11d44-108">Critical</span><span class="sxs-lookup"><span data-stu-id="11d44-108">Critical</span></span>|<span data-ttu-id="11d44-109">Неустранимая ошибка или сбой в работе приложения.</span><span class="sxs-lookup"><span data-stu-id="11d44-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="11d44-110">Error</span><span class="sxs-lookup"><span data-stu-id="11d44-110">Error</span></span>|<span data-ttu-id="11d44-111">Устранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="11d44-111">Recoverable error.</span></span>|  
|<span data-ttu-id="11d44-112">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="11d44-112">Warning</span></span>|<span data-ttu-id="11d44-113">Информационное сообщение.</span><span class="sxs-lookup"><span data-stu-id="11d44-113">Informational message.</span></span>|  
|<span data-ttu-id="11d44-114">Сведения</span><span class="sxs-lookup"><span data-stu-id="11d44-114">Information</span></span>|<span data-ttu-id="11d44-115">Несущественная проблема.</span><span class="sxs-lookup"><span data-stu-id="11d44-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="11d44-116">Verbose</span><span class="sxs-lookup"><span data-stu-id="11d44-116">Verbose</span></span>|<span data-ttu-id="11d44-117">Трассировка отладки.</span><span class="sxs-lookup"><span data-stu-id="11d44-117">Debugging trace.</span></span>|  
|<span data-ttu-id="11d44-118">Запуск</span><span class="sxs-lookup"><span data-stu-id="11d44-118">Start</span></span>|<span data-ttu-id="11d44-119">Начало логического блока обработки.</span><span class="sxs-lookup"><span data-stu-id="11d44-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="11d44-120">Suspend</span><span class="sxs-lookup"><span data-stu-id="11d44-120">Suspend</span></span>|<span data-ttu-id="11d44-121">Приостановка логического блока обработки.</span><span class="sxs-lookup"><span data-stu-id="11d44-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="11d44-122">Возобновление</span><span class="sxs-lookup"><span data-stu-id="11d44-122">Resume</span></span>|<span data-ttu-id="11d44-123">Возобновление логического блока обработки.</span><span class="sxs-lookup"><span data-stu-id="11d44-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="11d44-124">Остановить</span><span class="sxs-lookup"><span data-stu-id="11d44-124">Stop</span></span>|<span data-ttu-id="11d44-125">Остановка логического блока обработки.</span><span class="sxs-lookup"><span data-stu-id="11d44-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="11d44-126">Transfer</span><span class="sxs-lookup"><span data-stu-id="11d44-126">Transfer</span></span>|<span data-ttu-id="11d44-127">Изменение идентификации взаимосвязей.</span><span class="sxs-lookup"><span data-stu-id="11d44-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="11d44-128">Действие определяется как сочетание перечисленных выше типов трассировок.</span><span class="sxs-lookup"><span data-stu-id="11d44-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="11d44-129">Ниже приведено регулярное выражение, определяющее идеальное действие в локальной области (области источника трассировки):</span><span class="sxs-lookup"><span data-stu-id="11d44-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="11d44-130">Это означает, что действие должно удовлетворять следующим условиям.</span><span class="sxs-lookup"><span data-stu-id="11d44-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="11d44-131">Должно запускаться и останавливаться трассировками Start и Stop соответственно.</span><span class="sxs-lookup"><span data-stu-id="11d44-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="11d44-132">Трассировка Transfer должна непосредственно предшествовать трассировке Suspend или Resume.</span><span class="sxs-lookup"><span data-stu-id="11d44-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="11d44-133">Не должно содержать никаких трассировок между трассировками Suspend и Resume, если такие трассировки имеются.</span><span class="sxs-lookup"><span data-stu-id="11d44-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="11d44-134">Может содержать любые и в любом количестве трассировки уровня Critical/Error/Warning/Information/Verbose/Transfer при условии соблюдения предыдущих условий.</span><span class="sxs-lookup"><span data-stu-id="11d44-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="11d44-135">Ниже приведено регулярное выражение, определяющее идеальное действие в глобальной области,</span><span class="sxs-lookup"><span data-stu-id="11d44-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="11d44-136">где R - регулярное выражение для действия в локальной области.</span><span class="sxs-lookup"><span data-stu-id="11d44-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="11d44-137">Таким образом, получаем:</span><span class="sxs-lookup"><span data-stu-id="11d44-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
