---
title: Практическое руководство. Создание пользовательской привязки надежного сеанса с использованием HTTPS
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599000"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="4a2b8-102">Практическое руководство. Создание пользовательской привязки надежного сеанса с использованием HTTPS</span><span class="sxs-lookup"><span data-stu-id="4a2b8-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="4a2b8-103">В этом разделе рассматривается использование механизма обеспечения безопасности транспорта через протокол SSL и надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="4a2b8-104">Для использования надежных сеансов через протокол HTTPS требуется создать пользовательскую привязку, использующую надежный сеанс и транспорт HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="4a2b8-105">Надежный сеанс можно включить принудительно с помощью кода или декларативно в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="4a2b8-106">В этой процедуре используются файлы конфигурации клиента и службы для включения надежного сеанса и [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="4a2b8-107">Основная часть этой процедуры заключается в том, что **\<endpoint>** элемент Configuration содержит `bindingConfiguration` атрибут, который ссылается на конфигурацию пользовательской привязки с именем `reliableSessionOverHttps` .</span><span class="sxs-lookup"><span data-stu-id="4a2b8-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="4a2b8-108">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Элемент Configuration ссылается на это имя, чтобы указать, что надежный сеанс и транспорт HTTPS используются, включая **\<reliableSession>** элементы и **\<httpsTransport>** .</span><span class="sxs-lookup"><span data-stu-id="4a2b8-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="4a2b8-109">Исходный экземпляр этого примера см. в разделе [Пользовательская привязка надежного сеанса по протоколу HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="4a2b8-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="4a2b8-110">Настройка службы с помощью CustomBinding для использования надежного сеанса с HTTPS</span><span class="sxs-lookup"><span data-stu-id="4a2b8-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="4a2b8-111">Определите контракт службы для данного типа службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="4a2b8-112">Реализуйте контракт службы в классе службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="4a2b8-113">Обратите внимание, что адрес или сведения о привязке не указываются внутри реализации службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="4a2b8-114">Вам не нужно писать код для получения адреса или сведений о привязке из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="4a2b8-115">Создайте файл *Web. config* , чтобы настроить конечную точку для `CalculatorService` с пользовательской привязкой с именем `reliableSessionOverHttps` , использующей надежный сеанс и транспорт HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="4a2b8-116">Создайте файл *Service. svc* , содержащий строку:</span><span class="sxs-lookup"><span data-stu-id="4a2b8-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="4a2b8-117">Поместите файл *Service. svc* в виртуальный каталог службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="4a2b8-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="4a2b8-118">Настройка клиента с помощью CustomBinding для использования надежного сеанса с HTTPS</span><span class="sxs-lookup"><span data-stu-id="4a2b8-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="4a2b8-119">Используйте [средство служебной программы метаданных ServiceModel (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) из командной строки для создания кода из метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="4a2b8-120">Созданный клиент содержит `ICalculator` интерфейс, определяющий контракт службы, которому должна соответствовать реализация клиента.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="4a2b8-121">Созданное клиентское приложение также содержит реализацию `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="4a2b8-122">Обратите внимание, что адрес и сведения о привязке не указаны в реализации службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="4a2b8-123">Вам не нужно писать код для получения адреса и сведений о привязке из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="4a2b8-124">Настройте пользовательскую привязку с именем `reliableSessionOverHttps` , чтобы использовать транспорт HTTPS и надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="4a2b8-125">Создайте экземпляр класса `ClientCalculator` в приложении и вызовите операции службы.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="4a2b8-126">Скомпилируйте и запустите клиент.</span><span class="sxs-lookup"><span data-stu-id="4a2b8-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="4a2b8-127">безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4a2b8-127">.NET Framework security</span></span>

<span data-ttu-id="4a2b8-128">Так как сертификат, используемый в этом примере, является тестовым сертификатом, созданным с помощью *Makecert. exe*, при попытке доступа к HTTPS-адресу, например, в браузере появляется предупреждение системы безопасности `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="4a2b8-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a2b8-129">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="4a2b8-129">See also</span></span>

- [<span data-ttu-id="4a2b8-130">Надежные сеансы</span><span class="sxs-lookup"><span data-stu-id="4a2b8-130">Reliable Sessions</span></span>](reliable-sessions.md)
