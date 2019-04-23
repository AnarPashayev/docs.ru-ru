---
title: Метод ICorDebugManagedCallback3::CustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193581"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="45f5e-102">Метод ICorDebugManagedCallback3::CustomNotification</span><span class="sxs-lookup"><span data-stu-id="45f5e-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="45f5e-103">Указывает, что пользовательское уведомление отладчика.</span><span class="sxs-lookup"><span data-stu-id="45f5e-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f5e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45f5e-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45f5e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="45f5e-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="45f5e-106">[in] Указатель на поток, вызвавший уведомление.</span><span class="sxs-lookup"><span data-stu-id="45f5e-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="45f5e-107">[in] Указатель на домен приложения, который содержит потока, который вызвал уведомление.</span><span class="sxs-lookup"><span data-stu-id="45f5e-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45f5e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="45f5e-108">Return Value</span></span>  
 <span data-ttu-id="45f5e-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="45f5e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="45f5e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45f5e-110">HRESULT</span></span>|<span data-ttu-id="45f5e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="45f5e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45f5e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="45f5e-112">S_OK</span></span>|<span data-ttu-id="45f5e-113">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="45f5e-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="45f5e-114">Исключения</span><span class="sxs-lookup"><span data-stu-id="45f5e-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f5e-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="45f5e-115">Remarks</span></span>  
 <span data-ttu-id="45f5e-116">Последующий вызов [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) метод извлекает объект потока, который был передан <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="45f5e-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="45f5e-117">Тип объекта потока необходимо предварительно включить путем вызова [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="45f5e-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="45f5e-118">Отладчик может считывать параметры конкретного типа поля объекта потока и сохранять ответы в поля.</span><span class="sxs-lookup"><span data-stu-id="45f5e-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="45f5e-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) интерфейс применяет политика, не о типах уведомлений или их содержимое, а семантика уведомлений определяется исключительно контракт между отладчики, приложения и платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45f5e-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45f5e-120">Требования</span><span class="sxs-lookup"><span data-stu-id="45f5e-120">Requirements</span></span>  
 <span data-ttu-id="45f5e-121">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45f5e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45f5e-122">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45f5e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45f5e-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45f5e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45f5e-124">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f5e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f5e-125">См. также</span><span class="sxs-lookup"><span data-stu-id="45f5e-125">See also</span></span>

- [<span data-ttu-id="45f5e-126">Интерфейс ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="45f5e-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="45f5e-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="45f5e-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="45f5e-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="45f5e-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
