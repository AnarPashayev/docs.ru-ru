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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790095"
---
# <a name="closeassembly-method"></a><span data-ttu-id="7133b-102">Метод CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="7133b-102">CloseAssembly Method</span></span>
<span data-ttu-id="7133b-103">Завершает операции сборки.</span><span class="sxs-lookup"><span data-stu-id="7133b-103">Finalizes assembly operations.</span></span> <span data-ttu-id="7133b-104">Этот метод вызывается перед началом новой сборки или модуля, не связанного с данными.</span><span class="sxs-lookup"><span data-stu-id="7133b-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7133b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7133b-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7133b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7133b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7133b-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="7133b-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7133b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7133b-108">Return Value</span></span>  
 <span data-ttu-id="7133b-109">Возвращает S_OK, если метод выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="7133b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7133b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7133b-110">Requirements</span></span>  
 <span data-ttu-id="7133b-111">Требуется alink.h.</span><span class="sxs-lookup"><span data-stu-id="7133b-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7133b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="7133b-112">See also</span></span>

- [<span data-ttu-id="7133b-113">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="7133b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7133b-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="7133b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7133b-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="7133b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
