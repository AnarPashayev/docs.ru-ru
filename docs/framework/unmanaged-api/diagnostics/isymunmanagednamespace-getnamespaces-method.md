---
title: Метод ISymUnmanagedNamespace::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: 48c50ac6be6d525676d85578e5a55a27104c180a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615102"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="74eef-102">Метод ISymUnmanagedNamespace::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="74eef-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="74eef-103">Возвращает дочерние элементы этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="74eef-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74eef-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74eef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74eef-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="74eef-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="74eef-106">окне Значение типа `ULONG32` , указывающее размер `namespaces` массива.</span><span class="sxs-lookup"><span data-stu-id="74eef-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="74eef-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимого для хранения пространств имен.</span><span class="sxs-lookup"><span data-stu-id="74eef-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="74eef-108">заполняет Указатель на буфер, содержащий пространства имен.</span><span class="sxs-lookup"><span data-stu-id="74eef-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74eef-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="74eef-109">Return Value</span></span>  
 <span data-ttu-id="74eef-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="74eef-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74eef-111">Требования</span><span class="sxs-lookup"><span data-stu-id="74eef-111">Requirements</span></span>  
 <span data-ttu-id="74eef-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="74eef-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74eef-113">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="74eef-113">See also</span></span>

- [<span data-ttu-id="74eef-114">Интерфейс ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="74eef-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
