---
title: Метод ISymUnmanagedReader::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0c72cd6e7dce784064f7653ba35e488061d9fd7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773582"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="d7374-102">Метод ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="d7374-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="d7374-103">Получает пространства имен, определенные в глобальной области в данном хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="d7374-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7374-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7374-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7374-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7374-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="d7374-106">[in] Размер массива пространства имен.</span><span class="sxs-lookup"><span data-stu-id="d7374-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="d7374-107">[out] Указатель на переменную, которая получает длину списка пространств имен.</span><span class="sxs-lookup"><span data-stu-id="d7374-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="d7374-108">[out] Указатель на переменную, которая получает список имен.</span><span class="sxs-lookup"><span data-stu-id="d7374-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7374-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d7374-109">Return Value</span></span>  
 <span data-ttu-id="d7374-110">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="d7374-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7374-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d7374-111">Requirements</span></span>  
 <span data-ttu-id="d7374-112">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d7374-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7374-113">См. также</span><span class="sxs-lookup"><span data-stu-id="d7374-113">See also</span></span>

- [<span data-ttu-id="d7374-114">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="d7374-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
