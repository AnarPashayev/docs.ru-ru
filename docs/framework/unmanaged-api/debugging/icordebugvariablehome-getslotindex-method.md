---
title: Метод ICorDebugVariableHome::GetSlotIndex
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993672"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="535d9-102">Метод ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="535d9-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="535d9-103">Возвращает управляемый индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="535d9-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="535d9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="535d9-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="535d9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="535d9-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="535d9-106">[out] Указатель на индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="535d9-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="535d9-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="535d9-107">Return Value</span></span>  
 <span data-ttu-id="535d9-108">Метод возвращает следующие значения.</span><span class="sxs-lookup"><span data-stu-id="535d9-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="535d9-109">Значение</span><span class="sxs-lookup"><span data-stu-id="535d9-109">Value</span></span>|<span data-ttu-id="535d9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="535d9-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="535d9-111">Этот метод вернул значение индекс слота в `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="535d9-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="535d9-112">Текущий [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) экземпляр представляет аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="535d9-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="535d9-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="535d9-113">Remarks</span></span>  
 <span data-ttu-id="535d9-114">Индекс слота можно использовать для получения метаданных для данной локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="535d9-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="535d9-115">Требования</span><span class="sxs-lookup"><span data-stu-id="535d9-115">Requirements</span></span>  
 <span data-ttu-id="535d9-116">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="535d9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="535d9-117">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="535d9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="535d9-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="535d9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="535d9-119">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="535d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535d9-120">См. также</span><span class="sxs-lookup"><span data-stu-id="535d9-120">See also</span></span>

- [<span data-ttu-id="535d9-121">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="535d9-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
