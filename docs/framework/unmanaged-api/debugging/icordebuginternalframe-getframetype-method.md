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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b6f0550bad534379b562c3df9da9ab917f5270
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946354"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="c61bc-102">Метод ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="c61bc-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="c61bc-103">Получает тип данного внутреннего фрейма.</span><span class="sxs-lookup"><span data-stu-id="c61bc-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61bc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c61bc-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c61bc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="c61bc-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="c61bc-106">[out] Указатель на значение, указывающее тип внутреннего кадра, представленный этим перечисление CorDebugInternalFrameType `ICorDebugInternalFrame` объекта.</span><span class="sxs-lookup"><span data-stu-id="c61bc-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c61bc-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="c61bc-107">Remarks</span></span>  
 <span data-ttu-id="c61bc-108">Тип внутренний фрейм никогда не будет STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="c61bc-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="c61bc-109">Отладчики корректно должен игнорировать Неизвестный кадр внутренних типов.</span><span class="sxs-lookup"><span data-stu-id="c61bc-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c61bc-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c61bc-110">Requirements</span></span>  
 <span data-ttu-id="c61bc-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61bc-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c61bc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c61bc-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c61bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c61bc-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
