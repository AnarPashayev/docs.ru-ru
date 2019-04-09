---
title: Метод ICorDebugStaticFieldSymbol::GetAddress
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e233fe78f6b2c721114f0307a8ca414625a0087e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160424"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="8fc12-102">Метод ICorDebugStaticFieldSymbol::GetAddress</span><span class="sxs-lookup"><span data-stu-id="8fc12-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="8fc12-103">Получает адрес статического поля.</span><span class="sxs-lookup"><span data-stu-id="8fc12-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc12-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8fc12-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc12-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="8fc12-105">Parameters</span></span>  
 <span data-ttu-id="8fc12-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="8fc12-106">pRVA</span></span>  
 <span data-ttu-id="8fc12-107">[out] Указатель на относительный виртуальный адрес (RVA) статического поля.</span><span class="sxs-lookup"><span data-stu-id="8fc12-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fc12-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="8fc12-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fc12-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="8fc12-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc12-110">Требования</span><span class="sxs-lookup"><span data-stu-id="8fc12-110">Requirements</span></span>  
 <span data-ttu-id="8fc12-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc12-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc12-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fc12-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fc12-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fc12-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8fc12-114">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8fc12-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc12-115">См. также</span><span class="sxs-lookup"><span data-stu-id="8fc12-115">See also</span></span>

- [<span data-ttu-id="8fc12-116">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="8fc12-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="8fc12-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8fc12-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
