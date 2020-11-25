---
title: Метод INotifyConnection2::UnregisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: 90220c2bfea683ff0472473e180c9e11ea568672
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720039"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="1ef3b-102">Метод INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="1ef3b-102">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="1ef3b-103">Удаляет указанный объект источника уведомления из соединения.</span><span class="sxs-lookup"><span data-stu-id="1ef3b-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef3b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ef3b-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef3b-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ef3b-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="1ef3b-106">окне Отменяется регистрация объекта уведомления.</span><span class="sxs-lookup"><span data-stu-id="1ef3b-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ef3b-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1ef3b-107">Return Value</span></span>  

 <span data-ttu-id="1ef3b-108">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="1ef3b-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef3b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="1ef3b-109">Requirements</span></span>  

 <span data-ttu-id="1ef3b-110">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="1ef3b-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef3b-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1ef3b-111">See also</span></span>

- [<span data-ttu-id="1ef3b-112">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="1ef3b-112">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="1ef3b-113">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="1ef3b-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="1ef3b-114">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="1ef3b-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="1ef3b-115">Метод RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="1ef3b-115">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
