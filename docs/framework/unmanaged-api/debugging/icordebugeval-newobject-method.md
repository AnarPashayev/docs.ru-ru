---
title: Метод ICorDebugEval::NewObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: e9570d3c916123093f69e7f26d3778f1c7184b1f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976191"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="29335-102">Метод ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="29335-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="29335-103">Выделяет новый экземпляр объекта и вызывает указанный метод конструктора.</span><span class="sxs-lookup"><span data-stu-id="29335-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="29335-104">Этот метод является устаревшим в .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="29335-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="29335-105">Вместо этого используйте [ICorDebugEval2:: невпараметеризедобжект](icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="29335-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29335-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="29335-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29335-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="29335-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="29335-108">окне Вызываемый конструктор.</span><span class="sxs-lookup"><span data-stu-id="29335-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="29335-109">[in] Размер массива `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="29335-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="29335-110">окне Массив объектов ICorDebugValue, каждый из которых представляет аргумент, передаваемый конструктору.</span><span class="sxs-lookup"><span data-stu-id="29335-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29335-111">Требования</span><span class="sxs-lookup"><span data-stu-id="29335-111">Requirements</span></span>  
 <span data-ttu-id="29335-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29335-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29335-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29335-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29335-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29335-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29335-115">**.NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="29335-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29335-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="29335-116">See also</span></span>

- [<span data-ttu-id="29335-117">Метод NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="29335-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
