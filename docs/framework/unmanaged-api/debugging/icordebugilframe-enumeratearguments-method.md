---
title: Метод ICorDebugILFrame::EnumerateArguments
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 499f58cc0a3f2d1b3c159435ed7d9b523f25e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757890"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="a7785-102">Метод ICorDebugILFrame::EnumerateArguments</span><span class="sxs-lookup"><span data-stu-id="a7785-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="a7785-103">Получает перечислитель для аргументов в кадре.</span><span class="sxs-lookup"><span data-stu-id="a7785-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7785-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7785-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7785-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a7785-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="a7785-106">[out] Указатель на адрес объекта ICorDebugValueEnum, который является перечислителем для аргументов в кадре.</span><span class="sxs-lookup"><span data-stu-id="a7785-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7785-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="a7785-107">Remarks</span></span>  
 <span data-ttu-id="a7785-108">`EnumerateArguments` Возвращает перечислитель, который можно вывести список доступных в кадр вызова, который представлен этим объектом ICorDebugILFrame аргументов.</span><span class="sxs-lookup"><span data-stu-id="a7785-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="a7785-109">В списке будут содержаться аргументы, которые являются [vararg](/cpp/windows/vararg) (то есть несколько переменных аргументов) а также аргументы, которые не являются `vararg`.</span><span class="sxs-lookup"><span data-stu-id="a7785-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7785-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a7785-110">Requirements</span></span>  
 <span data-ttu-id="a7785-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7785-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7785-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7785-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7785-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7785-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7785-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7785-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
