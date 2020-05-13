---
title: Интерфейс ICorDebugInternalFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: ce3ca4745727a1738fdc1a526480d70ffc55ccf8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209907"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="1c9b7-102">Интерфейс ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="1c9b7-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="1c9b7-103">Предоставляет сведения о внутренних кадрах, включая стековый адрес и положение относительно объектов ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="1c9b7-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c9b7-104">Методы</span><span class="sxs-lookup"><span data-stu-id="1c9b7-104">Methods</span></span>  
  
|<span data-ttu-id="1c9b7-105">Метод</span><span class="sxs-lookup"><span data-stu-id="1c9b7-105">Method</span></span>|<span data-ttu-id="1c9b7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1c9b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c9b7-107">Метод GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="1c9b7-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="1c9b7-108">Возвращает адрес стека внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="1c9b7-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="1c9b7-109">Метод IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="1c9b7-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="1c9b7-110">Проверяет, `this` находится ли внутренний кадр ближе к конечному объекту, чем указанный объект ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="1c9b7-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c9b7-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c9b7-111">Remarks</span></span>  
 <span data-ttu-id="1c9b7-112">Этот интерфейс расширяет интерфейс ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="1c9b7-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c9b7-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="1c9b7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c9b7-114">Требования</span><span class="sxs-lookup"><span data-stu-id="1c9b7-114">Requirements</span></span>  
 <span data-ttu-id="1c9b7-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c9b7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c9b7-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c9b7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c9b7-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c9b7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c9b7-118">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c9b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c9b7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1c9b7-119">See also</span></span>

- [<span data-ttu-id="1c9b7-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1c9b7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1c9b7-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="1c9b7-121">Debugging</span></span>](index.md)
