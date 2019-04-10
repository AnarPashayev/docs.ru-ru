---
title: Сертификат безопасности сообщений
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: b5a36d39e6e38f121bf3155c822681fb198f0850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306278"
---
# <a name="message-security-certificate"></a><span data-ttu-id="e5e6c-102">Сертификат безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="e5e6c-102">Message Security Certificate</span></span>
<span data-ttu-id="e5e6c-103">В этом образце показано, как реализовать приложение, использующее протокол WS-Security и проверку подлинности с использованием сертификата X.509 v3 для клиента и требующее проверки подлинности сервера с использованием сертификата X.509 v3 сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="e5e6c-104">В этом образце используются параметры по умолчанию, обеспечивающие подписывание и шифрование всех сообщений приложения, которыми обмениваются клиент и сервер.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="e5e6c-105">Этот образец основан на [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) и состоит из консольной программы клиента и библиотеку службы, размещаемую в Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="e5e6c-106">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="e5e6c-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5e6c-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e5e6c-108">В этом образце демонстрируется управление проверкой подлинности с помощью файла конфигурации, а также получение удостоверения вызывающего объекта из контекста безопасности, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="e5e6c-109">Служба предоставляет одну конечную точку для взаимодействия со службой и одну конечную точку для предоставления документа WSDL службы с использованием протокола WS-MetadataExchange, определенного с помощью файла конфигурации (Web.config).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="e5e6c-110">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e5e6c-111">Привязка настраивается с помощью стандартного [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) элемент, который по умолчанию использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="e5e6c-112">В этом образце атрибуту `clientCredentialType` присваивается значение Certificate для запроса проверки подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="e5e6c-113">Поведение задает учетные данные службы, используемые при проверке подлинности службы клиентом.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="e5e6c-114">Имя субъекта сертификата сервера задается в `findValue` атрибут в [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="e5e6c-115">Конфигурация конечной точки клиента состоит из абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="e5e6c-116">Привязка клиента настраивается с помощью соответствующих режимов безопасности и проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="e5e6c-117">Если сценарий выполняется на нескольких компьютерах, убедитесь, что адрес конечной точки службы изменен соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e5e6c-118">Реализация клиента позволяет задать сертификат для использования посредством файла конфигурации или кода.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="e5e6c-119">В следующем образце показано, как задать сертификат для использования в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e5e6c-120">В следующем образце показано, как вызвать службу в программе.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="e5e6c-121">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e5e6c-122">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e5e6c-123">Пакетный файл Setup.bat, входящий в состав образцов реализации безопасности сообщений, позволяет настроить для клиента и сервера соответствующие сертификаты, необходимые для выполнения размещенного приложения, для которого требуется обеспечение безопасности на основе сертификата.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="e5e6c-124">Пакетный файл можно выполнять в трех режимах.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="e5e6c-125">Для запуска в режиме одного компьютера, введите **setup.bat** в командную строку разработчика для Visual Studio; в режиме службы введите **setup.bat service**; и в режиме клиента введите **setup.bat client**.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="e5e6c-126">Режимы клиента и сервера используются для выполнения образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="e5e6c-127">Подробные сведения см. в описании процедуры настройки в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="e5e6c-128">Ниже представлен краткий обзор различных разделов пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
-   <span data-ttu-id="e5e6c-129">Создание сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="e5e6c-130">Следующая строка пакетного файла создает сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="e5e6c-131">В качестве имени субъекта создаваемого сертификата используется указанное имя клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="e5e6c-132">Сертификат сохраняется в хранилище `My` в расположении `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="e5e6c-133">Установка сертификата клиента в хранилище доверенных сертификатов сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="e5e6c-134">Следующая строка пакетного файла копирует сертификат клиента в хранилище TrustedPeople сервера, чтобы сервер мог принимать соответствующие решения о доверии или недоверии.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="e5e6c-135">Чтобы установленный в хранилище TrustedPeople сертификат был доверенным для службы Windows Communication Foundation (WCF), режима проверки сертификата клиента должно быть присвоено `PeerOrChainTrust` или `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="e5e6c-136">Чтобы узнать, как это сделать с помощью файла конфигурации, см. приведенный выше образец конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   <span data-ttu-id="e5e6c-137">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="e5e6c-138">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="e5e6c-139">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="e5e6c-140">Сертификат хранится в хранилище LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="e5e6c-141">Если пакетный файл Setup.bat запускается с аргументом service (например, **setup.bat service**), % SERVER_NAME % содержит полное доменное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e5e6c-142">В противном случае по умолчанию используется значение localhost.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-142">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="e5e6c-143">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="e5e6c-144">Следующая строка копирует сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e5e6c-145">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e5e6c-146">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="e5e6c-147">Предоставление разрешений в отношении закрытого ключа сертификата.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="e5e6c-148">Следующие строки файла Setup.bat открывают доступ к сертификату сервера, расположенному в хранилище LocalMachine, для учетной записи рабочего процесса [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5e6c-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e5e6c-149">Если используется в англоязычном (не американском) выпуске Windows, необходимо изменить файл Setup.bat и заменить имя учетной записи «NT AUTHORITY\NETWORK SERVICE» своим региональным эквивалентом.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5e6c-150">Средства, используемые в этом пакетном файле, расположены в каталоге C:\Program Files\Microsoft Visual Studio 8\Common7\tools или C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="e5e6c-151">Один из этих каталогов должен быть указан в системном пути.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="e5e6c-152">Если у вас установлена среда Visual Studio, чтобы открыть командную строку разработчика для Visual Studio является самым простым способом получения этого каталога в пути.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="e5e6c-153">Нажмите кнопку **запустить**, а затем выберите **все программы**, **Visual Studio 2012**, **средства**.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="e5e6c-154">В командной строке уже должны быть настроены соответствующие пути.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="e5e6c-155">В противном случае необходимо вручную добавить соответствующий каталог в путь.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5e6c-156">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e5e6c-157">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e5e6c-158">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5e6c-159">Этот образец находится в следующем каталоге:</span><span class="sxs-lookup"><span data-stu-id="e5e6c-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e5e6c-160">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="e5e6c-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e5e6c-161">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e5e6c-162">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e5e6c-163">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="e5e6c-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="e5e6c-164">Откройте командную строку разработчика для Visual Studio с правами администратора и запустите файл Setup.bat из папки установки образца.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="e5e6c-165">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5e6c-166">Пакетный файл Setup.bat предназначен для запуска из командной строки разработчика для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="e5e6c-167">Необходимо, чтобы переменная среды path указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="e5e6c-168">Эта переменная среды автоматически устанавливается в командную строку разработчика для Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="e5e6c-169">Проверка доступа к службе с помощью браузера, введя адрес `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="e5e6c-170">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e5e6c-171">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="e5e6c-172">Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e5e6c-173">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="e5e6c-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="e5e6c-174">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-174">Create a directory on the service computer.</span></span> <span data-ttu-id="e5e6c-175">Создайте для этого каталога виртуальное приложение servicemodelsamples, с помощью средства управления службами IIS.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="e5e6c-176">Скопируйте файлы служебной программы из каталога «\inetpub\wwwroot\servicemodelsamples» в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="e5e6c-177">Убедитесь, что скопированы все файлы из подкаталога \bin.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="e5e6c-178">Также скопируйте файлы Setup.bat, Cleanup.bat и ImportClientCert.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e5e6c-179">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="e5e6c-180">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="e5e6c-181">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="e5e6c-182">На сервере, запустите **setup.bat service** в командную строку разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="e5e6c-183">Под управлением **setup.bat** с **службы** аргумент создается сертификат службы с полным доменным именем компьютера и экспортируется в файл с именем Service.cer.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="e5e6c-184">Изменение файла Web.config в соответствии с новым именем сертификата (в `findValue` атрибут в [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) которого совпадает со значением полное доменное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="e5e6c-185">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="e5e6c-186">На стороне клиента, выполните **setup.bat client** в командную строку разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="e5e6c-187">Под управлением **setup.bat** с **клиента** аргумент создается сертификат клиента с именем client.com и этот сертификат клиента экспортируется в файл с именем Client.cer.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="e5e6c-188">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="e5e6c-189">Для этого замените имя localhost полным доменным именем сервера.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="e5e6c-190">Скопируйте файл Client.cer из клиентского каталога в каталог службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="e5e6c-191">На стороне клиента запустите файл ImportServiceCert.bat в командную строку разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="e5e6c-192">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="e5e6c-193">На сервере запустите файл ImportClientCert.bat в командную строку разработчика для Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="e5e6c-194">При этом импортируется сертификат клиента из файла Client.cer в хранилище «LocalMachine - TrustedPeople».</span><span class="sxs-lookup"><span data-stu-id="e5e6c-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="e5e6c-195">На клиентском компьютере из окна командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="e5e6c-196">Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e5e6c-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e5e6c-197">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="e5e6c-197">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="e5e6c-198">После завершения работы образца запустите в папке образцов файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5e6c-199">Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="e5e6c-200">При запуске примеров Windows Communication Foundation (WCF), которые используют сертификаты на компьютерах, обязательно удалите сертификаты службы, которые были установлены в хранилище CurrentUser - trustedpeople.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e5e6c-201">Чтобы сделать это, используйте следующую команду: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e5e6c-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
