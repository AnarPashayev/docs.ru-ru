---
title: События безопасности (трассировка событий Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ea19c88ff8b854b09ed372b35bf8c45d994585
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583650"
---
# <a name="security-etw-events"></a><span data-ttu-id="23654-102">События безопасности (трассировка событий Windows)</span><span class="sxs-lookup"><span data-stu-id="23654-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="23654-103">События безопасности создаются при проверке строгого имени и проверке Authenticode.</span><span class="sxs-lookup"><span data-stu-id="23654-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="23654-104">Эта категория состоит из следующих событий:</span><span class="sxs-lookup"><span data-stu-id="23654-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="23654-105">События StrongNameVerificationStart_V1 и StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="23654-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="23654-106">События AuthenticodeVerificationStart_V1 и AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="23654-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="23654-107">События StrongNameVerificationStart_V1 и StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="23654-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="23654-108">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="23654-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="23654-109">(Дополнительные сведения см. в разделе [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="23654-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="23654-110">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="23654-110">Keyword for raising the event</span></span>|<span data-ttu-id="23654-111">Уровень</span><span class="sxs-lookup"><span data-stu-id="23654-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="23654-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="23654-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="23654-113">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="23654-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="23654-114">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="23654-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="23654-115">событие</span><span class="sxs-lookup"><span data-stu-id="23654-115">Event</span></span>|<span data-ttu-id="23654-116">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="23654-116">Event ID</span></span>|<span data-ttu-id="23654-117">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="23654-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="23654-118">181</span><span class="sxs-lookup"><span data-stu-id="23654-118">181</span></span>|<span data-ttu-id="23654-119">Начало проверки строгого имени.</span><span class="sxs-lookup"><span data-stu-id="23654-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="23654-120">182</span><span class="sxs-lookup"><span data-stu-id="23654-120">182</span></span>|<span data-ttu-id="23654-121">Окончание проверки строгого имени.</span><span class="sxs-lookup"><span data-stu-id="23654-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="23654-122">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="23654-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="23654-123">Имя поля</span><span class="sxs-lookup"><span data-stu-id="23654-123">Field name</span></span>|<span data-ttu-id="23654-124">Тип данных</span><span class="sxs-lookup"><span data-stu-id="23654-124">Data type</span></span>|<span data-ttu-id="23654-125">Описание</span><span class="sxs-lookup"><span data-stu-id="23654-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="23654-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="23654-126">VerificationFlags</span></span>|<span data-ttu-id="23654-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="23654-127">win:UInt32</span></span>|<span data-ttu-id="23654-128">Флаги проверки.</span><span class="sxs-lookup"><span data-stu-id="23654-128">The verification flags.</span></span>|  
|<span data-ttu-id="23654-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="23654-129">ErrorCode</span></span>|<span data-ttu-id="23654-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="23654-130">win:UInt32</span></span>|<span data-ttu-id="23654-131">Код ошибки HResult.</span><span class="sxs-lookup"><span data-stu-id="23654-131">The HResult error code.</span></span>|  
|<span data-ttu-id="23654-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="23654-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="23654-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="23654-133">win:UnicodeString</span></span>|<span data-ttu-id="23654-134">Полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="23654-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="23654-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="23654-135">ClrInstanceID</span></span>|<span data-ttu-id="23654-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="23654-136">win:UInt16</span></span>|<span data-ttu-id="23654-137">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="23654-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="23654-138">К началу</span><span class="sxs-lookup"><span data-stu-id="23654-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="23654-139">События AuthenticodeVerificationStart_V1 и AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="23654-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="23654-140">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="23654-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="23654-141">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="23654-141">Keyword for raising the event</span></span>|<span data-ttu-id="23654-142">Уровень</span><span class="sxs-lookup"><span data-stu-id="23654-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="23654-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="23654-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="23654-144">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="23654-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="23654-145">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="23654-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="23654-146">событие</span><span class="sxs-lookup"><span data-stu-id="23654-146">Event</span></span>|<span data-ttu-id="23654-147">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="23654-147">Event ID</span></span>|<span data-ttu-id="23654-148">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="23654-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="23654-149">183</span><span class="sxs-lookup"><span data-stu-id="23654-149">183</span></span>|<span data-ttu-id="23654-150">Начало проверки Authenticode.</span><span class="sxs-lookup"><span data-stu-id="23654-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="23654-151">184</span><span class="sxs-lookup"><span data-stu-id="23654-151">184</span></span>|<span data-ttu-id="23654-152">Окончание проверки Authenticode.</span><span class="sxs-lookup"><span data-stu-id="23654-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="23654-153">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="23654-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="23654-154">Имя поля</span><span class="sxs-lookup"><span data-stu-id="23654-154">Field name</span></span>|<span data-ttu-id="23654-155">Тип данных</span><span class="sxs-lookup"><span data-stu-id="23654-155">Data type</span></span>|<span data-ttu-id="23654-156">Описание</span><span class="sxs-lookup"><span data-stu-id="23654-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="23654-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="23654-157">VerificationFlags</span></span>|<span data-ttu-id="23654-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="23654-158">win:UInt32</span></span>|<span data-ttu-id="23654-159">Флаги проверки.</span><span class="sxs-lookup"><span data-stu-id="23654-159">The verification flags.</span></span>|  
|<span data-ttu-id="23654-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="23654-160">ErrorCode</span></span>|<span data-ttu-id="23654-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="23654-161">win:UInt32</span></span>|<span data-ttu-id="23654-162">Код ошибки HResult.</span><span class="sxs-lookup"><span data-stu-id="23654-162">The HResult error code.</span></span>|  
|<span data-ttu-id="23654-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="23654-163">ModulePath</span></span>|<span data-ttu-id="23654-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="23654-164">win:UnicodeString</span></span>|<span data-ttu-id="23654-165">Путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="23654-165">The module path.</span></span>|  
|<span data-ttu-id="23654-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="23654-166">ClrInstanceID</span></span>|<span data-ttu-id="23654-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="23654-167">win:UInt16</span></span>|<span data-ttu-id="23654-168">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="23654-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23654-169">См. также</span><span class="sxs-lookup"><span data-stu-id="23654-169">See also</span></span>

- [<span data-ttu-id="23654-170">События трассировки событий Windows в среде CLR</span><span class="sxs-lookup"><span data-stu-id="23654-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
