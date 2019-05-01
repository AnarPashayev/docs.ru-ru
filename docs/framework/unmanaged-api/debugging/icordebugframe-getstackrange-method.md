---
title: Метод ICorDebugFrame::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995817"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="c911b-102">Метод ICorDebugFrame::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="c911b-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="c911b-103">Возвращает диапазон абсолютных адресов этого кадра стека.</span><span class="sxs-lookup"><span data-stu-id="c911b-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c911b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c911b-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c911b-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="c911b-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="c911b-106">[out] Указатель на `CORDB_ADDRESS` , указывающий начальный адрес кадра стека, представленный этим `ICorDebugFrame` объекта.</span><span class="sxs-lookup"><span data-stu-id="c911b-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="c911b-107">[out] Указатель на `CORDB_ADDRESS` , указывающий конечный адрес кадра стека, представленный этим `ICorDebugFrame` объекта.</span><span class="sxs-lookup"><span data-stu-id="c911b-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c911b-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="c911b-108">Remarks</span></span>  
 <span data-ttu-id="c911b-109">Диапазон адресов стека полезно для соединения вместе перемежаемых трассировок стека из нескольких обработчиков отладки.</span><span class="sxs-lookup"><span data-stu-id="c911b-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="c911b-110">Числовой диапазон не предоставляет сведений о содержимом кадра стека.</span><span class="sxs-lookup"><span data-stu-id="c911b-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="c911b-111">Он имеет смысл только для сравнения расположений кадра стека.</span><span class="sxs-lookup"><span data-stu-id="c911b-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c911b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c911b-112">Requirements</span></span>  
 <span data-ttu-id="c911b-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c911b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c911b-114">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c911b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c911b-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c911b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c911b-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c911b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
