---
title: Метод ICorDebugVariableSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 1079351e75ec9c48a9657f514ee56e2e6a4b0920
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731375"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="17cf4-102">Метод ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="17cf4-102">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="17cf4-103">Получает размер переменной в байтах.</span><span class="sxs-lookup"><span data-stu-id="17cf4-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cf4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17cf4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cf4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="17cf4-105">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="17cf4-106">Указатель на 32-разрядное целое число без знака, содержащее размер переменной.</span><span class="sxs-lookup"><span data-stu-id="17cf4-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17cf4-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="17cf4-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17cf4-108">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="17cf4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cf4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="17cf4-109">Requirements</span></span>  

 <span data-ttu-id="17cf4-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17cf4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cf4-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17cf4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17cf4-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17cf4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17cf4-113">**.NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cf4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cf4-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="17cf4-114">See also</span></span>

- [<span data-ttu-id="17cf4-115">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="17cf4-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="17cf4-116">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="17cf4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
