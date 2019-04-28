---
title: Метод IHostMemoryManager::VirtualQuery
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760107"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="8d39a-102">Метод IHostMemoryManager::VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="8d39a-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="8d39a-103">Служит в качестве логической программой-оболочкой для соответствующей функции Win32.</span><span class="sxs-lookup"><span data-stu-id="8d39a-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="8d39a-104">Реализация Win32 `VirtualQuery` извлекает сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="8d39a-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d39a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d39a-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d39a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d39a-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="8d39a-107">[in] Указатель на адрес в виртуальной памяти, должны запрашиваться.</span><span class="sxs-lookup"><span data-stu-id="8d39a-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="8d39a-108">[out] Указатель на структуру, содержащую сведения о регионе указанной области памяти.</span><span class="sxs-lookup"><span data-stu-id="8d39a-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8d39a-109">[in] Размер в байтах буфера, `lpBuffer` указывает.</span><span class="sxs-lookup"><span data-stu-id="8d39a-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="8d39a-110">[out] Указатель на число байтов, возвращенных в буфере сведения.</span><span class="sxs-lookup"><span data-stu-id="8d39a-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d39a-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8d39a-111">Return Value</span></span>  
  
|<span data-ttu-id="8d39a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d39a-112">HRESULT</span></span>|<span data-ttu-id="8d39a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="8d39a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d39a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d39a-114">S_OK</span></span>|<span data-ttu-id="8d39a-115">`VirtualQuery` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="8d39a-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="8d39a-116">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d39a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d39a-117">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8d39a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d39a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d39a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d39a-119">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="8d39a-119">The call timed out.</span></span>|  
|<span data-ttu-id="8d39a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d39a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d39a-121">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="8d39a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d39a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d39a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d39a-123">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="8d39a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d39a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d39a-124">E_FAIL</span></span>|<span data-ttu-id="8d39a-125">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="8d39a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d39a-126">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8d39a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d39a-127">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d39a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d39a-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="8d39a-128">Remarks</span></span>  
 <span data-ttu-id="8d39a-129">`VirtualQuery` сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="8d39a-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="8d39a-130">Эта реализация задает значение `pResult` параметр число байтов, возвращаемых в буфере сведения и возвращает значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8d39a-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="8d39a-131">В Win32 `VirtualQuery` функция, возвращаемое значение представляет размер буфера.</span><span class="sxs-lookup"><span data-stu-id="8d39a-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="8d39a-132">Дополнительные сведения см. в документации платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="8d39a-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d39a-133">Реализация операционной системы `VirtualQuery` не приводит к взаимоблокировке и выполняются до завершения с помощью случайной приостановки потоков в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="8d39a-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="8d39a-134">Используйте особую осторожность при реализации размещенных версия этого метода.</span><span class="sxs-lookup"><span data-stu-id="8d39a-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d39a-135">Требования</span><span class="sxs-lookup"><span data-stu-id="8d39a-135">Requirements</span></span>  
 <span data-ttu-id="8d39a-136">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d39a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d39a-137">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d39a-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d39a-138">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d39a-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d39a-139">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d39a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d39a-140">См. также</span><span class="sxs-lookup"><span data-stu-id="8d39a-140">See also</span></span>

- [<span data-ttu-id="8d39a-141">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="8d39a-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
