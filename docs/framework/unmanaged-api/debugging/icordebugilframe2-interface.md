---
title: Интерфейс ICorDebugILFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 2e0f284625e99215900c6aaab94e4eae611787ed
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212104"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="f9d66-102">Интерфейс ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="f9d66-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="f9d66-103">Логическое расширение интерфейса ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="f9d66-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9d66-104">Методы</span><span class="sxs-lookup"><span data-stu-id="f9d66-104">Methods</span></span>  
  
|<span data-ttu-id="f9d66-105">Метод</span><span class="sxs-lookup"><span data-stu-id="f9d66-105">Method</span></span>|<span data-ttu-id="f9d66-106">Описание</span><span class="sxs-lookup"><span data-stu-id="f9d66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9d66-107">Метод EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="f9d66-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="f9d66-108">Возвращает объект ICorDebugTypeEnum, содержащий <xref:System.Type> Параметры в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="f9d66-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="f9d66-109">Метод RemapFunction</span><span class="sxs-lookup"><span data-stu-id="f9d66-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="f9d66-110">Повторно сопоставляет отредактированную функцию, указывая новое смещение MSIL.</span><span class="sxs-lookup"><span data-stu-id="f9d66-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9d66-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9d66-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9d66-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="f9d66-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d66-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f9d66-113">Requirements</span></span>  
 <span data-ttu-id="f9d66-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9d66-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d66-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9d66-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9d66-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9d66-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9d66-117">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d66-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d66-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f9d66-118">See also</span></span>

- [<span data-ttu-id="f9d66-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="f9d66-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
