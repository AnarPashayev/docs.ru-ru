---
title: Метод ISymUnmanagedWriter3::OpenMethod2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3dcb1327ad50761a8268e8adc7b1e976cae0b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200302"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="b35f9-102">Метод ISymUnmanagedWriter3::OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="b35f9-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="b35f9-103">Открывает метод и предоставляет его фактическое смещение раздела в образе.</span><span class="sxs-lookup"><span data-stu-id="b35f9-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35f9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b35f9-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b35f9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b35f9-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="b35f9-106">[in] Токен метаданных для открываемого метода.</span><span class="sxs-lookup"><span data-stu-id="b35f9-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="b35f9-107">[in] Смещение раздела в образе.</span><span class="sxs-lookup"><span data-stu-id="b35f9-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="b35f9-108">[in] Смещение в образе.</span><span class="sxs-lookup"><span data-stu-id="b35f9-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b35f9-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b35f9-109">Return Value</span></span>  
 <span data-ttu-id="b35f9-110">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="b35f9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b35f9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b35f9-111">Requirements</span></span>  
 <span data-ttu-id="b35f9-112">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b35f9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35f9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b35f9-113">See also</span></span>

- [<span data-ttu-id="b35f9-114">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="b35f9-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="b35f9-115">Метод OpenMethod</span><span class="sxs-lookup"><span data-stu-id="b35f9-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
