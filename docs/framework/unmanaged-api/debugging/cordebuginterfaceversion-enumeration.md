---
title: Перечисление CorDebugInterfaceVersion
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: cfdcfc69400fccf824d019f3904aeca76b6b37a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098130"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="12aed-102">Перечисление CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="12aed-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="12aed-103">Указывает интерфейс, версию платформы .NET Framework или версию платформы .NET Framework, в которой был представлен интерфейс.</span><span class="sxs-lookup"><span data-stu-id="12aed-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12aed-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12aed-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="12aed-105">Члены</span><span class="sxs-lookup"><span data-stu-id="12aed-105">Members</span></span>  
 <span data-ttu-id="12aed-106">В следующей таблице каждое значение перечисления сопоставляется с соответствующим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="12aed-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="12aed-107">Кроме того, в таблице указана первая версия платформы .NET Framework, в которой поддерживался интерфейс.</span><span class="sxs-lookup"><span data-stu-id="12aed-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="12aed-108">Член</span><span class="sxs-lookup"><span data-stu-id="12aed-108">Member</span></span>|<span data-ttu-id="12aed-109">Что определяет</span><span class="sxs-lookup"><span data-stu-id="12aed-109">Specifies</span></span>|<span data-ttu-id="12aed-110">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12aed-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="12aed-111">Недопустимая версия платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12aed-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="12aed-112">Версия платформы .NET Framework (включая все пакеты обновления) — 1.0.</span><span class="sxs-lookup"><span data-stu-id="12aed-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="12aed-113">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="12aed-114">Версия платформы .NET Framework (включая все пакеты обновления) — 1.1.</span><span class="sxs-lookup"><span data-stu-id="12aed-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="12aed-115">1.1</span><span class="sxs-lookup"><span data-stu-id="12aed-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="12aed-116">Версия платформы .NET Framework (включая все пакеты обновления) — 2.0.</span><span class="sxs-lookup"><span data-stu-id="12aed-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="12aed-117">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="12aed-118">Версия платформы .NET Framework (включая все пакеты обновления) — 4.</span><span class="sxs-lookup"><span data-stu-id="12aed-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="12aed-119">4</span><span class="sxs-lookup"><span data-stu-id="12aed-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="12aed-120">Версия платформы .NET Framework (включая все пакеты обновления) — 4.5.</span><span class="sxs-lookup"><span data-stu-id="12aed-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="12aed-121">4.5</span><span class="sxs-lookup"><span data-stu-id="12aed-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="12aed-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="12aed-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="12aed-123">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="12aed-124">икордебугунманажедкаллбакк</span><span class="sxs-lookup"><span data-stu-id="12aed-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="12aed-125">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="12aed-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="12aed-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="12aed-127">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="12aed-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="12aed-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="12aed-129">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="12aed-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="12aed-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="12aed-131">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="12aed-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="12aed-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="12aed-133">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="12aed-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="12aed-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="12aed-135">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="12aed-136">икордебугбреакпоинт</span><span class="sxs-lookup"><span data-stu-id="12aed-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="12aed-137">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="12aed-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="12aed-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="12aed-139">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="12aed-140">икордебугмодулебреакпоинт</span><span class="sxs-lookup"><span data-stu-id="12aed-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="12aed-141">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="12aed-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="12aed-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="12aed-143">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="12aed-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="12aed-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="12aed-145">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="12aed-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="12aed-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="12aed-147">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="12aed-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="12aed-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="12aed-149">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="12aed-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="12aed-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="12aed-151">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="12aed-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="12aed-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="12aed-153">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="12aed-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="12aed-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="12aed-155">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="12aed-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="12aed-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="12aed-157">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="12aed-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="12aed-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="12aed-159">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="12aed-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="12aed-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="12aed-161">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="12aed-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="12aed-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="12aed-163">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="12aed-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="12aed-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="12aed-165">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="12aed-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="12aed-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="12aed-167">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="12aed-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="12aed-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="12aed-169">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="12aed-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="12aed-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="12aed-171">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="12aed-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="12aed-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="12aed-173">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="12aed-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="12aed-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="12aed-175">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="12aed-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="12aed-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="12aed-177">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="12aed-178">икордебугбоксвалуе</span><span class="sxs-lookup"><span data-stu-id="12aed-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="12aed-179">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="12aed-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="12aed-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="12aed-181">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="12aed-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="12aed-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="12aed-183">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="12aed-184">икордебугконтекст</span><span class="sxs-lookup"><span data-stu-id="12aed-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="12aed-185">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="12aed-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="12aed-187">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="12aed-188">икордебугобжектенум</span><span class="sxs-lookup"><span data-stu-id="12aed-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="12aed-189">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="12aed-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="12aed-191">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="12aed-192">икордебугстепперенум</span><span class="sxs-lookup"><span data-stu-id="12aed-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="12aed-193">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="12aed-194">икордебугпроцессенум</span><span class="sxs-lookup"><span data-stu-id="12aed-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="12aed-195">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="12aed-196">икордебугсреаденум</span><span class="sxs-lookup"><span data-stu-id="12aed-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="12aed-197">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="12aed-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="12aed-199">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="12aed-200">икордебугчаиненум</span><span class="sxs-lookup"><span data-stu-id="12aed-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="12aed-201">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="12aed-202">икордебугмодулинум</span><span class="sxs-lookup"><span data-stu-id="12aed-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="12aed-203">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="12aed-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="12aed-205">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="12aed-206">икордебугкодинум</span><span class="sxs-lookup"><span data-stu-id="12aed-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="12aed-207">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="12aed-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="12aed-209">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="12aed-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="12aed-211">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="12aed-212">икордебугаппдомаиненум</span><span class="sxs-lookup"><span data-stu-id="12aed-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="12aed-213">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="12aed-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="12aed-215">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="12aed-216">икордебужедитандконтинуирроринфо</span><span class="sxs-lookup"><span data-stu-id="12aed-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="12aed-217">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="12aed-218">Метод icordebugeditandcontinuesnapshot</span><span class="sxs-lookup"><span data-stu-id="12aed-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="12aed-219">1,0</span><span class="sxs-lookup"><span data-stu-id="12aed-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="12aed-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="12aed-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="12aed-221">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="12aed-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="12aed-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="12aed-223">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="12aed-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="12aed-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="12aed-225">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="12aed-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="12aed-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="12aed-227">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="12aed-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="12aed-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="12aed-229">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="12aed-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="12aed-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="12aed-231">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="12aed-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="12aed-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="12aed-233">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="12aed-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="12aed-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="12aed-235">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="12aed-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="12aed-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="12aed-237">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="12aed-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="12aed-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="12aed-239">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="12aed-240">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="12aed-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="12aed-241">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="12aed-242">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="12aed-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="12aed-243">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="12aed-244">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="12aed-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="12aed-245">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="12aed-246">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="12aed-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="12aed-247">2.0</span><span class="sxs-lookup"><span data-stu-id="12aed-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="12aed-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="12aed-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="12aed-249">4</span><span class="sxs-lookup"><span data-stu-id="12aed-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="12aed-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="12aed-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="12aed-251">4</span><span class="sxs-lookup"><span data-stu-id="12aed-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="12aed-252">икордебугстакквалк</span><span class="sxs-lookup"><span data-stu-id="12aed-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="12aed-253">4</span><span class="sxs-lookup"><span data-stu-id="12aed-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="12aed-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="12aed-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="12aed-255">4</span><span class="sxs-lookup"><span data-stu-id="12aed-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="12aed-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="12aed-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="12aed-257">4</span><span class="sxs-lookup"><span data-stu-id="12aed-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="12aed-258">икордебугрунтимеунвиндаблефраме</span><span class="sxs-lookup"><span data-stu-id="12aed-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="12aed-259">4</span><span class="sxs-lookup"><span data-stu-id="12aed-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="12aed-260">Интерфейс ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="12aed-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="12aed-261">4</span><span class="sxs-lookup"><span data-stu-id="12aed-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="12aed-262">Интерфейс ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="12aed-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="12aed-263">4</span><span class="sxs-lookup"><span data-stu-id="12aed-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="12aed-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="12aed-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="12aed-265">4</span><span class="sxs-lookup"><span data-stu-id="12aed-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="12aed-266">икордебугкомобжектвалуе</span><span class="sxs-lookup"><span data-stu-id="12aed-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="12aed-267">4.5</span><span class="sxs-lookup"><span data-stu-id="12aed-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="12aed-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="12aed-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="12aed-269">4.5</span><span class="sxs-lookup"><span data-stu-id="12aed-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="12aed-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="12aed-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="12aed-271">4.5</span><span class="sxs-lookup"><span data-stu-id="12aed-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="12aed-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="12aed-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="12aed-273">4.5</span><span class="sxs-lookup"><span data-stu-id="12aed-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="12aed-274">Версия платформы .NET Framework (включая все пакеты обновления) — самая последняя.</span><span class="sxs-lookup"><span data-stu-id="12aed-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="12aed-275">Заметки</span><span class="sxs-lookup"><span data-stu-id="12aed-275">Remarks</span></span>  
 <span data-ttu-id="12aed-276">Отладчик может использовать перечисление `CorDebugInterfaceVersion` в функции [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) для указания самой последней версии .NET Framework, поддерживаемой отладчиком.</span><span class="sxs-lookup"><span data-stu-id="12aed-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="12aed-277">Имена интерфейсов</span><span class="sxs-lookup"><span data-stu-id="12aed-277">Interface Names</span></span>  
 <span data-ttu-id="12aed-278">Число в конце каждого имени интерфейсов в API отладки (например, "3" в `ICorDebugThread3`) обозначает версию интерфейса, а не платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12aed-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="12aed-279">Все имена интерфейсов в API отладки, кроме интерфейсов, появившихся в платформе .NET Framework версии 1, включают номера версий.</span><span class="sxs-lookup"><span data-stu-id="12aed-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="12aed-280">Любые совпадения между номерами версий интерфейсов и номерами версий платформы .NET Framework являются случайными.</span><span class="sxs-lookup"><span data-stu-id="12aed-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="12aed-281">Интерфейсы, представленные в платформе .NET Framework версии 1.0, не включают цифры, потому что все они имеют версию 1.</span><span class="sxs-lookup"><span data-stu-id="12aed-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="12aed-282">Платформа .NET Framework версии 1.1 использует интерфейсы версии 1.0 и не вводит никаких новых интерфейсов отладки.</span><span class="sxs-lookup"><span data-stu-id="12aed-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="12aed-283">Четырнадцать интерфейсов отладки, представленных в платформе .NET Framework версии 2.0, являются логическими расширениями версии 1, а их названия содержат число "2".</span><span class="sxs-lookup"><span data-stu-id="12aed-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="12aed-284">Платформы .NET Framework версий 3.0 и 3.5 используют существующие интерфейсы платформы .NET Framework версии 2.0 и не вводят никаких новых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="12aed-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="12aed-285">В .NET Framework 4 введены разные версии интерфейса.</span><span class="sxs-lookup"><span data-stu-id="12aed-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="12aed-286">Например, и `ICorDebugThread3`, и `ICorDebugThread4` отображаются как третья и четвертая версии интерфейса `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="12aed-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="12aed-287">В .NET Framework 4 также введена первая версия интерфейса `ICorDebugStackWalk` и вторая версия интерфейса `ICorDebugNativeFrame` (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="12aed-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12aed-288">Требования</span><span class="sxs-lookup"><span data-stu-id="12aed-288">Requirements</span></span>  
 <span data-ttu-id="12aed-289">**Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12aed-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12aed-290">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12aed-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12aed-291">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12aed-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12aed-292">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12aed-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12aed-293">См. также</span><span class="sxs-lookup"><span data-stu-id="12aed-293">See also</span></span>

- [<span data-ttu-id="12aed-294">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="12aed-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
