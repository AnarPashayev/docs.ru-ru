---
title: Метод ICorDebugILFrame::GetArgument
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995531"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="a58a9-102">Метод ICorDebugILFrame::GetArgument</span><span class="sxs-lookup"><span data-stu-id="a58a9-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="a58a9-103">Получает значение указанного аргумента в кадре стека промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="a58a9-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58a9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a58a9-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a58a9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a58a9-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a58a9-106">[in] Индекс аргумента в кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="a58a9-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a58a9-107">[out] Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение.</span><span class="sxs-lookup"><span data-stu-id="a58a9-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a58a9-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="a58a9-108">Remarks</span></span>  
 <span data-ttu-id="a58a9-109">`GetArgument` Метод может использоваться в кадре стека MSIL или во фрейме скомпилированного just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="a58a9-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58a9-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a58a9-110">Requirements</span></span>  
 <span data-ttu-id="a58a9-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a58a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58a9-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a58a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a58a9-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58a9-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
