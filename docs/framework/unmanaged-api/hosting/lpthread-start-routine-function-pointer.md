---
title: Указатель функции LPTHREAD_START_ROUTINE
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d1837f9f9f11ad34140f50ec41aa6fe8a62160
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765249"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="48319-102">Указатель функции LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="48319-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="48319-103">Указывает на функцию, которая уведомляет основное приложение, который запущен поток для выполнения.</span><span class="sxs-lookup"><span data-stu-id="48319-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="48319-104">Этот указатель функции был объявлен устаревшим в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48319-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48319-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48319-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48319-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="48319-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="48319-107">[in] Указатель на код, который начато выполнение.</span><span class="sxs-lookup"><span data-stu-id="48319-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48319-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="48319-108">Remarks</span></span>  
 <span data-ttu-id="48319-109">Функция, которая `LPTHREAD_START_ROUTINE` точки — это функция обратного вызова и должны быть реализованы модулем записи ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="48319-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48319-110">Требования</span><span class="sxs-lookup"><span data-stu-id="48319-110">Requirements</span></span>  
 <span data-ttu-id="48319-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48319-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48319-112">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48319-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48319-113">**Библиотека:** "Mscorwks.dll"</span><span class="sxs-lookup"><span data-stu-id="48319-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="48319-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48319-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48319-115">См. также</span><span class="sxs-lookup"><span data-stu-id="48319-115">See also</span></span>

- [<span data-ttu-id="48319-116">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="48319-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
