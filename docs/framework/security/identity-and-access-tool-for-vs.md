---
title: Средство Identity and Access Tool для Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 9216298889637780e79d1bfc7ac060458c745968
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170122"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="5913f-102">Средство Identity and Access Tool для Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="5913f-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="5913f-103">В этом разделе представлены сведения о новом средстве Identity and Access Tool для Visual Studio 11.</span><span class="sxs-lookup"><span data-stu-id="5913f-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="5913f-104">Это средство можно загрузить со следующего URL: [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849) или непосредственно из Visual Studio 11, выполнив поиск «identity» в диспетчере расширений.</span><span class="sxs-lookup"><span data-stu-id="5913f-104">You can download this tool from the following URL: [https://go.microsoft.com/fwlink/?LinkID=245849](https://go.microsoft.com/fwlink/?LinkID=245849) or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="5913f-105">Средство Identity and Access Tool для Visual Studio 11 предлагает существенно упрощенную среду для разработки. Особенности данной среды:</span><span class="sxs-lookup"><span data-stu-id="5913f-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
-   <span data-ttu-id="5913f-106">С помощью данного средства можно выполнять разработку, ориентированную на IIS Express, при помощи различных типов проектов веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="5913f-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
-   <span data-ttu-id="5913f-107">В отличие от общей аутентификации, пригодной только для защиты, новое средство предоставляет возможность указать страницу обнаружения/контроллер локальной домашней области (или любую другую конечную точку, в которой ваше приложение реализует аутентификацию), после чего WIF настроит все запросы, не прошедшие аутентификацию, на переход в данную область вместо перенаправления в STS.</span><span class="sxs-lookup"><span data-stu-id="5913f-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
-   <span data-ttu-id="5913f-108">Данное средство включает в себя тестовую службу токенов безопасности (STS), выполняемую на локальном компьютере при запуске сеанса отладки.</span><span class="sxs-lookup"><span data-stu-id="5913f-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="5913f-109">Поэтому вам больше не потребуется создавать настраиваемые проекты STS и адаптировать их для получения утверждений, необходимых для тестирования ваших приложений.</span><span class="sxs-lookup"><span data-stu-id="5913f-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="5913f-110">Типы и значения утверждений полностью настраиваются.</span><span class="sxs-lookup"><span data-stu-id="5913f-110">The claim types and values are fully customizable.</span></span>  
  
-   <span data-ttu-id="5913f-111">Стандартные параметры можно изменить напрямую через интерфейс данного средства, не редактируя файл web.config.</span><span class="sxs-lookup"><span data-stu-id="5913f-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
-   <span data-ttu-id="5913f-112">Можно создать федерацию со службами федерации Active Directory (AD FS) 2.0 (или другими поставщиками WS-Federation) на одном экране.</span><span class="sxs-lookup"><span data-stu-id="5913f-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
-   <span data-ttu-id="5913f-113">Данный инструмент применяет возможности службы контроля доступа (ACS) Azure Windows с помощью простой список флажков для всех поставщиков удостоверений, которые вы хотите использовать: Facebook, Google, Live ID, Yahoo!, любой поставщик OpenID и любым поставщиком WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="5913f-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="5913f-114">Выберите поставщиков удостоверений, нажмите кнопку OK, а затем клавишу F5. Ваше приложение и ACS будут автоматически настроены, после чего тестовое приложение будет поддерживать службу ACS.</span><span class="sxs-lookup"><span data-stu-id="5913f-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5913f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5913f-115">See also</span></span>

- [<span data-ttu-id="5913f-116">Возможности WIF</span><span class="sxs-lookup"><span data-stu-id="5913f-116">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)
