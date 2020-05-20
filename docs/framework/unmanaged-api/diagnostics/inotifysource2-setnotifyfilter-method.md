---
title: Метод INotifySource2::SetNotifyFilter
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441972"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="d1ffb-102">Метод INotifySource2::SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="d1ffb-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="d1ffb-103">Назначает фильтр уведомлений для использования с этим источником.</span><span class="sxs-lookup"><span data-stu-id="d1ffb-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ffb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d1ffb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1ffb-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d1ffb-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="d1ffb-106">окне Побитовое сочетание значений перечисления [NOTIFY_FILTER](notify-filter-enumeration.md) , которые указывают обратные вызовы для API отладчика.</span><span class="sxs-lookup"><span data-stu-id="d1ffb-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="d1ffb-107">окне Указатель на структуру [USER_THREAD](user-thread-structure.md) , которая идентифицирует потоки для API отладчика.</span><span class="sxs-lookup"><span data-stu-id="d1ffb-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1ffb-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d1ffb-108">Return Value</span></span>  
 <span data-ttu-id="d1ffb-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="d1ffb-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ffb-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d1ffb-110">Requirements</span></span>  
 <span data-ttu-id="d1ffb-111">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="d1ffb-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ffb-112">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="d1ffb-112">See also</span></span>

- [<span data-ttu-id="d1ffb-113">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="d1ffb-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="d1ffb-114">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="d1ffb-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="d1ffb-115">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="d1ffb-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
