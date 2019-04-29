---
title: Структура проверки подлинности маркера
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 501f1801c1cb475a87c586f8bbc14146b9141047
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779175"
---
# <a name="token-authenticator"></a><span data-ttu-id="6475c-102">Структура проверки подлинности маркера</span><span class="sxs-lookup"><span data-stu-id="6475c-102">Token Authenticator</span></span>
<span data-ttu-id="6475c-103">Данный образец демонстрирует способ реализации пользовательской структуры проверки подлинности маркеров.</span><span class="sxs-lookup"><span data-stu-id="6475c-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="6475c-104">Маркер проверки подлинности в Windows Communication Foundation (WCF) используется для проверки маркера, используемого с сообщением, проверка того, что является согласованным и проверки подлинности идентификации связанное с маркером.</span><span class="sxs-lookup"><span data-stu-id="6475c-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="6475c-105">Пользовательские структуры проверки подлинности маркера могут быть полезны в различных случаях, а именно:</span><span class="sxs-lookup"><span data-stu-id="6475c-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="6475c-106">при возникновении необходимости переопределения механизма проверки подлинности по умолчанию, связанного с маркером;</span><span class="sxs-lookup"><span data-stu-id="6475c-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="6475c-107">при построении пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="6475c-107">When you are building a custom token.</span></span>

 <span data-ttu-id="6475c-108">В этом образце демонстрируется следующее:</span><span class="sxs-lookup"><span data-stu-id="6475c-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="6475c-109">как клиент может проходить проверку подлинности с использованием пары "имя пользователя/пароль";</span><span class="sxs-lookup"><span data-stu-id="6475c-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="6475c-110">как сервер может проверить учетные данные клиента с помощью пользовательской структуры проверки подлинности маркера;</span><span class="sxs-lookup"><span data-stu-id="6475c-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="6475c-111">Как код службы WCF механизму проверки подлинности пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="6475c-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="6475c-112">как сервер может проходить проверку подлинности с помощью сертификата X.509 сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="6475c-113">В этом примере также показано, как удостоверение вызывающей стороны, доступен из WCF после завершения процесса проверки подлинности пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="6475c-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="6475c-114">Служба предоставляет одну конечную точку для взаимодействия со службой, определенной в файле конфигурации App.config.</span><span class="sxs-lookup"><span data-stu-id="6475c-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="6475c-115">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="6475c-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6475c-116">Привязка настроена со стандартной привязкой `wsHttpBinding`, режимом безопасности, заданным для сообщения - режимом по умолчанию привязки `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="6475c-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="6475c-117">В этом образце стандартная привязка `wsHttpBinding` использует проверку подлинности имени пользователя клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="6475c-118">Кроме того, служба настраивает сертификат службы с помощью поведения `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="6475c-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="6475c-119">Поведение `securityCredentials` позволяет указать на сертификат службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="6475c-120">Сертификат службы используется клиентом для проверки подлинности службы и обеспечения защиты сообщения.</span><span class="sxs-lookup"><span data-stu-id="6475c-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="6475c-121">В следующей конфигурации делается ссылка на сертификат localhost, установленный во время установки образца, как описано в инструкциях по установке далее.</span><span class="sxs-lookup"><span data-stu-id="6475c-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="6475c-122">Конфигурация конечной точки клиента состоит из имени конфигурации, абсолютного адреса конечной точки службы, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="6475c-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="6475c-123">Привязка клиента настраивается с помощью соответствующих `Mode` и `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="6475c-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 <span data-ttu-id="6475c-124">Реализация клиента задает используемые имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="6475c-124">The client implementation sets the user name and password to use.</span></span>

```
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="6475c-125">Пользовательская структура проверки подлинности маркера</span><span class="sxs-lookup"><span data-stu-id="6475c-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="6475c-126">Для создания структуры проверки подлинности пользовательского маркера выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="6475c-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="6475c-127">Запишите структуру проверки подлинности пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="6475c-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="6475c-128">Образец реализует структуру проверки подлинности пользовательского маркера, которая проверяет, что имя пользователя имеет действительный формат адреса электронной почты.</span><span class="sxs-lookup"><span data-stu-id="6475c-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="6475c-129">Она наследуется от <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="6475c-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="6475c-130">Наиболее важным методом в данном классе является <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="6475c-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="6475c-131">В данном методе структура проверки подлинности проверяет формат имени пользователя, а также имя узла на предмет законности домена.</span><span class="sxs-lookup"><span data-stu-id="6475c-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="6475c-132">Если оба условия удовлетворены, то возвращается доступная только для чтения коллекция экземпляров <xref:System.IdentityModel.Policy.IAuthorizationPolicy>, которая затем используется для предоставления утверждений, представляющих информацию, хранящуюся внутри маркера имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="6475c-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="6475c-133">Предоставьте политику авторизации, возвращаемую пользовательской структурой проверки подлинности маркера.</span><span class="sxs-lookup"><span data-stu-id="6475c-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="6475c-134">В этом образце приводится собственная реализация политики <xref:System.IdentityModel.Policy.IAuthorizationPolicy>, называемой `UnconditionalPolicy`, которая возвращает набор утверждений и удостоверений, которые были переданы ей в ее конструкторе.</span><span class="sxs-lookup"><span data-stu-id="6475c-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="6475c-135">Запишите пользовательский диспетчер маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="6475c-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="6475c-136">Класс <xref:System.IdentityModel.Selectors.SecurityTokenManager> используется для создания объекта <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> для конкретных объектов <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, которые передаются в него в методе `CreateSecurityTokenAuthenticator`.</span><span class="sxs-lookup"><span data-stu-id="6475c-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="6475c-137">Диспетчер маркеров безопасности также используется для создания поставщиков маркеров и сериализаторов маркеров. В этом образце они не представлены.</span><span class="sxs-lookup"><span data-stu-id="6475c-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="6475c-138">В данном образце пользовательский диспетчер маркеров безопасности наследуется от класса <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> и переопределяет метод `CreateSecurityTokenAuthenticator`, возвращающий пользовательскую структуру проверки подлинности маркера имени пользователя, когда переданные требования маркера указывают на запрос структуры проверки подлинности имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="6475c-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="6475c-139">Запишите пользовательские учетные данные службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-139">Write a custom service credential.</span></span>

     <span data-ttu-id="6475c-140">Класс учетных данных службы используется для представления учетных данных, которые сконфигурированы для службы, и создает диспетчер маркеров безопасности, который используется для получения структур проверки подлинности маркеров, поставщиков маркеров и сериализаторов маркеров.</span><span class="sxs-lookup"><span data-stu-id="6475c-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="6475c-141">Настройте службу для использования пользовательских учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="6475c-142">Для того чтобы служба использовала пользовательские учетные данные службы, нужно удалить класс учетных данных службы по умолчанию после перехвата сертификата службы, который уже предварительно настроен в учетных данных службы по умолчанию. Затем необходимо настроить новый экземпляр учетных данных для использования предварительно настроенных сертификатов службы и добавить этот новый экземпляр учетных данных службы в поведения службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="6475c-143">Для вывода информации об абоненте можно использовать свойство <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="6475c-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="6475c-144">Свойство <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> содержит информацию об утверждениях о текущем вызывающем модуле.</span><span class="sxs-lookup"><span data-stu-id="6475c-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="6475c-145">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6475c-146">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="6475c-147">Пакетный файл Setup</span><span class="sxs-lookup"><span data-stu-id="6475c-147">Setup Batch File</span></span>
 <span data-ttu-id="6475c-148">Входящий в состав образца пакетный файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="6475c-149">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="6475c-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="6475c-150">Ниже представлен краткий обзор различных разделов пакетных файлов, позволяющий изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6475c-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="6475c-151">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-151">Creating the server certificate.</span></span>

     <span data-ttu-id="6475c-152">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="6475c-153">Переменная `%SERVER_NAME%`задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="6475c-154">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="6475c-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="6475c-155">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="6475c-155">The default in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6475c-156">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="6475c-157">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6475c-158">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="6475c-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6475c-159">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="6475c-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="6475c-160">Пакетный файл Setup предназначен для запуска из командной строки Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="6475c-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="6475c-161">Требуется, чтобы переменная среды MSSDK указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="6475c-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6475c-162">Эта переменная среды автоматически устанавливается в командной строке Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="6475c-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="6475c-163">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="6475c-163">To set up and build the sample</span></span>

