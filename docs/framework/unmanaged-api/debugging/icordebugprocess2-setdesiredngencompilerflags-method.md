---
title: Метод ICorDebugProcess2::SetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 366a48e5f6abd92f0c6f796f40bdd263181da4a8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213482"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="eecdc-102">Метод ICorDebugProcess2::SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="eecdc-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="eecdc-103">Задает флаги, которые должны быть внедрены в предкомпилированное изображение, чтобы среда выполнения загружала этот образ в текущий процесс.</span><span class="sxs-lookup"><span data-stu-id="eecdc-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eecdc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eecdc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eecdc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="eecdc-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="eecdc-106">окне Значение перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) , указывающее флаги компилятора, используемые для выбора правильного предварительно скомпилированного изображения.</span><span class="sxs-lookup"><span data-stu-id="eecdc-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eecdc-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="eecdc-107">Remarks</span></span>  
 <span data-ttu-id="eecdc-108">`SetDesiredNGENCompilerFlags`Метод задает флаги, которые должны быть внедрены в предкомпилированное изображение, чтобы среда выполнения загружала этот образ в этот процесс.</span><span class="sxs-lookup"><span data-stu-id="eecdc-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="eecdc-109">Флаги, заданные этим методом, используются только для выбора правильного предкомпилированного изображения.</span><span class="sxs-lookup"><span data-stu-id="eecdc-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="eecdc-110">Если такого образа не существует, среда выполнения загрузит образ MSIL и JIT-компилятор, вместо этого.</span><span class="sxs-lookup"><span data-stu-id="eecdc-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="eecdc-111">В этом случае отладчик должен по-прежнему использовать метод [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) , чтобы установить флаги для JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="eecdc-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="eecdc-112">Если изображение загружено, но для этого образа необходимо выполнить некоторые JIT-компиляции (что будет так, если изображение содержит универсальные шаблоны), то флаги компилятора, заданные в `SetDesiredNGENCompilerFlags` методе, будут применяться к дополнительной JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="eecdc-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="eecdc-113">`SetDesiredNGENCompilerFlags`Метод должен вызываться во время обратного вызова [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eecdc-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="eecdc-114">Попытки вызвать `SetDesiredNGENCompilerFlags` метод позже завершатся ошибкой.</span><span class="sxs-lookup"><span data-stu-id="eecdc-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="eecdc-115">Кроме того, пытается установить флаги, которые либо не определены в `CorDebugJITCompilerFlags` перечислении, либо не являются допустимыми для данного процесса.</span><span class="sxs-lookup"><span data-stu-id="eecdc-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eecdc-116">Требования</span><span class="sxs-lookup"><span data-stu-id="eecdc-116">Requirements</span></span>  
 <span data-ttu-id="eecdc-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eecdc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eecdc-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eecdc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eecdc-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eecdc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eecdc-120">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eecdc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eecdc-121">См. также</span><span class="sxs-lookup"><span data-stu-id="eecdc-121">See also</span></span>

- [<span data-ttu-id="eecdc-122">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="eecdc-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="eecdc-123">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="eecdc-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
