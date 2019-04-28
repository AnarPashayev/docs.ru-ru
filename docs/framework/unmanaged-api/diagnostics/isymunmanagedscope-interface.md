---
title: Интерфейс ISymUnmanagedScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809368ea19528a7ce00d4fcada06ef5724eb79a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761641"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="8937c-102">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="8937c-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="8937c-103">Представляет лексическую область внутри метода.</span><span class="sxs-lookup"><span data-stu-id="8937c-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8937c-104">Методы</span><span class="sxs-lookup"><span data-stu-id="8937c-104">Methods</span></span>  
  
|<span data-ttu-id="8937c-105">Метод</span><span class="sxs-lookup"><span data-stu-id="8937c-105">Method</span></span>|<span data-ttu-id="8937c-106">Описание</span><span class="sxs-lookup"><span data-stu-id="8937c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8937c-107">Метод GetChildren</span><span class="sxs-lookup"><span data-stu-id="8937c-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="8937c-108">Возвращает дочерние элементы данной области.</span><span class="sxs-lookup"><span data-stu-id="8937c-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="8937c-109">Метод GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="8937c-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="8937c-110">Возвращает конечное смещение для этой области.</span><span class="sxs-lookup"><span data-stu-id="8937c-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="8937c-111">Метод GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="8937c-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="8937c-112">Возвращает число локальных переменных, определенных в данной области.</span><span class="sxs-lookup"><span data-stu-id="8937c-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="8937c-113">Метод GetLocals</span><span class="sxs-lookup"><span data-stu-id="8937c-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="8937c-114">Возвращает локальные переменные, определенные в этой области.</span><span class="sxs-lookup"><span data-stu-id="8937c-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="8937c-115">Метод GetMethod</span><span class="sxs-lookup"><span data-stu-id="8937c-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="8937c-116">Возвращает метод, который содержит эту область.</span><span class="sxs-lookup"><span data-stu-id="8937c-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="8937c-117">Метод GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="8937c-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="8937c-118">Получает пространства имен, используемые в этой области.</span><span class="sxs-lookup"><span data-stu-id="8937c-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="8937c-119">Метод GetParent</span><span class="sxs-lookup"><span data-stu-id="8937c-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="8937c-120">Получает родительскую область этой области.</span><span class="sxs-lookup"><span data-stu-id="8937c-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="8937c-121">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="8937c-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="8937c-122">Возвращает начальное смещение для этой области.</span><span class="sxs-lookup"><span data-stu-id="8937c-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8937c-123">Требования</span><span class="sxs-lookup"><span data-stu-id="8937c-123">Requirements</span></span>  
 <span data-ttu-id="8937c-124">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8937c-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8937c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="8937c-125">See also</span></span>

- [<span data-ttu-id="8937c-126">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="8937c-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8937c-127">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="8937c-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