1. <span data-ttu-id="6475c-164">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6475c-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6475c-165">Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6475c-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6475c-166">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="6475c-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6475c-167">Запустите файл Setup.bat из папки установки образца командную строку Visual Studio 2012, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="6475c-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="6475c-168">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="6475c-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="6475c-169">Пакетный файл Setup.bat предназначен для запуска из командной строки с 2012 Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6475c-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="6475c-170">Набор переменных среды в командной строке Visual Studio 2012 путь указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="6475c-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="6475c-171">Запустите программу Service.exe из каталога \service\bin.</span><span class="sxs-lookup"><span data-stu-id="6475c-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="6475c-172">Запустите программу Client.exe из \client\bin.</span><span class="sxs-lookup"><span data-stu-id="6475c-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="6475c-173">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="6475c-174">Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6475c-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6475c-175">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="6475c-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6475c-176">Создайте на компьютере службы каталог для двоичных файлов службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="6475c-177">Скопируйте файлы служебной программы в каталог службы на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="6475c-178">Кроме того, скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="6475c-179">Необходимо иметь сертификат сервера с именем субъекта, содержащим полное имя домена компьютера.</span><span class="sxs-lookup"><span data-stu-id="6475c-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="6475c-180">Для отображения этого нового имени сертификата необходимо обновить файл службы App.config.</span><span class="sxs-lookup"><span data-stu-id="6475c-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="6475c-181">Можно создать его с помощью файла Setup.bat, если переменной `%SERVER_NAME%` присвоено полное имя узла компьютера, на котором будет работать служба.</span><span class="sxs-lookup"><span data-stu-id="6475c-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="6475c-182">Обратите внимание на то, что файл setup.bat нужно запускать из командной строки разработчика для Visual Studio, открытой с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="6475c-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="6475c-183">Скопируйте сертификат сервера в хранилище CurrentUser-TrustedPeople клиента.</span><span class="sxs-lookup"><span data-stu-id="6475c-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="6475c-184">Это нужно делать только тогда, когда сертификат сервера выдан центром выдачи, которому доверяет клиент.</span><span class="sxs-lookup"><span data-stu-id="6475c-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="6475c-185">В файле App.config компьютера службы измените значение базового адреса для указания полного имени компьютера вместо localhost.</span><span class="sxs-lookup"><span data-stu-id="6475c-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="6475c-186">На компьютере службы запустите из командной строки программу service.exe.</span><span class="sxs-lookup"><span data-stu-id="6475c-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="6475c-187">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="6475c-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="6475c-188">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="6475c-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="6475c-189">На клиентском компьютере из командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="6475c-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="6475c-190">Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6475c-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6475c-191">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="6475c-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="6475c-192">После завершения работы примера запустите в папке примеров файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="6475c-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
