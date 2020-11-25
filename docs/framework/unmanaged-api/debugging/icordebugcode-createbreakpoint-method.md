---
title: Метод ICorDebugCode::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: ade428ce001a6b40e2fed67f4f23b12cef5ea30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717661"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="1ccd9-102">Метод ICorDebugCode::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1ccd9-102">ICorDebugCode::CreateBreakpoint Method</span></span>

<span data-ttu-id="1ccd9-103">Создает точку останова в этом сегменте кода в указанном смещении.</span><span class="sxs-lookup"><span data-stu-id="1ccd9-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ccd9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ccd9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ccd9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ccd9-105">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="1ccd9-106">окне Смещение для создания точки останова.</span><span class="sxs-lookup"><span data-stu-id="1ccd9-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="1ccd9-107">заполняет Указатель на адрес объекта "ICorDebugFunctionBreakpoint", представляющего точку останова.</span><span class="sxs-lookup"><span data-stu-id="1ccd9-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ccd9-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="1ccd9-108">Remarks</span></span>  

 <span data-ttu-id="1ccd9-109">Прежде чем точка останова станет активной, ее необходимо добавить в объект Process.</span><span class="sxs-lookup"><span data-stu-id="1ccd9-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="1ccd9-110">Если этот код является кодом на языке MSIL и имеется JIT-скомпилированная собственная версия кода, то точка останова будет применена и в JIT-скомпилированном коде.</span><span class="sxs-lookup"><span data-stu-id="1ccd9-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="1ccd9-111">(То же самое верно, если код компилируется позже.)</span><span class="sxs-lookup"><span data-stu-id="1ccd9-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ccd9-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1ccd9-112">Requirements</span></span>  

 <span data-ttu-id="1ccd9-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ccd9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ccd9-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ccd9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ccd9-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ccd9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ccd9-116">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ccd9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
