---
title: Интерфейс ISymUnmanagedWriter3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614660"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="c6639-102">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="c6639-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="c6639-103">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="c6639-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c6639-104">Этот интерфейс расширяет интерфейс [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c6639-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6639-105">Методы</span><span class="sxs-lookup"><span data-stu-id="c6639-105">Methods</span></span>  
  
|<span data-ttu-id="c6639-106">Метод</span><span class="sxs-lookup"><span data-stu-id="c6639-106">Method</span></span>|<span data-ttu-id="c6639-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c6639-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6639-108">Метод Commit</span><span class="sxs-lookup"><span data-stu-id="c6639-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="c6639-109">Фиксирует изменения, записанные на данный момент в поток.</span><span class="sxs-lookup"><span data-stu-id="c6639-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="c6639-110">Метод OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="c6639-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="c6639-111">Открывает метод и предоставляет его фактическое смещение раздела в изображении.</span><span class="sxs-lookup"><span data-stu-id="c6639-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6639-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c6639-112">Requirements</span></span>  
 <span data-ttu-id="c6639-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="c6639-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6639-114">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="c6639-114">See also</span></span>

- [<span data-ttu-id="c6639-115">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="c6639-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c6639-116">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c6639-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c6639-117">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="c6639-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
