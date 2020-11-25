---
title: Метод ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: cee1556fd7d803765b09a7cbd86ce2ff7be91cc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732636"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="39c46-102">Метод ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="39c46-102">ICorDebugProcess6::GetCode Method</span></span>

<span data-ttu-id="39c46-103">Получает информацию об управляемом коде по адресу определенного кода.</span><span class="sxs-lookup"><span data-stu-id="39c46-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c46-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39c46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c46-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="39c46-105">Parameters</span></span>  

 `codeAddress`  
 <span data-ttu-id="39c46-106">окне Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , указывающее начальный адрес сегмента управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="39c46-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="39c46-107">заполняет Указатель на адрес объекта ICorDebugCode, который представляет сегмент управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="39c46-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39c46-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="39c46-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c46-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="39c46-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c46-110">Требования</span><span class="sxs-lookup"><span data-stu-id="39c46-110">Requirements</span></span>  

 <span data-ttu-id="39c46-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39c46-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c46-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39c46-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39c46-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39c46-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39c46-114">**.NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c46-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c46-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="39c46-115">See also</span></span>

- [<span data-ttu-id="39c46-116">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="39c46-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="39c46-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="39c46-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
