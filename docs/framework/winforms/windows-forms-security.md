---
title: Безопасность Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: f64d5ef2e9bb0e977b4c007e8c5109ac0c331a84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799376"
---
# <a name="windows-forms-security"></a><span data-ttu-id="b86ec-102">Безопасность Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b86ec-102">Windows Forms Security</span></span>
<span data-ttu-id="b86ec-103">Windows Forms представляют модель безопасности, основанные на коде (безопасности для кода, независимо от того, пользователь, запускающий код заданы режимы).</span><span class="sxs-lookup"><span data-stu-id="b86ec-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="b86ec-104">Это дополнение к всем схемам безопасности, которые могут быть выполнены уже на компьютере.</span><span class="sxs-lookup"><span data-stu-id="b86ec-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="b86ec-105">Они могут включать в браузере (например, безопасность на основе зон в Internet Explorer) или для операционной системы (например, безопасность Windows NT, основанная на учетных данных).</span><span class="sxs-lookup"><span data-stu-id="b86ec-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b86ec-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="b86ec-106">In This Section</span></span>  
 [<span data-ttu-id="b86ec-107">Общие сведения о безопасности в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b86ec-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="b86ec-108">Краткое описание модели безопасности платформы .NET Framework и основные шаги, необходимые для приложений Windows Forms являются безопасными.</span><span class="sxs-lookup"><span data-stu-id="b86ec-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="b86ec-109">Более безопасный доступ к файлам и данным в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b86ec-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="b86ec-110">Описание способов доступа к файлам и данным в среде с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="b86ec-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="b86ec-111">Более безопасная печать в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b86ec-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="b86ec-112">Описание способов доступа к возможностям печати в среде с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="b86ec-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="b86ec-113">Дополнительные вопросы безопасности в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b86ec-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="b86ec-114">Описание работы с окнами с помощью буфера обмена и вызовы неуправляемого кода в среде с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="b86ec-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b86ec-115">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="b86ec-115">Related Sections</span></span>  
 <span data-ttu-id="b86ec-116">[Политика безопасности по умолчанию](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b86ec-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="b86ec-117">Перечисляет разрешения по умолчанию в наборах разрешений полного доверия, локальной интрасети и Интернета.</span><span class="sxs-lookup"><span data-stu-id="b86ec-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="b86ec-118">[Общее администрирование политики безопасности](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b86ec-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="b86ec-119">Сведения по администрированию политики безопасности платформы .NET Framework и повышению разрешений.</span><span class="sxs-lookup"><span data-stu-id="b86ec-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="b86ec-120">Опасные разрешения и администрирование политик</span><span class="sxs-lookup"><span data-stu-id="b86ec-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="b86ec-121">Рассказывает о некоторых разрешений.NET Framework, которые потенциально позволяют обойти систему безопасности.</span><span class="sxs-lookup"><span data-stu-id="b86ec-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="b86ec-122">Правила написания безопасного кода</span><span class="sxs-lookup"><span data-stu-id="b86ec-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="b86ec-123">Ссылки на разделы, объясняющие и рекомендации по написанию безопасного кода для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b86ec-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="b86ec-124">[Запрос разрешений](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b86ec-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="b86ec-125">Обсуждается использование атрибутов, которые позволяют среду выполнения о разрешениях, ваш код должен выполнять.</span><span class="sxs-lookup"><span data-stu-id="b86ec-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="b86ec-126">Основные понятия безопасности</span><span class="sxs-lookup"><span data-stu-id="b86ec-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="b86ec-127">Ссылки на разделы, посвященные основным аспектам безопасности кода.</span><span class="sxs-lookup"><span data-stu-id="b86ec-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="b86ec-128">Основы управления доступом для кода</span><span class="sxs-lookup"><span data-stu-id="b86ec-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="b86ec-129">Рассматриваются основы работы с политикой безопасности времени выполнения .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b86ec-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="b86ec-130">[Определение необходимости изменения политики безопасности](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b86ec-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="b86ec-131">Объясняется, как определить, когда ваши приложения должны отклоняться от политики безопасности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b86ec-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="b86ec-132">[Развертывание политики безопасности](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b86ec-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="b86ec-133">Обсуждение наилучших способов для развертывания изменений политики безопасности.</span><span class="sxs-lookup"><span data-stu-id="b86ec-133">Discusses the best manner for deploying security policy changes.</span></span>
