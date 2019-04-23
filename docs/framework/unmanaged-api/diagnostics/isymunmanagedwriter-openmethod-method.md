---
title: Метод ISymUnmanagedWriter::OpenMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194790"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="a939b-102">Метод ISymUnmanagedWriter::OpenMethod</span><span class="sxs-lookup"><span data-stu-id="a939b-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="a939b-103">Открывает метод в символ, который создается сведения.</span><span class="sxs-lookup"><span data-stu-id="a939b-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="a939b-104">Данный метод становится текущим методом для вызовов с целью определения точек следования, параметров и лексические области.</span><span class="sxs-lookup"><span data-stu-id="a939b-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="a939b-105">Нет неявную лексическую область вокруг весь метод.</span><span class="sxs-lookup"><span data-stu-id="a939b-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="a939b-106">Повторное открытие метода, которое было ранее закрыто приведет к удалению всех ранее определенных символов для этого метода.</span><span class="sxs-lookup"><span data-stu-id="a939b-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="a939b-107">Одновременно может существовать только один метод open.</span><span class="sxs-lookup"><span data-stu-id="a939b-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a939b-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a939b-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a939b-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="a939b-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="a939b-110">[in] Токен метаданных для открываемого метода.</span><span class="sxs-lookup"><span data-stu-id="a939b-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a939b-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a939b-111">Return Value</span></span>  
 <span data-ttu-id="a939b-112">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="a939b-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a939b-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a939b-113">Requirements</span></span>  
 <span data-ttu-id="a939b-114">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a939b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a939b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a939b-115">See also</span></span>

- [<span data-ttu-id="a939b-116">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="a939b-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a939b-117">Метод CloseMethod</span><span class="sxs-lookup"><span data-stu-id="a939b-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="a939b-118">Метод OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="a939b-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
