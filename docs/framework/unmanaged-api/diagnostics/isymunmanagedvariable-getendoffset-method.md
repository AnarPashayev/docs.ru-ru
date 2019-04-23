---
title: Метод ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 325db05cc322d85e836ca9ba62b6a169e8965241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220959"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="28a7e-102">Метод ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="28a7e-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="28a7e-103">Возвращает конечное смещение переменной внутри родительского.</span><span class="sxs-lookup"><span data-stu-id="28a7e-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="28a7e-104">Если это локальной переменной в области, конечное смещение выходит в границах смещений, определенных для данной области.</span><span class="sxs-lookup"><span data-stu-id="28a7e-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a7e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28a7e-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28a7e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="28a7e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="28a7e-107">[out] Указатель на `ULONG32` , который получает конечное смещение.</span><span class="sxs-lookup"><span data-stu-id="28a7e-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28a7e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="28a7e-108">Return Value</span></span>  
 <span data-ttu-id="28a7e-109">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="28a7e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28a7e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="28a7e-110">Requirements</span></span>  
 <span data-ttu-id="28a7e-111">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28a7e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a7e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="28a7e-112">See also</span></span>

- [<span data-ttu-id="28a7e-113">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="28a7e-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="28a7e-114">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="28a7e-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
