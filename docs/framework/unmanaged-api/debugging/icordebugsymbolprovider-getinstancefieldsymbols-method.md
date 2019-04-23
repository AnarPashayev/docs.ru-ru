---
title: Метод ICorDebugSymbolProvider::GetInstanceFieldSymbols
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea9afdd2c032e99d7feee6b2935161c70c56787
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187698"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="962ac-102">Метод ICorDebugSymbolProvider::GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="962ac-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="962ac-103">Получает символы поля экземпляра, которые соответствуют сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="962ac-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962ac-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="962ac-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="962ac-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="962ac-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="962ac-106">[in] Число байтов в массиве `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="962ac-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="962ac-107">[in] Массив байтов, содержащий сигнатуру `typespec`.</span><span class="sxs-lookup"><span data-stu-id="962ac-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="962ac-108">[in] Количество запрошенных символов.</span><span class="sxs-lookup"><span data-stu-id="962ac-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="962ac-109">[out] Указатель на число  символов, полученных при помощи метода.</span><span class="sxs-lookup"><span data-stu-id="962ac-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="962ac-110">[out] Указатель на [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) массив, содержащий символы поля запрошенного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="962ac-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="962ac-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="962ac-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="962ac-112">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="962ac-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962ac-113">Требования</span><span class="sxs-lookup"><span data-stu-id="962ac-113">Requirements</span></span>  
 <span data-ttu-id="962ac-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="962ac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962ac-115">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="962ac-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="962ac-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="962ac-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="962ac-117">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962ac-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962ac-118">См. также</span><span class="sxs-lookup"><span data-stu-id="962ac-118">See also</span></span>

- [<span data-ttu-id="962ac-119">Метод GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="962ac-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="962ac-120">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="962ac-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="962ac-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="962ac-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
