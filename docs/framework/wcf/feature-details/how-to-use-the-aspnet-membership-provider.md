---
title: Практическое руководство. Использование поставщика членства ASP.NET
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 840e4a5d365f2adbaf335c1061a580665a39824d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595327"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Практическое руководство. Использование поставщика членства ASP.NET

Поставщик членства ASP.NET — это функция, позволяющая разработчикам ASP.NET создавать веб-сайты, позволяющие пользователям создавать уникальные сочетания имени пользователя и пароля. Эта функция позволяет любому пользователю создавать на узле учетную запись и при входе получать монопольный доступ к узлу и его службам. В этом заключается отличие от безопасности Windows, по условиям которой пользователи обязаны создавать ученые записи в домене Windows. Вместо этого любой пользователь, предоставляющий свои учетные данные (сочетание имени пользователя и пароля), может использовать сайт и его службы.

Пример приложения см. в разделе [поставщик членства и роли](../samples/membership-and-role-provider.md). Сведения об использовании функции поставщика ролей ASP.NET см. в разделе [как использовать поставщик ролей ASP.NET со службой](how-to-use-the-aspnet-role-provider-with-a-service.md).

Возможность членства требует использования базы данных SQL Server для хранения сведений о пользователе. Эта возможность также включает методы напоминания пользователю его пароля с помощью специального вопроса.

Разработчики Windows Communication Foundation (WCF) могут воспользоваться преимуществами этих функций в целях обеспечения безопасности. При интеграции в приложение WCF пользователи должны указать сочетание имени пользователя и пароля для клиентского приложения WCF. Чтобы переместить данные в службу WCF, используйте привязку, которая поддерживает учетные данные имени пользователя и пароля, например <xref:System.ServiceModel.WSHttpBinding> (в конфигурации [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ), и задайте для параметра Тип учетных данных клиента значение `UserName` . В службе безопасность WCF проверяет подлинность пользователя на основе имени пользователя и пароля, а также назначает роль, заданную ролью ASP.NET.

> [!NOTE]
> WCF не предоставляет методы для заполнения базы данных сочетаниями имени пользователя и пароля или других сведений о пользователе.

### <a name="to-configure-the-membership-provider"></a>Настройка поставщика членства

1. В файле Web. config в `system.web` элементе < > Создайте `membership` элемент > <.

2. В элементе `<membership>`.

3. В качестве дочернего элемента для <`providers`> добавьте `<clear />` элемент для очистки коллекции поставщиков.

4. В `<clear />` элементе создайте `add` элемент <> со следующими атрибутами, для которых заданы соответствующие значения: `name` , `type` ,,,, `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` , `requiresQuestionAndAnswer` , `requiresUniqueEmail` и `passwordFormat` . Атрибут `name` используется далее в качестве значения в файле конфигурации. В следующем примере задается значение `SqlMembershipProvider`.

    В следующем примере демонстрируется раздел конфигурации.

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Настройка системы безопасности службы на прием сочетания имя/пароль пользователя

1. В файле конфигурации в [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) элементе добавьте [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) элемент.

2. Добавьте в [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) раздел привязок. Дополнительные сведения о создании элемента привязки WCF см. в разделе [инструкции. Указание привязки службы в конфигурации](../how-to-specify-a-service-binding-in-configuration.md).

3. Задайте атрибуту `mode` элемента `<security>` значение `Message`.

4. Задайте `clientCredentialType` `message` для атрибута элемента> <значение `UserName` . В этом случае пара "имя пользователя и пароль" будет использоваться в качестве учетной записи клиента.

    В следующем примере показан код конфигурации для привязки.

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Настройка службы на использование поставщика членства

1. `<system.serviceModel>`Добавьте элемент в качестве дочернего элемента [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)

2. Добавьте в [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` элемент> <.

3. Добавьте [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) и задайте `name` для атрибута соответствующее значение.

4. Добавьте в [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) `behavior` элемент> <.

5. Добавьте в [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>` элемент.

6. Задайте для атрибута `userNamePasswordValidationMode` значение `MembershipProvider`.

    > [!IMPORTANT]
    > Если `userNamePasswordValidationMode` значение не задано, WCF использует проверку подлинности Windows вместо поставщика членства ASP.NET.

7. Задайте для атрибута `membershipProviderName` значение "имя поставщика" (указывается при добавлении поставщика в первой процедуре данного раздела). В следующем примере показан фрагмент `<serviceCredentials>`, иллюстрирующий вышеуказанные действия.

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>Пример

В следующем коде показана конфигурация службы, использующей возможность членства в ASP.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Дополнительно

- [Практическое руководство. Использование поставщика ролей ASP.NET со службой](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Поставщик членства и ролей](../samples/membership-and-role-provider.md)
