---
title: Метод ISymUnmanagedVariable::GetAddressKind
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eae5b21af3bcdca911ec13067a61bb957d4ae6ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797583"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="a6b8e-102">Метод ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="a6b8e-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="a6b8e-103">Возвращает вид адрес этой переменной.</span><span class="sxs-lookup"><span data-stu-id="a6b8e-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b8e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6b8e-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6b8e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6b8e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a6b8e-106">[out] Указатель на `ULONG32` , получающий значение.</span><span class="sxs-lookup"><span data-stu-id="a6b8e-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="a6b8e-107">Возможные значения определяются в [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="a6b8e-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6b8e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a6b8e-108">Return Value</span></span>  
 <span data-ttu-id="a6b8e-109">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="a6b8e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b8e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a6b8e-110">Requirements</span></span>  
 <span data-ttu-id="a6b8e-111">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a6b8e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b8e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="a6b8e-112">See also</span></span>

- [<span data-ttu-id="a6b8e-113">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="a6b8e-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
