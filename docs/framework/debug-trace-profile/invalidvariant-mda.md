---
title: Помощник по отладке управляемого кода invalidVariant
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052573"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="8aa5f-102">Помощник по отладке управляемого кода invalidVariant</span><span class="sxs-lookup"><span data-stu-id="8aa5f-102">invalidVariant MDA</span></span>
<span data-ttu-id="8aa5f-103">Помощник по отладке управляемого кода (MDA) `invalidVariant` активируется, когда во время вызова из машинного или неуправляемого кода обнаруживается недопустимая структура `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8aa5f-104">Симптомы</span><span class="sxs-lookup"><span data-stu-id="8aa5f-104">Symptoms</span></span>  
 <span data-ttu-id="8aa5f-105">Непредвиденное поведение во время перехода между машинным и управляемым кодом, включающего маршалинг `VARIANT` к объекту.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8aa5f-106">Причина</span><span class="sxs-lookup"><span data-stu-id="8aa5f-106">Cause</span></span>  
 <span data-ttu-id="8aa5f-107">Машинный код передает в управляемый код структуру `VARIANT` неправильного формата.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="8aa5f-108">Среда выполнения пытается выполнить маршалинг этой структуры `VARIANT` в объект и активирует MDA, если `VARIANT` является недопустимой.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="8aa5f-109">Примеры недопустимых структур `VARIANT` включают `VARIANT` с `VARTYPE` VT_EMPTY | VT_BYREF или `VARIANT` с `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8aa5f-110">Решение</span><span class="sxs-lookup"><span data-stu-id="8aa5f-110">Resolution</span></span>  
 <span data-ttu-id="8aa5f-111">Машинный или неуправляемый код, передающий `VARIANT`, должен убедиться, что структура `VARIANT` правильно сформирована и инициализирована.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8aa5f-112">Влияние на среду выполнения</span><span class="sxs-lookup"><span data-stu-id="8aa5f-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="8aa5f-113">MDA не оказывает влияния на поведение среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8aa5f-114">Вывод</span><span class="sxs-lookup"><span data-stu-id="8aa5f-114">Output</span></span>  
 <span data-ttu-id="8aa5f-115">Сообщение MDA, указывающее, что среда выполнения обнаружила недопустимую структуру `VARIANT`, переданную в управляемый код неуправляемым модулем.</span><span class="sxs-lookup"><span data-stu-id="8aa5f-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8aa5f-116">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="8aa5f-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8aa5f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8aa5f-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8aa5f-118">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="8aa5f-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8aa5f-119">Маршалинг взаимодействия</span><span class="sxs-lookup"><span data-stu-id="8aa5f-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
