---
title: 'Как выполнить: Включение обнаружения воспроизведения маркеров'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
ms.openlocfilehash: a357f153d61b6a8e1e105639bd68647dabdc26f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940482"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="2e0b9-102">Как выполнить: Включение обнаружения воспроизведения маркеров</span><span class="sxs-lookup"><span data-stu-id="2e0b9-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="2e0b9-103">Применение</span><span class="sxs-lookup"><span data-stu-id="2e0b9-103">Applies To</span></span>  
  
- <span data-ttu-id="2e0b9-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="2e0b9-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="2e0b9-105">Веб-формы ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="2e0b9-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="2e0b9-106">Сводка</span><span class="sxs-lookup"><span data-stu-id="2e0b9-106">Summary</span></span>  
 <span data-ttu-id="2e0b9-107">Это практическое руководство содержит подробные пошаговые инструкции по включению обнаружения воспроизведения маркеров в приложении ASP.NET, использующем платформу WIF.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="2e0b9-108">Также здесь приводятся инструкции по проверке приложения на наличие включенной функции обнаружения воспроизведения маркеров.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="2e0b9-109">В этом практическом руководстве нет подробных инструкций по созданию службы токенов безопасности (STS); вместо этого используется служба Development STS, входящая в состав средства Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="2e0b9-110">Служба Development STS не выполняет фактическую аутентификацию и предназначена только для тестирования.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="2e0b9-111">Для выполнения этого практического руководства необходимо установить средство Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="2e0b9-112">Его можно скачать из следующего расположения: [IDENTITY and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="2e0b9-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="2e0b9-113">Описание</span><span class="sxs-lookup"><span data-stu-id="2e0b9-113">Contents</span></span>  
  
- <span data-ttu-id="2e0b9-114">Цели</span><span class="sxs-lookup"><span data-stu-id="2e0b9-114">Objectives</span></span>  
  
- <span data-ttu-id="2e0b9-115">Обзор</span><span class="sxs-lookup"><span data-stu-id="2e0b9-115">Overview</span></span>  
  
- <span data-ttu-id="2e0b9-116">Сводка действий</span><span class="sxs-lookup"><span data-stu-id="2e0b9-116">Summary of Steps</span></span>  
  
- <span data-ttu-id="2e0b9-117">Шаг 1. Создание простого приложения веб-форм ASP.NET и включение обнаружения воспроизведения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
- <span data-ttu-id="2e0b9-118">Шаг 2. Тестирование решения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="2e0b9-119">Цели</span><span class="sxs-lookup"><span data-stu-id="2e0b9-119">Objectives</span></span>  
  
- <span data-ttu-id="2e0b9-120">Создание простого приложения ASP.NET, которое использует WIF и службу Development STS в составе средства Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="2e0b9-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
- <span data-ttu-id="2e0b9-121">Включение обнаружения воспроизведения маркеров и проверка работоспособности этой функции</span><span class="sxs-lookup"><span data-stu-id="2e0b9-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="2e0b9-122">Обзор</span><span class="sxs-lookup"><span data-stu-id="2e0b9-122">Overview</span></span>  
 <span data-ttu-id="2e0b9-123">Атаки с повторением пакетов возникают в тех случаях, когда клиент пытается проверить подлинность проверяющей стороны с помощью маркера службы маркеров безопасности, который уже был использован этим клиентом.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="2e0b9-124">Чтобы предотвратить атаки такого рода, на платформе WIF применяется кэш обнаружения воспроизведения ранее использованных маркеров службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="2e0b9-125">Если обнаружение воспроизведения включено, эта функция проверяет маркер безопасности входящего запроса и определяет, был ли он использован ранее.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="2e0b9-126">Если этот маркер уже использовался, запрос отклоняется и возникает исключение <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException>.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="2e0b9-127">Далее демонстрируются изменения конфигурации, которые необходимы для включения обнаружения воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="2e0b9-128">Сводка действий</span><span class="sxs-lookup"><span data-stu-id="2e0b9-128">Summary of Steps</span></span>  
  
- <span data-ttu-id="2e0b9-129">Шаг 1. Создание простого приложения веб-форм ASP.NET и включение обнаружения воспроизведения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
- <span data-ttu-id="2e0b9-130">Шаг 2. Тестирование решения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="2e0b9-131">Шаг 1. Создание простого приложения веб-форм ASP.NET и включение обнаружения воспроизведения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="2e0b9-132">На этом шаге вы создадите приложение веб-форм ASP.NET и включите обнаружение воспроизведения, изменив файл *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="2e0b9-133">Создание простого приложения ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e0b9-133">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="2e0b9-134">Запустите Visual Studio и выберите **Файл**, **Создать** и затем **Проект**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="2e0b9-135">В окне **Новый проект** выберите **Приложение веб-форм ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="2e0b9-136">В поле **Имя** введите `TestApp` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="2e0b9-137">В **обозревателе решений** щелкните правой кнопкой мыши проект **TestApp**, а затем выберите **Идентификация и доступ**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="2e0b9-138">Откроется окно **Идентификация и доступ**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="2e0b9-139">В поле **Поставщики** выберите **Протестировать приложение с помощью локальной службы Development STS** и нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="2e0b9-140">Добавьте следующий элемент **\<tokenReplayDetection>** в файл конфигурации *Web.config* непосредственно после элементов **\<system.identityModel>** и **\<identityConfiguration>**, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2e0b9-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="2e0b9-141">Шаг 2. Тестирование решения</span><span class="sxs-lookup"><span data-stu-id="2e0b9-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="2e0b9-142">На этом шаге вы проверите, включено ли обнаружение воспроизведения в приложении ASP.NET с поддержкой WIF.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="2e0b9-143">Проверка обнаружения воспроизведения в приложении ASP.NET с поддержкой WIF</span><span class="sxs-lookup"><span data-stu-id="2e0b9-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1. <span data-ttu-id="2e0b9-144">Запустите решение, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="2e0b9-145">Откроется домашняя страница ASP.NET по умолчанию, и будет выполнен автоматический вход в систему с именем пользователя *Terry*. Это пользователь по умолчанию для службы Development STS.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="2e0b9-146">Нажмите кнопку **Назад** в браузере.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="2e0b9-147">Вы увидите **ошибка сервера в приложении «/»** страницы со следующим описанием: *ID1062: Обнаружено для: Маркер: «System.IdentityModel.Tokens.SamlSecurityToken»*, за которым следует *AssertionId* и *издателя*.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="2e0b9-148">Эта страница появляется в том случае, если было обнаружено воспроизведение маркера безопасности и возникло исключение <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException>.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="2e0b9-149">Эта ошибка происходит при попытке повторно отправить первоначальный запрос POST, для которого сначала был предоставлен маркер безопасности.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="2e0b9-150">Такое поведение не наблюдается при нажатии кнопки **Назад** для последующих запросов к серверу.</span><span class="sxs-lookup"><span data-stu-id="2e0b9-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
