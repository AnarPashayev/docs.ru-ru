---
title: Метод ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946254"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="2a10a-102">Метод ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="2a10a-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="2a10a-103">Возвращает размер в байтах загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="2a10a-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a10a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2a10a-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a10a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="2a10a-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="2a10a-106">[out] Указатель на число байтов в загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="2a10a-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a10a-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="2a10a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a10a-108">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="2a10a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a10a-109">Требования</span><span class="sxs-lookup"><span data-stu-id="2a10a-109">Requirements</span></span>  
 <span data-ttu-id="2a10a-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a10a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a10a-111">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a10a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a10a-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a10a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a10a-113">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a10a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a10a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="2a10a-114">See also</span></span>

- [<span data-ttu-id="2a10a-115">Интерфейс ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="2a10a-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="2a10a-116">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2a10a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
