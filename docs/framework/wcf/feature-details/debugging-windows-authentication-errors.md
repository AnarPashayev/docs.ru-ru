---
title: Отладка ошибок проверки подлинности Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: 20ca8f049298f75412da4c8a7e58975954f67741
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968861"
---
# <a name="debugging-windows-authentication-errors"></a>Отладка ошибок проверки подлинности Windows
При использовании в качестве механизма обеспечения безопасности проверки подлинности Windows процессы безопасности обрабатываются интерфейсом поставщика поддержки безопасности SSPI. При возникновении ошибок безопасности на уровне SSPI они выводятся Windows Communication Foundation (WCF). В этом разделе описаны общие принципы и некоторые вопросы, помогающие диагностировать такие ошибки.  
  
 Общие сведения о протоколе Kerberos см. в статье [Описание](https://go.microsoft.com/fwlink/?LinkID=86946)протокола Kerberos. Общие сведения о SSPI см. в разделе [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Для проверки подлинности Windows в WCF обычно используется поставщик услуг безопасности *Negotiate* , который выполняет взаимную проверку подлинности Kerberos между клиентом и службой. Если протокол Kerberos недоступен, WCF по умолчанию переходит к диспетчеру NT LAN Manager (NTLM). Однако можно настроить WCF для использования только протокола Kerberos (и исключения, если протокол Kerberos недоступен). Можно также настроить WCF для использования ограниченных форм протокола Kerberos.  
  
## <a name="debugging-methodology"></a>Методология отладки  
 Базовый метод отладки состоит в следующем.  
  
1. Определите, используется ли проверка подлинности Windows. Если используется какая-либо другая схема, этот раздел неприменим к такому сценарию.  
  
2. Если вы уверены, что используете проверку подлинности Windows, определите, использует ли конфигурация WCF Direct или Negotiate.  
  
3. После определения протокола, который используется в текущей конфигурации (Kerberos или NTLM), можно рассматривать сообщения об ошибках в правильном контексте.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Доступность протокола Kerberos и NTLM  
 Поставщику SSP Kerberos необходимо, чтоб контроллер домена выступал в роли центра распространения ключей Kerberos. Протокол Kerberos доступен только в том случае, если и клиент, и служба используют удостоверения домена. При других сочетаниях учетных записей используется протокол NTLM, что подтверждается следующей таблицей.  
  
 В заголовке таблицы приведены возможные типы учетных записей, используемые сервером. В левом столбце приведены возможные типы учетных записей, используемые клиентом.  
  
||Локальный пользователь|локальная система;|Пользователь домена|Компьютер домена|  
|-|----------------|------------------|-----------------|--------------------|  
|Локальный пользователь|NTLM|NTLM|NTLM|NTLM|  
|локальная система;|Anonymous NTLM|Anonymous NTLM|Anonymous NTLM|Anonymous NTLM|  
|Пользователь домена|NTLM|NTLM|Kerberos|Kerberos|  
|Компьютер домена|NTLM|NTLM|Kerberos|Kerberos|  
  
 Здесь четыре типа учетных записей включают:  
  
- Локальный пользователь: Профиль пользователя только для компьютера. Пример: `MachineName\Administrator` или `MachineName\ProfileName`.  
  
- Локальная система: Встроенная система учетных записей на компьютере, который не присоединен к домену.  
  
- Пользователь домена: Учетная запись пользователя в домене Windows. Например, `DomainName\ProfileName`.  
  
- Компьютер домена: Процесс с удостоверением компьютера, работающим на компьютере, присоединенном к домену Windows. Например, `MachineName\Network Service`.  
  
> [!NOTE]
> Получение учетных данных службы происходит при вызове метода <xref:System.ServiceModel.ICommunicationObject.Open%2A> класса <xref:System.ServiceModel.ServiceHost>. Чтение учетных данных клиента происходит всякий раз, когда клиент отправляет сообщение.  
  
## <a name="common-windows-authentication-problems"></a>Распространенные проблемы проверки подлинности Windows  
 В этом разделе описаны некоторые распространенные проблемы проверки подлинности Windows и возможные решения.  
  
### <a name="kerberos-protocol"></a>Протокол Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Проблемы SPN/UPN, возникающие при использовании протокола Kerberos  
 Если при проверке подлинности Windows используется протокол Kerberos, или он выбирается с помощью интерфейса SSPI, URL-адрес, используемый конечной точкой клиента, должен включать полное доменное имя узла службы внутри URL-адреса службы. Предполагается, что у учетной записи, от имени которой запущена служба, есть доступ к ключу (имени участника-службы) (по умолчанию), который создается при добавлении компьютера в домен Active Directory, что чаще всего выполняется путем запуска службы в Учетная запись сетевой службы. Если у службы нет доступа к ключу имени участника-службы этого компьютера, необходимо предоставить правильное имя участника-службы или имя участника-пользователя (UPN) учетной записи, под которой выполняется служба в удостоверении конечной точки клиента. Дополнительные сведения о том, как WCF работает с SPN и UPN, см. в статье [удостоверение службы и проверка](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)подлинности.  
  
 В сценариях с балансировкой нагрузки, например при использовании веб-ферм или веб-садов, распространена практика определения уникальной учетной записи для каждого из приложений, назначения этой учетной записи имени участника-службы и контроль за тем, чтобы все службы приложения выполнялись от имени этой учетной записи.  
  
 Чтобы получить для учетной записи службы имя участника-службы, нужны права администратора домена Active Directory. Дополнительные сведения см. в статье [техническое дополнение Kerberos для Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Для непосредственного применения протокола Kerberos необходимо, чтобы служба выполнялась от имени учетной записи компьютера домена  
 Такая ситуация возникает, когда свойство `ClientCredentialType` имеет значение `Windows`, а свойство <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> - `false`, как показано в следующем примере кода.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Чтобы решить эту проблему, запустите службу от имени учетной записи компьютера домена, например учетной записи Network Service, на компьютере, входящем в домен.  
  
### <a name="delegation-requires-credential-negotiation"></a>Для делегирования требуется согласование учетных данных  
 Для использования протокола проверки подлинности Kerberos с делегированием необходимо реализовать протокол Kerberos с согласованием учетных данных (иногда называется многоступенчатой проверкой подлинности Kerberos). Если проверка подлинности Kerberos реализована без согласования учетных данных (иногда называется одноступенчатой проверкой подлинности Kerberos), возникает исключение.  
  
 Чтобы реализовать протокол Kerberos с согласованием учетных данных, выполните следующие действия.  
  
1. Реализуйте делегирование, присвоив свойству <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> значение <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2. Потребуйте согласования SSPI:  
  
    1. если используются стандартные привязки, установите свойство `NegotiateServiceCredential` равным `true`;  
  
    2. если используются пользовательские привязки, установите атрибут `AuthenticationMode` элемента `Security` равным `SspiNegotiated`.  
  
3. Потребуйте, чтобы при согласовании SSPI использовался протокол Kerberos, запретив использование NTLM:  
  
    1. для этого в коде воспользуйтесь инструкцией: `ChannelFactory.Credentials.Windows.AllowNtlm = false`;  
  
    2. либо в файле конфигурации установите атрибут `allowNtlm` равным `false`. Этот атрибут содержится в [ \<> Windows](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Протокол NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>В результате согласования SSP используется протокол NTLM, хотя протокол NTLM отключен  
 Свойству присвоено значение, которое приводит к тому, что Windows Communication Foundation (WCF) наилучшим образом выдавать исключение, если используется NTLM. `false` <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Обратите внимание, что установка для данного свойства значения `false` не предотвращает отправки учетных данных NTLM по сети.  
  
 Ниже показано, как отключить переключение к протоколу NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Сбой входа NTLM  
 Учетные данные клиента недействительны на стороне службы. Проверьте, что имя пользователя и пароль заданы правильно и соответствуют учетной записи, которая известна компьютеру, на котором выполняется служба. Протокол NTLM использует указанные учетные данные для входа на компьютер службы. Хотя эти учетные данные могут быть недействительными на компьютере клиента, сбой входа произойдет, если они будут недействительными на компьютере службы.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Происходит анонимный вход NTLM, хотя по умолчанию анонимный вход отключен  
 При создании клиента свойство <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> устанавливается равным <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, как показано в следующем примере кода, но по умолчанию сервер запрещает анонимный вход. Это происходит потому, что свойство <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> класса <xref:System.ServiceModel.Security.WindowsServiceCredential> по умолчанию имеет значение `false`.  
  
 Следующий код клиента пытается включить анонимный вход (обратите внимание, что по умолчанию свойство имеет значение `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Следующий код службы изменяет значение по умолчанию, чтобы разрешить анонимный вход сервера.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Дополнительные сведения об олицетворении см. в разделе [Делегирование и олицетворение](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Либо клиент может выполняться в качестве службы Windows от имени встроенной учетной записи SYSTEM.  
  
### <a name="other-problems"></a>Другие проблемы  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Учетные данные клиента заданы неверно  
 При проверке подлинности Windows используется экземпляр <xref:System.ServiceModel.Security.WindowsClientCredential>, возвращаемый свойством <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> класса <xref:System.ServiceModel.ClientBase%601>, а не экземпляр <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Ниже приведен пример с ошибкой.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Ниже приведен пример без ошибки.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Интерфейс SSPI недоступен  
 Следующие операционные системы не поддерживают проверку подлинности Windows при использовании в качестве сервера: [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Выпуск Home Edition [!INCLUDE[wxp](../../../../includes/wxp-md.md)] , Media Center Edition и [!INCLUDE[wv](../../../../includes/wv-md.md)]домашние выпуски.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Разработка и развертывание с использованием различных удостоверений  
 В случае разработки приложения на одном компьютере и его развертывания на другом компьютере с использованием для проверки подлинности на каждом из компьютеров учетных записей различных типов работа приложения может различаться. Предположим, приложение разрабатывается на компьютере под управлением Windows XP Professional Edition с использованием режима проверки подлинности `SSPI Negotiated`. Если для проверки подлинности используется учетная запись локального пользователя, будет использоваться протокол NTLM. После разработки приложения служба развертывается на компьютере под управлением Windows Server 2003, где она выполняется от имени учетной записи домена. В этом случае клиент не сможет пройти проверку подлинности на стороне службы, поскольку будут использоваться протокол Kerberos и контроллер домена.  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Делегирование и олицетворение](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Неподдерживаемые сценарии](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
