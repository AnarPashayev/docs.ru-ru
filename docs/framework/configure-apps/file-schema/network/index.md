---
title: Схема параметров сети
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 71d945e6046a8648a812de939f197429bc695808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674536"
---
# <a name="network-settings-schema"></a><span data-ttu-id="30cf7-102">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="30cf7-102">Network Settings Schema</span></span>
<span data-ttu-id="30cf7-103">Параметры сети определяют способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="30cf7-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="30cf7-104">В приведенной ниже таблице описывается назначение каждого дочернего элемента конфигурации для [элемента \<system.Net> (параметры сети)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="30cf7-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="30cf7-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="30cf7-105">Element</span></span>|<span data-ttu-id="30cf7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="30cf7-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30cf7-107">Элемент \<authenticationModules> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="30cf7-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="30cf7-108">Определяет модули, используемые для проверки подлинности интернет-запросов.</span><span class="sxs-lookup"><span data-stu-id="30cf7-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="30cf7-109">Элемент \<connectionManagement> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="30cf7-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="30cf7-110">Задает максимальное число подключений к узлам в Интернете.</span><span class="sxs-lookup"><span data-stu-id="30cf7-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="30cf7-111">Элемент \<defaultProxy> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="30cf7-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="30cf7-112">Задает прокси-сервер, используемый для HTTP-запросов к Интернету.</span><span class="sxs-lookup"><span data-stu-id="30cf7-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="30cf7-113">Элемент \<mailSettings> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="30cf7-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="30cf7-114">Содержит параметры отправки почты.</span><span class="sxs-lookup"><span data-stu-id="30cf7-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="30cf7-115">Элемент \<requestCaching> (сетевые параметры)</span><span class="sxs-lookup"><span data-stu-id="30cf7-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="30cf7-116">Определяет механизм кэширования для сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="30cf7-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="30cf7-117">Элемент \<webRequestModules> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="30cf7-117">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="30cf7-118">Задает модули, используемые для запроса данных от узлов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="30cf7-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="30cf7-119">Параметры универсальных кодов ресурсов (URI) определяют, как платформа .NET Framework обрабатывает веб-адреса, выраженные с использованием URI.</span><span class="sxs-lookup"><span data-stu-id="30cf7-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="30cf7-120">В приведенной ниже таблице описывается назначение каждого дочернего элемента конфигурации для [элемента \<Uri> (параметры URI)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="30cf7-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="30cf7-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="30cf7-121">Element</span></span>|<span data-ttu-id="30cf7-122">Описание</span><span class="sxs-lookup"><span data-stu-id="30cf7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30cf7-123">Элемент \<idn> (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="30cf7-123">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="30cf7-124">Определяет, применяется ли к доменным именам анализ международных доменных имен (IDN).</span><span class="sxs-lookup"><span data-stu-id="30cf7-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="30cf7-125">Элемент \<iriParsing> (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="30cf7-125">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="30cf7-126">Определяет, применяется ли к <xref:System.Uri> анализ международных идентификаторов ресурсов (IRI) и применяются ли правила анализа IRI.</span><span class="sxs-lookup"><span data-stu-id="30cf7-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="30cf7-127">Элемент \<schemeSettings> (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="30cf7-127">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="30cf7-128">Определяет, как <xref:System.Uri> анализируется для определенных схем.</span><span class="sxs-lookup"><span data-stu-id="30cf7-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30cf7-129">См. также</span><span class="sxs-lookup"><span data-stu-id="30cf7-129">See also</span></span>

- [<span data-ttu-id="30cf7-130">Настройка веб-приложений</span><span class="sxs-lookup"><span data-stu-id="30cf7-130">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="30cf7-131">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="30cf7-131">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
