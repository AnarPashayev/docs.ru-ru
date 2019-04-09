---
title: Перечисление LoggingLevelEnum
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086511"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="be31a-102">Перечисление LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="be31a-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="be31a-103">Указывает уровень важности описательного сообщения, записанного в журнале событий при регистрации события управляемым потоком.</span><span class="sxs-lookup"><span data-stu-id="be31a-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be31a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be31a-104">Syntax</span></span>  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="be31a-105">Участники</span><span class="sxs-lookup"><span data-stu-id="be31a-105">Members</span></span>  
  
|<span data-ttu-id="be31a-106">Член</span><span class="sxs-lookup"><span data-stu-id="be31a-106">Member</span></span>|<span data-ttu-id="be31a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="be31a-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="be31a-108">Сообщение является уровень трассировки 0.</span><span class="sxs-lookup"><span data-stu-id="be31a-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="be31a-109">Сообщение является уровень трассировки 1.</span><span class="sxs-lookup"><span data-stu-id="be31a-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="be31a-110">Сообщение является уровень трассировки 2.</span><span class="sxs-lookup"><span data-stu-id="be31a-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="be31a-111">Сообщение является уровень трассировки 3.</span><span class="sxs-lookup"><span data-stu-id="be31a-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="be31a-112">Сообщение является уровень трассировки 4.</span><span class="sxs-lookup"><span data-stu-id="be31a-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="be31a-113">Сообщение является уровнем состояние 0.</span><span class="sxs-lookup"><span data-stu-id="be31a-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="be31a-114">Сообщение является уровнем состояние 1.</span><span class="sxs-lookup"><span data-stu-id="be31a-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="be31a-115">Сообщение является уровнем состояние 2.</span><span class="sxs-lookup"><span data-stu-id="be31a-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="be31a-116">Сообщение является уровнем состояние 3.</span><span class="sxs-lookup"><span data-stu-id="be31a-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="be31a-117">Сообщение является уровнем состояние 4.</span><span class="sxs-lookup"><span data-stu-id="be31a-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="be31a-118">Сообщение является уровень предупреждений.</span><span class="sxs-lookup"><span data-stu-id="be31a-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="be31a-119">Сообщение находится на уровне ошибки.</span><span class="sxs-lookup"><span data-stu-id="be31a-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="be31a-120">Сообщение находится на уровне тревоги.</span><span class="sxs-lookup"><span data-stu-id="be31a-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be31a-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="be31a-121">Remarks</span></span>  
 <span data-ttu-id="be31a-122">Общеязыковая среда выполнения (CLR) вызывает [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) метод для уведомления отладчик о том, что управляемый поток выполнил событие.</span><span class="sxs-lookup"><span data-stu-id="be31a-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="be31a-123">Среда CLR передает значение `LoggingLevelEnum` перечисление, чтобы указать уровень серьезности сообщения, которое написал управляемый поток в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="be31a-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be31a-124">Требования</span><span class="sxs-lookup"><span data-stu-id="be31a-124">Requirements</span></span>  
 <span data-ttu-id="be31a-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be31a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be31a-126">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be31a-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be31a-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be31a-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="be31a-128">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="be31a-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be31a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="be31a-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="be31a-130">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="be31a-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
