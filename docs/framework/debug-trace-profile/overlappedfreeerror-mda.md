---
title: Помощник по отладке управляемого кода overlappedFreeError
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: defd7f90fcac8d1e98104796682058638c9bd799
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753690"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="66675-102">Помощник по отладке управляемого кода overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="66675-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="66675-103">Помощник по отладке управляемого кода `overlappedFreeError` (MDA) активируется, если метод <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> вызывается до завершения перекрывающейся операции.</span><span class="sxs-lookup"><span data-stu-id="66675-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="66675-104">Симптомы</span><span class="sxs-lookup"><span data-stu-id="66675-104">Symptoms</span></span>  
 <span data-ttu-id="66675-105">Нарушение прав доступа или повреждение кучи сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="66675-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="66675-106">Причина</span><span class="sxs-lookup"><span data-stu-id="66675-106">Cause</span></span>  
 <span data-ttu-id="66675-107">Перекрывающаяся структура была освобождена до завершения операции.</span><span class="sxs-lookup"><span data-stu-id="66675-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="66675-108">Функция, использующая перекрывающийся указатель, может выполнять запись в структуру позднее, после ее освобождения.</span><span class="sxs-lookup"><span data-stu-id="66675-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="66675-109">Это может привести к повреждению кучи, поскольку требуемая область может быть занята другим объектом.</span><span class="sxs-lookup"><span data-stu-id="66675-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="66675-110">Этот помощник по отладке управляемого кода может не возвращать ошибку, если перекрывающаяся операция не была успешно запущена.</span><span class="sxs-lookup"><span data-stu-id="66675-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="66675-111">Решение</span><span class="sxs-lookup"><span data-stu-id="66675-111">Resolution</span></span>  
 <span data-ttu-id="66675-112">Прежде чем вызывать метод <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>, убедитесь, что операция ввода-вывода, использующая перекрывающуюся структуру, была завершена.</span><span class="sxs-lookup"><span data-stu-id="66675-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="66675-113">Влияние на среду выполнения</span><span class="sxs-lookup"><span data-stu-id="66675-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="66675-114">Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.</span><span class="sxs-lookup"><span data-stu-id="66675-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="66675-115">Вывод</span><span class="sxs-lookup"><span data-stu-id="66675-115">Output</span></span>  
 <span data-ttu-id="66675-116">Ниже приведен пример выходных данных для этого помощника по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="66675-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="66675-117">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="66675-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66675-118">См. также</span><span class="sxs-lookup"><span data-stu-id="66675-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="66675-119">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="66675-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="66675-120">Маршалинг взаимодействия</span><span class="sxs-lookup"><span data-stu-id="66675-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
