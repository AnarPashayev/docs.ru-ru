---
title: Безопасность сообщений с возможностью анонимного доступа
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: fe248c6fcb9db80b0ab8f62cc78a480e70803633
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756043"
---
# <a name="message-security-anonymous"></a>Безопасность сообщений с возможностью анонимного доступа
Образец Anonymous безопасности сообщения показано, как реализовать приложение, Windows Communication Foundation (WCF), использующей безопасность уровня сообщений без проверки подлинности клиента, но с требованием проверки подлинности сервера с использованием сертификата X.509 сервера сертификат. Все сообщения приложений, которыми обмениваются служба и клиент, подписываются и шифруются. Этот образец основан на [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) образца. Этот образец содержит консольную программу клиента (EXE) и библиотеку службы (DLL), размещаемую в службах IIS. Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".

> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.

 В этом образце в интерфейс калькулятора добавлена новая операция, возвращающая значение `True`, если клиент прошел проверку подлинности.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 Служба предоставляет одну конечную точку для взаимодействия с ней; конечная точка определяется в файле конфигурации (Web.config). Конечная точка состоит из адреса, привязки и контракта. Привязка сконфигурирована с использованием привязки `wsHttpBinding`. Режимом безопасности по умолчанию для привязки `wsHttpBinding` является `Message`. Для атрибута `clientCredentialType` устанавливается значение `None`.

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Учетные данные, используемые для проверки подлинности службы указываются в [ \<поведение >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Значение параметра `SubjectName`, содержащееся в сертификате сервера, должно совпадать со значением атрибута `findValue`, указанным следующем образце кода.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 Конфигурация конечной точки клиента состоит из абсолютного адреса конечной точки службы, привязки и контракта. Режимом безопасности клиента для привязки `wsHttpBinding` является `Message`. Для атрибута `clientCredentialType` устанавливается значение `None`.

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 В этом образце свойству <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> задается значение <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> для проверки подлинности сертификата службы. Его можно задать в файле App.config для клиента (в разделе `behaviors`). Это значение параметра обеспечивает, что если сертификат находится в хранилище пользователя "Доверенные лица", он признается доверенным без выполнения проверки цепочки издателей сертификата. В данном случает этот параметр используется для удобства, чтобы можно было выполнить образец без затребования сертификатов, выдаваемых центром сертификации. Этот параметр обеспечивает более низкий уровень безопасности, чем значение по умолчанию (ChainTrust). Прежде чем использовать параметр `PeerOrChainTrust` в рабочей среде, необходимо тщательно изучить связанные с этим проблемы безопасности.

 Реализация клиента добавляется вызов `IsCallerAnonymous` метод и в противном случае не будет отличаться от [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) образца.

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 При выполнении примера запросы и ответы операций отображаются в окне консоли клиента. Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Пакетный файл Setup.bat, входящий в состав образца реализации безопасности сообщений с возможностью анонимного доступа, позволяет настроить для сервера соответствующий сертификат, необходимый для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера. Пакетный файл можно выполнять в двух режимах. Чтобы выполнить пакетный файл в режиме одного компьютера, введите `setup.bat` в командной строке. Чтобы выполнить его в режиме службы, введите `setup.bat service`. Этот режим используется для выполнения образца на нескольких компьютерах. Подробные сведения см. в описании процедуры настройки в конце этого раздела.

 Ниже приводится краткое описание различных разделов пакетного файла.

- Создание сертификата сервера.

     Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Переменная %SERVER_NAME% задает имя сервера. Сертификат хранится в хранилище LocalMachine. Если пакетный файл Setup запускается с аргументом service (например, `setup.bat service`), переменная %SERVER_NAME% содержит полное имя домена компьютера. В противном случае по умолчанию используется значение localhost.

- Установка сертификата сервера в хранилище доверенных сертификатов клиента.

     Следующая строка копирует сертификат сервера в хранилище доверенных лиц клиента. Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы. Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Предоставление разрешений в отношении закрытого ключа сертификата.

     Следующие строки файла Setup.bat открывают доступ к сертификату сервера, расположенному в хранилище LocalMachine, для учетной записи рабочего процесса [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  Если используется в англоязычном (не американском) выпуске Windows, необходимо изменить файл Setup.bat и заменить имя учетной записи `NT AUTHORITY\NETWORK SERVICE` своим региональным эквивалентом.

### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца

1. Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Запуск образца на одном компьютере

1. Убедитесь, что путь включает папку, в которой хранятся файлы Makecert.exe и FindPrivateKey.exe.

2. Запустите файл Setup.bat из папки установки образца в командную строку разработчика для Visual Studio с правами администратора. При этом устанавливаются все сертификаты, необходимые для выполнения образца.

    > [!NOTE]
    > Пакетный файл setup предназначен для запуска из командной строки разработчика для Visual Studio. Необходимо, чтобы переменная среды path указывала на каталог, в котором установлен пакет SDK. Эта переменная среды автоматически устанавливается в командную строку разработчика для Visual Studio.  
  
3. Проверка доступа к службе с помощью браузера, введя адрес `http://localhost/servicemodelsamples/service.svc`.  
  
4. Запустите программу Client.exe из каталога \client\bin. Действия клиента отображаются в консольном приложении клиента.  
  
5. Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Запуск образца на нескольких компьютерах  
  
1. Создайте каталог на компьютере службы. Создайте для этого каталога виртуальное приложение servicemodelsamples, с помощью средства управления службами IIS.  
  
2. Скопируйте файлы служебной программы из каталога «\inetpub\wwwroot\servicemodelsamples» в виртуальный каталог на компьютере службы. Убедитесь, что скопированы все файлы из подкаталога \bin. Кроме того, скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.  
  
3. Создайте на клиентском компьютере каталог для двоичных файлов клиента.  
  
4. Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента. Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.  
  
5. На сервере, запустите `setup.bat service` в командную строку разработчика для Visual Studio, открытой с правами администратора. Под управлением `setup.bat` с `service` аргумент создается сертификат службы с полным доменным именем компьютера и экспортируется в файл с именем Service.cer.  
  
6. Изменение файла Web.config в соответствии с новым именем сертификата (в `findValue` атрибут в [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), который совпадает со значением полное доменное имя компьютера.  
  
7. Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.  
  
8. В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.  
  
9. На стороне клиента запустите файл ImportServiceCert.bat в командную строку разработчика для Visual Studio, открытой с правами администратора. Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.  
  
10. На клиентском компьютере из командной строки запустите программу Client.exe. Если клиент и служба не может взаимодействовать, см. в разделе [советы по устранению неполадок для образцов WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Очистка после образца  
  
- После завершения работы образца запустите в папке образцов файл Cleanup.bat.  
  
> [!NOTE]
>  Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах. При запуске примеров Windows Communication Foundation (WCF), которые используют сертификаты на компьютерах, обязательно удалите сертификаты службы, которые были установлены в хранилище CurrentUser - trustedpeople. Чтобы сделать это, используйте следующую команду: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`
