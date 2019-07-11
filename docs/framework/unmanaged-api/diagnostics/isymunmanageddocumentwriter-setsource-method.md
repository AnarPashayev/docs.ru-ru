---
title: Метод ISymUnmanagedDocumentWriter::SetSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 555926e0e6a669f70bdeff484cff0eb62ae11f7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776937"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="a8882-102">Метод ISymUnmanagedDocumentWriter::SetSource</span><span class="sxs-lookup"><span data-stu-id="a8882-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="a8882-103">Устанавливает внедренный источник документа, который выполняется запись.</span><span class="sxs-lookup"><span data-stu-id="a8882-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8882-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8882-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8882-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a8882-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="a8882-106">[in] Объект `ULONG32` , содержащий размер `source` буфера.</span><span class="sxs-lookup"><span data-stu-id="a8882-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="a8882-107">[in] Буфер, который хранит внедренного источника.</span><span class="sxs-lookup"><span data-stu-id="a8882-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8882-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a8882-108">Return Value</span></span>  
 <span data-ttu-id="a8882-109">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="a8882-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8882-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a8882-110">Requirements</span></span>  
 <span data-ttu-id="a8882-111">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a8882-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8882-112">См. также</span><span class="sxs-lookup"><span data-stu-id="a8882-112">See also</span></span>

- [<span data-ttu-id="a8882-113">Интерфейс ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="a8882-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
