---
title: Метод ICorDebugInternalFrame::GetFrameType
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: 6b598352f734cf47514a82de1d0fca65d430a9ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209972"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="b813f-102">Метод ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="b813f-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="b813f-103">Возвращает тип этого внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="b813f-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b813f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b813f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b813f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b813f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="b813f-106">заполняет Указатель на значение перечисления CorDebugInternalFrameType, указывающее тип внутреннего кадра, представленного этим `ICorDebugInternalFrame` объектом.</span><span class="sxs-lookup"><span data-stu-id="b813f-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b813f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="b813f-107">Remarks</span></span>  
 <span data-ttu-id="b813f-108">Тип внутреннего кадра никогда не будет STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="b813f-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="b813f-109">Отладчики должны корректно пропускать нераспознаваемые типы внутренних кадров.</span><span class="sxs-lookup"><span data-stu-id="b813f-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b813f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b813f-110">Requirements</span></span>  
 <span data-ttu-id="b813f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b813f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b813f-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b813f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b813f-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b813f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b813f-114">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b813f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
