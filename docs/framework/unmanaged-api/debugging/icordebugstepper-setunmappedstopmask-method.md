---
title: Метод ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987458"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="4a8f0-102">Метод ICorDebugStepper::SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="4a8f0-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="4a8f0-103">Задает значение, указывающее тип кода, в котором выполнение будет остановлено.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a8f0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a8f0-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a8f0-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a8f0-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="4a8f0-106">[in] Значение, указывающее тип кода, в котором отладчик остановит выполнение перечисления CorDebugUnmappedStop.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="4a8f0-107">Значение по умолчанию — STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="4a8f0-108">Значение по умолчанию STOP_UNMANAGED допустим только для отладки взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a8f0-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="4a8f0-109">Remarks</span></span>  
 <span data-ttu-id="4a8f0-110">Когда отладчик обнаруживает компиляции just-in-time (JIT), который не имеет соответствующего сопоставления промежуточного языка Майкрософт (MSIL), он прерывает выполнение, если установлен флаг, указывающий типа неуправляемого кода; в противном случае проверка прозрачно продолжается.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="4a8f0-111">Если отладчик не использует средство организации пошагового режима для входа в метод, то он не будет обход обязательно неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="4a8f0-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a8f0-112">Требования</span><span class="sxs-lookup"><span data-stu-id="4a8f0-112">Requirements</span></span>  
 <span data-ttu-id="4a8f0-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a8f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a8f0-114">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a8f0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a8f0-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a8f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a8f0-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a8f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
