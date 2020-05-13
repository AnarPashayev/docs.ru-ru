---
title: Метод ICorDebugModule::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212585"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="9a39e-102">Метод ICorDebugModule::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="9a39e-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9a39e-103">Возвращает функцию, заданную маркером метаданных.</span><span class="sxs-lookup"><span data-stu-id="9a39e-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a39e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a39e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a39e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9a39e-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="9a39e-106">окне `mdMethodDef`Токен метаданных, который ссылается на метаданные функции.</span><span class="sxs-lookup"><span data-stu-id="9a39e-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="9a39e-107">заполняет Указатель на адрес объекта интерфейса ICorDebugFunction, представляющего функцию.</span><span class="sxs-lookup"><span data-stu-id="9a39e-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a39e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a39e-108">Remarks</span></span>  
 <span data-ttu-id="9a39e-109">`GetFunctionFromToken`Метод возвращает CORDBG_E_FUNCTION_NOT_IL HRESULT, если переданное значение `methodDef` не ссылается на метод языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="9a39e-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a39e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="9a39e-110">Requirements</span></span>  
 <span data-ttu-id="9a39e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a39e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a39e-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a39e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a39e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a39e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a39e-114">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a39e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
