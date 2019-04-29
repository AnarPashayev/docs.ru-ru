---
title: События безопасности (трассировка событий Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949205"
---
# <a name="security-etw-events"></a><span data-ttu-id="e7c52-102">События безопасности (трассировка событий Windows)</span><span class="sxs-lookup"><span data-stu-id="e7c52-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="e7c52-103">События безопасности создаются при проверке строгого имени и проверке Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e7c52-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="e7c52-104">Эта категория состоит из следующих событий:</span><span class="sxs-lookup"><span data-stu-id="e7c52-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="e7c52-105">События StrongNameVerificationStart_V1 и StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="e7c52-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="e7c52-106">События AuthenticodeVerificationStart_V1 и AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="e7c52-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="e7c52-107">События StrongNameVerificationStart_V1 и StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="e7c52-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="e7c52-108">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e7c52-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="e7c52-109">(Дополнительные сведения см. в разделе [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e7c52-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e7c52-110">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e7c52-110">Keyword for raising the event</span></span>|<span data-ttu-id="e7c52-111">Уровень</span><span class="sxs-lookup"><span data-stu-id="e7c52-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e7c52-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="e7c52-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="e7c52-113">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e7c52-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="e7c52-114">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e7c52-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e7c52-115">событие</span><span class="sxs-lookup"><span data-stu-id="e7c52-115">Event</span></span>|<span data-ttu-id="e7c52-116">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e7c52-116">Event ID</span></span>|<span data-ttu-id="e7c52-117">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e7c52-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="e7c52-118">181</span><span class="sxs-lookup"><span data-stu-id="e7c52-118">181</span></span>|<span data-ttu-id="e7c52-119">Начало проверки строгого имени.</span><span class="sxs-lookup"><span data-stu-id="e7c52-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="e7c52-120">182</span><span class="sxs-lookup"><span data-stu-id="e7c52-120">182</span></span>|<span data-ttu-id="e7c52-121">Окончание проверки строгого имени.</span><span class="sxs-lookup"><span data-stu-id="e7c52-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="e7c52-122">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e7c52-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e7c52-123">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e7c52-123">Field name</span></span>|<span data-ttu-id="e7c52-124">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e7c52-124">Data type</span></span>|<span data-ttu-id="e7c52-125">Описание</span><span class="sxs-lookup"><span data-stu-id="e7c52-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e7c52-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="e7c52-126">VerificationFlags</span></span>|<span data-ttu-id="e7c52-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7c52-127">win:UInt32</span></span>|<span data-ttu-id="e7c52-128">Флаги проверки.</span><span class="sxs-lookup"><span data-stu-id="e7c52-128">The verification flags.</span></span>|  
|<span data-ttu-id="e7c52-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="e7c52-129">ErrorCode</span></span>|<span data-ttu-id="e7c52-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7c52-130">win:UInt32</span></span>|<span data-ttu-id="e7c52-131">Код ошибки HResult.</span><span class="sxs-lookup"><span data-stu-id="e7c52-131">The HResult error code.</span></span>|  
|<span data-ttu-id="e7c52-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="e7c52-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="e7c52-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e7c52-133">win:UnicodeString</span></span>|<span data-ttu-id="e7c52-134">Полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="e7c52-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="e7c52-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e7c52-135">ClrInstanceID</span></span>|<span data-ttu-id="e7c52-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e7c52-136">win:UInt16</span></span>|<span data-ttu-id="e7c52-137">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e7c52-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e7c52-138">К началу</span><span class="sxs-lookup"><span data-stu-id="e7c52-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="e7c52-139">События AuthenticodeVerificationStart_V1 и AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="e7c52-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="e7c52-140">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e7c52-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e7c52-141">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e7c52-141">Keyword for raising the event</span></span>|<span data-ttu-id="e7c52-142">Уровень</span><span class="sxs-lookup"><span data-stu-id="e7c52-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e7c52-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="e7c52-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="e7c52-144">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e7c52-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="e7c52-145">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e7c52-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e7c52-146">событие</span><span class="sxs-lookup"><span data-stu-id="e7c52-146">Event</span></span>|<span data-ttu-id="e7c52-147">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e7c52-147">Event ID</span></span>|<span data-ttu-id="e7c52-148">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e7c52-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="e7c52-149">183</span><span class="sxs-lookup"><span data-stu-id="e7c52-149">183</span></span>|<span data-ttu-id="e7c52-150">Начало проверки Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e7c52-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="e7c52-151">184</span><span class="sxs-lookup"><span data-stu-id="e7c52-151">184</span></span>|<span data-ttu-id="e7c52-152">Окончание проверки Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e7c52-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="e7c52-153">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e7c52-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e7c52-154">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e7c52-154">Field name</span></span>|<span data-ttu-id="e7c52-155">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e7c52-155">Data type</span></span>|<span data-ttu-id="e7c52-156">Описание</span><span class="sxs-lookup"><span data-stu-id="e7c52-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e7c52-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="e7c52-157">VerificationFlags</span></span>|<span data-ttu-id="e7c52-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7c52-158">win:UInt32</span></span>|<span data-ttu-id="e7c52-159">Флаги проверки.</span><span class="sxs-lookup"><span data-stu-id="e7c52-159">The verification flags.</span></span>|  
|<span data-ttu-id="e7c52-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="e7c52-160">ErrorCode</span></span>|<span data-ttu-id="e7c52-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7c52-161">win:UInt32</span></span>|<span data-ttu-id="e7c52-162">Код ошибки HResult.</span><span class="sxs-lookup"><span data-stu-id="e7c52-162">The HResult error code.</span></span>|  
|<span data-ttu-id="e7c52-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="e7c52-163">ModulePath</span></span>|<span data-ttu-id="e7c52-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e7c52-164">win:UnicodeString</span></span>|<span data-ttu-id="e7c52-165">Путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="e7c52-165">The module path.</span></span>|  
|<span data-ttu-id="e7c52-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e7c52-166">ClrInstanceID</span></span>|<span data-ttu-id="e7c52-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e7c52-167">win:UInt16</span></span>|<span data-ttu-id="e7c52-168">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e7c52-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7c52-169">См. также</span><span class="sxs-lookup"><span data-stu-id="e7c52-169">See also</span></span>

- [<span data-ttu-id="e7c52-170">События трассировки событий Windows в среде CLR</span><span class="sxs-lookup"><span data-stu-id="e7c52-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
