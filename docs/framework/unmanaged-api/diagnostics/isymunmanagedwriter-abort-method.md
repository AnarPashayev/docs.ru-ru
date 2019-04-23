---
title: Метод ISymUnmanagedWriter::Abort
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 090183cad17aff6faf5e79639eadff086c1a26ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119539"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="ee064-102">Метод ISymUnmanagedWriter::Abort</span><span class="sxs-lookup"><span data-stu-id="ee064-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="ee064-103">Закрывает средство записи символов без передачи символов в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="ee064-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="ee064-104">После этого вызова модуля записи символов становится недействительным для дальнейших обновлений.</span><span class="sxs-lookup"><span data-stu-id="ee064-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="ee064-105">Чтобы зафиксировать символы и закрыть модуль записи символов, используйте [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="ee064-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee064-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee064-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ee064-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ee064-107">Return Value</span></span>  
 <span data-ttu-id="ee064-108">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="ee064-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee064-109">Требования</span><span class="sxs-lookup"><span data-stu-id="ee064-109">Requirements</span></span>  
 <span data-ttu-id="ee064-110">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ee064-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee064-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ee064-111">See also</span></span>

- [<span data-ttu-id="ee064-112">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="ee064-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
