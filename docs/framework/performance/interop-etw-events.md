---
title: События взаимодействия (трассировка событий Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38db390b8fad9cd36dacf33f9647b0272eddc4a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616407"
---
# <a name="interop-etw-events"></a><span data-ttu-id="a7d7b-102">События взаимодействия (трассировка событий Windows)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="a7d7b-103">С помощью событий взаимодействия регистрируются сведения о создании заглушек и кэшировании MSIL.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="a7d7b-104">Эта категория состоит из следующих событий:</span><span class="sxs-lookup"><span data-stu-id="a7d7b-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="a7d7b-105">Событие ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="a7d7b-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="a7d7b-106">Событие ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="a7d7b-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="a7d7b-107">Событие ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="a7d7b-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="a7d7b-108">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="a7d7b-109">(Дополнительные сведения см. в разделе [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a7d7b-110">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="a7d7b-110">Keyword for raising the event</span></span>|<span data-ttu-id="a7d7b-111">Уровень</span><span class="sxs-lookup"><span data-stu-id="a7d7b-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a7d7b-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="a7d7b-113">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="a7d7b-114">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a7d7b-115">событие</span><span class="sxs-lookup"><span data-stu-id="a7d7b-115">Event</span></span>|<span data-ttu-id="a7d7b-116">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="a7d7b-116">Event ID</span></span>|<span data-ttu-id="a7d7b-117">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="a7d7b-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="a7d7b-118">88</span><span class="sxs-lookup"><span data-stu-id="a7d7b-118">88</span></span>|<span data-ttu-id="a7d7b-119">Была создана заглушка языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="a7d7b-120">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a7d7b-121">Имя поля</span><span class="sxs-lookup"><span data-stu-id="a7d7b-121">Field name</span></span>|<span data-ttu-id="a7d7b-122">Тип данных</span><span class="sxs-lookup"><span data-stu-id="a7d7b-122">Data type</span></span>|<span data-ttu-id="a7d7b-123">Описание</span><span class="sxs-lookup"><span data-stu-id="a7d7b-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a7d7b-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-124">ModuleID</span></span>|<span data-ttu-id="a7d7b-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a7d7b-125">win:UInt16</span></span>|<span data-ttu-id="a7d7b-126">Идентификатор модуля.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-126">The module identifier.</span></span>|  
|<span data-ttu-id="a7d7b-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-127">StubMethodID</span></span>|<span data-ttu-id="a7d7b-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a7d7b-128">win:UInt64</span></span>|<span data-ttu-id="a7d7b-129">Идентификатор метода-заглушки.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="a7d7b-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="a7d7b-130">StubFlags</span></span>|<span data-ttu-id="a7d7b-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a7d7b-131">win:UInt64</span></span>|<span data-ttu-id="a7d7b-132">Флаги для заглушки:</span><span class="sxs-lookup"><span data-stu-id="a7d7b-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="a7d7b-133">0x1 — обратное взаимодействие;</span><span class="sxs-lookup"><span data-stu-id="a7d7b-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="a7d7b-134">0x2 — COM-взаимодействие;</span><span class="sxs-lookup"><span data-stu-id="a7d7b-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="a7d7b-135">0x4 — заглушка, созданная программой NGen.exe;</span><span class="sxs-lookup"><span data-stu-id="a7d7b-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="a7d7b-136">0x8 — делегат;</span><span class="sxs-lookup"><span data-stu-id="a7d7b-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="a7d7b-137">0x10 — переменный аргумент;</span><span class="sxs-lookup"><span data-stu-id="a7d7b-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="a7d7b-138">0x20 — неуправляемый вызываемый метод.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="a7d7b-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a7d7b-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a7d7b-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a7d7b-140">win:UInt32</span></span>|<span data-ttu-id="a7d7b-141">Токен управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a7d7b-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a7d7b-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-143">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-144">Пространство имен управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a7d7b-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="a7d7b-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-146">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-147">Имя управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a7d7b-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a7d7b-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-149">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-150">Сигнатура управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a7d7b-151">NativeMethodSignature</span></span>|<span data-ttu-id="a7d7b-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-152">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-153">Сигнатура неуправляемого метода.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-153">The native method signature.</span></span>|  
|<span data-ttu-id="a7d7b-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a7d7b-154">StubMethodSignature</span></span>|<span data-ttu-id="a7d7b-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-155">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-156">Сигнатура метода-заглушки.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-156">The stub method signature.</span></span>|  
|<span data-ttu-id="a7d7b-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="a7d7b-157">StubMethodILCode</span></span>|<span data-ttu-id="a7d7b-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-158">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-159">Код MSIL для метода-заглушки.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="a7d7b-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-160">ClrInstanceID</span></span>|<span data-ttu-id="a7d7b-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a7d7b-161">win:UInt16</span></span>|<span data-ttu-id="a7d7b-162">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a7d7b-163">К началу</span><span class="sxs-lookup"><span data-stu-id="a7d7b-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="a7d7b-164">Событие ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="a7d7b-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="a7d7b-165">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a7d7b-166">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="a7d7b-166">Keyword for raising the event</span></span>|<span data-ttu-id="a7d7b-167">Уровень</span><span class="sxs-lookup"><span data-stu-id="a7d7b-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a7d7b-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="a7d7b-169">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="a7d7b-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="a7d7b-170">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a7d7b-171">событие</span><span class="sxs-lookup"><span data-stu-id="a7d7b-171">Event</span></span>|<span data-ttu-id="a7d7b-172">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="a7d7b-172">Event ID</span></span>|<span data-ttu-id="a7d7b-173">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="a7d7b-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="a7d7b-174">89</span><span class="sxs-lookup"><span data-stu-id="a7d7b-174">89</span></span>|<span data-ttu-id="a7d7b-175">Обращение к кэшу MSIL.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="a7d7b-176">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a7d7b-177">Имя поля</span><span class="sxs-lookup"><span data-stu-id="a7d7b-177">Field name</span></span>|<span data-ttu-id="a7d7b-178">Тип данных</span><span class="sxs-lookup"><span data-stu-id="a7d7b-178">Data type</span></span>|<span data-ttu-id="a7d7b-179">Описание</span><span class="sxs-lookup"><span data-stu-id="a7d7b-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a7d7b-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-180">ModuleID</span></span>|<span data-ttu-id="a7d7b-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a7d7b-181">win:UInt16</span></span>|<span data-ttu-id="a7d7b-182">Идентификатор модуля.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-182">The module identifier.</span></span>|  
|<span data-ttu-id="a7d7b-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-183">StubMethodID</span></span>|<span data-ttu-id="a7d7b-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a7d7b-184">win:UInt64</span></span>|<span data-ttu-id="a7d7b-185">Идентификатор метода-заглушки.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="a7d7b-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a7d7b-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a7d7b-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a7d7b-187">win:UInt32</span></span>|<span data-ttu-id="a7d7b-188">Токен управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a7d7b-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a7d7b-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-190">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-191">Пространство имен управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a7d7b-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="a7d7b-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-193">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-194">Имя управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a7d7b-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a7d7b-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a7d7b-196">win:UnicodeString</span></span>|<span data-ttu-id="a7d7b-197">Сигнатура управляемого метода взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a7d7b-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a7d7b-198">ClrInstanceID</span></span>|<span data-ttu-id="a7d7b-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a7d7b-199">win:UInt16</span></span>|<span data-ttu-id="a7d7b-200">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a7d7b-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a7d7b-201">К началу</span><span class="sxs-lookup"><span data-stu-id="a7d7b-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="a7d7b-202">См. также</span><span class="sxs-lookup"><span data-stu-id="a7d7b-202">See also</span></span>

- [<span data-ttu-id="a7d7b-203">События трассировки событий Windows в среде CLR</span><span class="sxs-lookup"><span data-stu-id="a7d7b-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
