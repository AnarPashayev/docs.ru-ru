---
title: Метод ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c73889a6daaa50d1694e786c78f50d0e87644967
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750426"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="be6c0-102">Метод ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="be6c0-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="be6c0-103">Уведомляет профилировщик, что процесс завершил обработку запроса вызова удаленного метода и собирается передачи ответа по каналу.</span><span class="sxs-lookup"><span data-stu-id="be6c0-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be6c0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be6c0-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be6c0-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="be6c0-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="be6c0-106">[in] Указатель на идентификатор GUID, которое соответствует значение, указанное в [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) в этих условиях:</span><span class="sxs-lookup"><span data-stu-id="be6c0-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="be6c0-107">Файлы cookie для GUID удаленного взаимодействия активны.</span><span class="sxs-lookup"><span data-stu-id="be6c0-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="be6c0-108">Каналу удалось передать сообщение.</span><span class="sxs-lookup"><span data-stu-id="be6c0-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="be6c0-109">Файлы cookie GUID активны на процесс на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="be6c0-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="be6c0-110">Это позволяет легко создавать пары вызовов удаленного взаимодействия и Создание логического стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="be6c0-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="be6c0-111">[in] Значение, которое является `true` Если вызов выполняется асинхронно; в противном случае — значение `false`.</span><span class="sxs-lookup"><span data-stu-id="be6c0-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be6c0-112">Требования</span><span class="sxs-lookup"><span data-stu-id="be6c0-112">Requirements</span></span>  
 <span data-ttu-id="be6c0-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be6c0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be6c0-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be6c0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be6c0-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be6c0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be6c0-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be6c0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6c0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="be6c0-117">See also</span></span>

- [<span data-ttu-id="be6c0-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="be6c0-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
