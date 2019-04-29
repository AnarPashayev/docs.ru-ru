---
title: Метод ICorDebugEval2::NewParameterizedObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6feef7b1e1f09107cd2a57555df07bebec86effa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667032"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="6b117-102">Метод ICorDebugEval2::NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="6b117-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="6b117-103">Создает новый объект параметризованного типа указанного класса не пытается вызвать метод-конструктор.</span><span class="sxs-lookup"><span data-stu-id="6b117-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b117-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b117-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b117-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6b117-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="6b117-106">[in] Указатель на объект ICorDebugClass, который представляет класс для создания экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6b117-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="6b117-107">[in] Передано число аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="6b117-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="6b117-108">[in] Массив указателей, каждый из которых указывает на объект, представляющий аргумент типа для объекта, экземпляр которого создается ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="6b117-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b117-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="6b117-109">Remarks</span></span>  
 <span data-ttu-id="6b117-110">`NewParameterizedObjectNoConstructor` Метод завершится ошибкой, если неверное число аргументов типа, или неправильный типы аргументов типа передаются.</span><span class="sxs-lookup"><span data-stu-id="6b117-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b117-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6b117-111">Requirements</span></span>  
 <span data-ttu-id="6b117-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b117-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b117-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b117-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b117-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b117-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b117-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b117-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
