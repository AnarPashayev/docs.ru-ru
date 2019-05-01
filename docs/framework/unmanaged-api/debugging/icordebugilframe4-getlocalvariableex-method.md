---
title: Метод ICorDebugILFrame4::GetLocalVariableEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6594bb72ce9cd2fbfa9cdafebc152a90618b810
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995492"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="78525-102">Метод ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="78525-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="78525-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="78525-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="78525-104">Получает значение указанной локальной переменной в этом кадре стека промежуточного языка (IL) и дополнительно получает доступ к переменной, добавленной в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="78525-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78525-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78525-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78525-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="78525-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="78525-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) член перечисления, указывающее, включается ли в кадр переменная, добавленная в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="78525-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="78525-108">[в] Индекс локальной переменной в кадре стека промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="78525-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="78525-109">[out] Указатель на адрес объекта «ICorDebugValue», представляющего извлеченное значение.</span><span class="sxs-lookup"><span data-stu-id="78525-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78525-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="78525-110">Remarks</span></span>  
 <span data-ttu-id="78525-111">Этот метод аналогичен методу [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) за тем исключением, что он дополнительно получает доступ к переменной, добавленной в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="78525-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="78525-112">Вызов этого метода с `flags` значение `ILCODE_ORIGINAL_IL` эквивалентно вызову [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Если этот метод инструментирован с дополнительными локальными переменными, эти переменные не доступны.</span><span class="sxs-lookup"><span data-stu-id="78525-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="78525-113">`ILCODE_REJIT_IL` обеспечивает отладчику доступ к локальным переменным, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="78525-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="78525-114">Если промежуточный язык не инструментирован, метод возвращает значение `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="78525-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78525-115">Требования</span><span class="sxs-lookup"><span data-stu-id="78525-115">Requirements</span></span>  
 <span data-ttu-id="78525-116">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78525-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78525-117">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78525-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78525-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78525-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78525-119">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78525-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78525-120">См. также</span><span class="sxs-lookup"><span data-stu-id="78525-120">See also</span></span>

- [<span data-ttu-id="78525-121">Интерфейс ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="78525-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="78525-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="78525-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="78525-123">ReJIT: Практическое руководство</span><span class="sxs-lookup"><span data-stu-id="78525-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
