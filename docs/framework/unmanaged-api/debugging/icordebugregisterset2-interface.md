---
title: Интерфейс ICorDebugRegisterSet2
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378198"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="2f439-102">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="2f439-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="2f439-103">Расширяет возможности интерфейса [ICorDebugRegisterSet](icordebugregisterset-interface.md) для аппаратных платформ, имеющих более 64 регистров.</span><span class="sxs-lookup"><span data-stu-id="2f439-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f439-104">Методы</span><span class="sxs-lookup"><span data-stu-id="2f439-104">Methods</span></span>  
  
|<span data-ttu-id="2f439-105">Метод</span><span class="sxs-lookup"><span data-stu-id="2f439-105">Method</span></span>|<span data-ttu-id="2f439-106">Описание</span><span class="sxs-lookup"><span data-stu-id="2f439-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f439-107">Метод GetRegisters</span><span class="sxs-lookup"><span data-stu-id="2f439-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="2f439-108">Возвращает значение каждого регистра (на компьютере, выполняющем в данный момент код), который задается битовой маской.</span><span class="sxs-lookup"><span data-stu-id="2f439-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="2f439-109">Метод GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="2f439-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="2f439-110">Возвращает массив байтов, предоставляющий битовую карту доступных регистров.</span><span class="sxs-lookup"><span data-stu-id="2f439-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="2f439-111">Метод SetRegisters</span><span class="sxs-lookup"><span data-stu-id="2f439-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="2f439-112">Не реализовано в .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="2f439-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f439-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="2f439-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f439-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="2f439-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f439-115">Требования</span><span class="sxs-lookup"><span data-stu-id="2f439-115">Requirements</span></span>  
 <span data-ttu-id="2f439-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f439-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f439-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f439-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f439-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f439-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f439-119">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f439-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f439-120">См. также</span><span class="sxs-lookup"><span data-stu-id="2f439-120">See also</span></span>

- [<span data-ttu-id="2f439-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2f439-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2f439-122">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="2f439-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
