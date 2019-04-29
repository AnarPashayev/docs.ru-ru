---
title: Интерфейс ICorDebugRemote
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a50a799c625c647aa275994bc92738b8a4267eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782724"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="7e644-102">Интерфейс ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="7e644-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="7e644-103">Позволяет запускать или подключать управляемый отладчик к удаленному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="7e644-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e644-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7e644-104">Syntax</span></span>  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7e644-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7e644-105">Methods</span></span>  
  
|<span data-ttu-id="7e644-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7e644-106">Method</span></span>|<span data-ttu-id="7e644-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7e644-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e644-108">Метод ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="7e644-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="7e644-109">Создает процесс на удаленном компьютере, для отладки управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="7e644-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="7e644-110">Метод ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="7e644-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="7e644-111">Запускает процесс на удаленном компьютере в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="7e644-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e644-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="7e644-112">Remarks</span></span>  
 <span data-ttu-id="7e644-113">В настоящее время эта функция поддерживается только для отладки приложения на основе Silverlight целевой объект, который выполняется на удаленном компьютере Macintosh.</span><span class="sxs-lookup"><span data-stu-id="7e644-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e644-114">Требования</span><span class="sxs-lookup"><span data-stu-id="7e644-114">Requirements</span></span>  
 <span data-ttu-id="7e644-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e644-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e644-116">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e644-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e644-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e644-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e644-118">**Версии платформы .NET framework:** 4.5, 4, 3.5 С ПАКЕТОМ ОБНОВЛЕНИЯ 1</span><span class="sxs-lookup"><span data-stu-id="7e644-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e644-119">См. также</span><span class="sxs-lookup"><span data-stu-id="7e644-119">See also</span></span>

- [<span data-ttu-id="7e644-120">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="7e644-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="7e644-121">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="7e644-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="7e644-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7e644-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
