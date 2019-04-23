---
title: Метод CloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94c1c083d010cd82fd9e9e2f02b23e81d88fedd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116445"
---
# <a name="closeassembly-method"></a><span data-ttu-id="f2f5e-102">Метод CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="f2f5e-102">CloseAssembly Method</span></span>
<span data-ttu-id="f2f5e-103">Завершает операции сборки.</span><span class="sxs-lookup"><span data-stu-id="f2f5e-103">Finalizes assembly operations.</span></span> <span data-ttu-id="f2f5e-104">Этот метод вызывается перед началом новой сборки или модуля, не связанного с данными.</span><span class="sxs-lookup"><span data-stu-id="f2f5e-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f5e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2f5e-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f5e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f2f5e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f2f5e-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="f2f5e-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2f5e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f2f5e-108">Return Value</span></span>  
 <span data-ttu-id="f2f5e-109">Возвращает S_OK, если метод выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="f2f5e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f5e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="f2f5e-110">Requirements</span></span>  
 <span data-ttu-id="f2f5e-111">Требуется alink.h.</span><span class="sxs-lookup"><span data-stu-id="f2f5e-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f5e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="f2f5e-112">See also</span></span>

- [<span data-ttu-id="f2f5e-113">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="f2f5e-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f2f5e-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="f2f5e-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f2f5e-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="f2f5e-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
