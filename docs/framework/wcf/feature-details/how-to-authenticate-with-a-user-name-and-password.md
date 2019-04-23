---
title: Практическое руководство. Проверка подлинности с использованием имени и пароля пользователя
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 11a146e387171d6af95a7710fe96d6f35f6c611f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321045"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Практическое руководство. Проверка подлинности с использованием имени и пароля пользователя

В этом разделе показано, как включить службу Windows Communication Foundation (WCF) для проверки подлинности клиента с помощью имени пользователя домена Windows и пароль. Предполагается, что это рабочая резидентная служба WCF. Пример создания основных резидентной службы WCF см [Приступая к работе](../../../../docs/framework/wcf/getting-started-tutorial.md). В этом разделе предполагается, что служба настраивается в коде. Если вы хотите см. в разделе Пример настройки похожей службы с помощью файла конфигурации см. в разделе [имя пользователя для безопасности сообщений](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Чтобы настроить службу для проверки подлинности клиентов по имени пользователя и паролю в домене Windows, используйте <xref:System.ServiceModel.WSHttpBinding>, установив свойство `Security.Mode` в значение `Message`. Кроме того, необходимо указать сертификат X509, который будет использован для шифрования имени пользователя и пароля, так как они передаются от клиента к службе.  
  
 На стороне клиента необходимо запрашивать у пользователя учетные данные и указать учетные данные пользователя в клиентском классе-посреднике WCF.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Чтобы настроить службу WCF для проверки подлинности имя пользователя домена Windows и пароль
  
1. Создайте экземпляр <xref:System.ServiceModel.WSHttpBinding>, установите режим безопасности привязки в <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, установите `ClientCredentialType` привязки в значение <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> и добавьте в узел службы конечную точку службы с помощью заданной привязки, как показано в следующем коде:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2. Задает сертификат сервера, используемый для шифрования имени пользователя и пароля, передаваемых по сети. Этот код должен непосредственно следовать за показанным выше кодом. В следующем примере используется сертификат, созданный файлом setup.bat из [имя пользователя безопасности сообщения](../../../../docs/framework/wcf/samples/message-security-user-name.md) пример:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Вы можете использовать собственный сертификат, просто укажите ссылку на него в коде. Дополнительные сведения о создании и использовании сертификатов см. в разделе [работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Убедитесь, что сертификат находится в хранилище сертификатов «Доверенные лица» для локального компьютера. Это можно сделать, запустив mmc.exe и выбрав **файл**, **добавить или удалить оснастку...**  пункта меню. В **Добавление или удаление оснасток** диалоговом окне выберите **оснастку сертификатов** и нажмите кнопку **добавить**. В диалоговом окне оснастке сертификатов выберите **учетная запись компьютера**. По умолчанию сертификат, сформированный из образца «Безопасность сообщений с использованием имени пользователя», будет находиться в папке «Личное или сертификаты».  Оно будет отображаться как «localhost» выпущен столбцу в окне MMC. Перетащите сертификат в **доверенные лица** папки. Это позволит WCF считать сертификат доверенным при выполнении проверки подлинности.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>Вызов службы с передачей имени пользователя и пароля  
  
1. Клиентское приложение должно предложить пользователю ввести имя пользователя и пароль. Следующий код запрашивает у пользователя имя пользователя и пароль.  
  
    > [!WARNING]
    >  Этот код не следует использовать в рабочей среде, так как пароль во время ввода отображается на экране.  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2. Создайте экземпляр клиентского класса-посредника, указав учетные данные клиента, как показано в следующем коде:  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Безопасность транспорта с обычной проверкой подлинности](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [Защита распределенных приложений](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
