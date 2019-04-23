---
title: Метод ICorDebugRemoteTarget::GetHostName
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca7aee79b5b8c3d58b4beb8f1ff886a7d55afab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127586"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="34c9b-102">Метод ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="34c9b-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="34c9b-103">Возвращает полное доменное имя или IPv4-адрес удаленной отладки целевой машины.</span><span class="sxs-lookup"><span data-stu-id="34c9b-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="34c9b-104">IPv6 не поддерживается в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="34c9b-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c9b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="34c9b-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="34c9b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="34c9b-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="34c9b-107">[in] Размер в символах, из `szHostName` буфера.</span><span class="sxs-lookup"><span data-stu-id="34c9b-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="34c9b-108">Если этот параметр равен 0 (ноль), `szHostName` должен иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="34c9b-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="34c9b-109">[out] Число символов, включая завершающий нуль-символ, имя узла или IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="34c9b-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="34c9b-110">Этот параметр может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="34c9b-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="34c9b-111">[out] Буфер, содержащий имя узла или IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="34c9b-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34c9b-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="34c9b-112">Return Value</span></span>  
 <span data-ttu-id="34c9b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="34c9b-113">S_OK</span></span>  
 <span data-ttu-id="34c9b-114">Имя узла или IP-адрес был успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="34c9b-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="34c9b-115">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="34c9b-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="34c9b-116">Не удалось получить имя узла или IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="34c9b-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34c9b-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="34c9b-117">Remarks</span></span>  
 <span data-ttu-id="34c9b-118">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="34c9b-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="34c9b-119">Он должен соответствовать несколько парадигма вызова: При первом вызове, вызывающий объект передает null в оба `cchHostName` и `szHostName`, и `pcchHostName` возвращает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="34c9b-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="34c9b-120">При втором вызове, переданный размер, который был ранее возвращен `cchHostName`, и переданный буфера `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="34c9b-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c9b-121">Требования</span><span class="sxs-lookup"><span data-stu-id="34c9b-121">Requirements</span></span>  
 <span data-ttu-id="34c9b-122">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c9b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c9b-123">**Заголовок.** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="34c9b-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="34c9b-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34c9b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c9b-125">**Версии платформы .NET framework:** 3.5 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="34c9b-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c9b-126">См. также</span><span class="sxs-lookup"><span data-stu-id="34c9b-126">See also</span></span>

- [<span data-ttu-id="34c9b-127">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="34c9b-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="34c9b-128">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="34c9b-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
