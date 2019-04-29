---
title: Метод ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937180"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="16187-102">Метод ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="16187-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="16187-103">Определяет, сохраняет ли компилятор just-in-time (JIT) сведения об отладке для методов в данном модуле.</span><span class="sxs-lookup"><span data-stu-id="16187-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16187-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16187-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16187-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="16187-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="16187-106">[in] Это значение равно `true` для включения JIT-компилятор для сохранения сведений о сопоставлении между версией Microsoft промежуточного языка MSIL и версии JIT-компиляции каждого метода в данном модуле.</span><span class="sxs-lookup"><span data-stu-id="16187-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="16187-107">[in] Это значение равно `true` для включения JIT-компилятор для создания кода с помощью определенных реализаций определенных JIT-компилятора для отладки.</span><span class="sxs-lookup"><span data-stu-id="16187-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16187-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="16187-108">Remarks</span></span>  
 <span data-ttu-id="16187-109">JIT-отладка включена по умолчанию для всех модулей, загруженных при активном отладчике.</span><span class="sxs-lookup"><span data-stu-id="16187-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="16187-110">Программное Включение или отключение параметров переопределяет глобальные параметры.</span><span class="sxs-lookup"><span data-stu-id="16187-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16187-111">Требования</span><span class="sxs-lookup"><span data-stu-id="16187-111">Requirements</span></span>  
 <span data-ttu-id="16187-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16187-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16187-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16187-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16187-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16187-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16187-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16187-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
