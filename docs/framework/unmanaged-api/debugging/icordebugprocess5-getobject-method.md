---
title: Метод ICorDebugProcess5::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35fdcd4bc3c9dbf6408f501256ce0df0174f9374
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948737"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="b318c-102">Метод ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="b318c-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="b318c-103">Преобразует адрес объекта в объект «ICorDebugObjectValue».</span><span class="sxs-lookup"><span data-stu-id="b318c-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b318c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b318c-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b318c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b318c-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="b318c-106">[in] Адрес объекта.</span><span class="sxs-lookup"><span data-stu-id="b318c-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="b318c-107">[out] Указатель на адрес объекта «ICorDebugObjectValue».</span><span class="sxs-lookup"><span data-stu-id="b318c-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b318c-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="b318c-108">Remarks</span></span>  
 <span data-ttu-id="b318c-109">Если `addr` не указывает на допустимый управляемого объекта, `GetObject` возвращает метод `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="b318c-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b318c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b318c-110">Requirements</span></span>  
 <span data-ttu-id="b318c-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b318c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b318c-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b318c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b318c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b318c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b318c-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b318c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b318c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b318c-115">See also</span></span>

- [<span data-ttu-id="b318c-116">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="b318c-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b318c-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b318c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
