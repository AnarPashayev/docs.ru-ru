---
title: Метод ISymUnmanagedScope::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2c64d7ead2f7ce3d76b40f4fdc604506ee85561
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777892"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="cbad2-102">Метод ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="cbad2-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="cbad2-103">Получает пространства имен, используемые в этой области.</span><span class="sxs-lookup"><span data-stu-id="cbad2-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbad2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbad2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbad2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="cbad2-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="cbad2-106">[in] Размер массива `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="cbad2-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="cbad2-107">[out] Указатель на `ULONG32` , получающий размер буфера, необходимый для пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cbad2-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="cbad2-108">[out] Массив, получающий пространства имен.</span><span class="sxs-lookup"><span data-stu-id="cbad2-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbad2-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cbad2-109">Return Value</span></span>  
 <span data-ttu-id="cbad2-110">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="cbad2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbad2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="cbad2-111">Requirements</span></span>  
 <span data-ttu-id="cbad2-112">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cbad2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbad2-113">См. также</span><span class="sxs-lookup"><span data-stu-id="cbad2-113">See also</span></span>

- [<span data-ttu-id="cbad2-114">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="cbad2-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
