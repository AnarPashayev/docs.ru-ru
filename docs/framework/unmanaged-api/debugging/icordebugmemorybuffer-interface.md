---
title: Интерфейс ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212338"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="fe7d6-102">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="fe7d6-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="fe7d6-103">Представляет буфер в памяти.</span><span class="sxs-lookup"><span data-stu-id="fe7d6-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe7d6-104">Методы</span><span class="sxs-lookup"><span data-stu-id="fe7d6-104">Methods</span></span>  
  
|<span data-ttu-id="fe7d6-105">Метод</span><span class="sxs-lookup"><span data-stu-id="fe7d6-105">Method</span></span>|<span data-ttu-id="fe7d6-106">Описание</span><span class="sxs-lookup"><span data-stu-id="fe7d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe7d6-107">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="fe7d6-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="fe7d6-108">Возвращает размер буфера памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="fe7d6-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="fe7d6-109">Метод GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="fe7d6-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="fe7d6-110">Возвращает начальный адрес буфера памяти.</span><span class="sxs-lookup"><span data-stu-id="fe7d6-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe7d6-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fe7d6-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe7d6-112">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fe7d6-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fe7d6-113">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="fe7d6-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe7d6-114">Требования</span><span class="sxs-lookup"><span data-stu-id="fe7d6-114">Requirements</span></span>  
 <span data-ttu-id="fe7d6-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe7d6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe7d6-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe7d6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe7d6-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe7d6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe7d6-118">**.NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe7d6-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe7d6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="fe7d6-119">See also</span></span>

- [<span data-ttu-id="fe7d6-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fe7d6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fe7d6-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="fe7d6-121">Debugging</span></span>](index.md)
