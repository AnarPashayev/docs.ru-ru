---
title: Упрощенная конфигурация служб WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 57aa92eb0a2978ab463c368ed70fb298cc5fb90d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038864"
---
# <a name="simplified-configuration-for-wcf-services"></a>Упрощенная конфигурация служб WCF
В этом примере показано, как реализовать и настроить типичную службу и клиент с помощью Windows Communication Foundation (WCF). Этот образец является основой для всех остальных базовых образцов технологий.  
  
 Эта служба, которая предоставляет конечную точку для взаимодействия со службой, использует упрощенную конфигурацию в [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. До [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] конечная точка определяется в файле конфигурации (Web.config). См. следующий пример кода конфигурации.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 В [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] элемент `<service>` является необязательным. Если конечные точки не заданы в службе, то к службе добавляется конечная точка для каждого базового адреса и реализованного контракта. Базовый адрес добавляется к имени контракта для определения конечной точки, и привязка определяется с помощью схемы адреса. В следующем примере кода показан файл упрощенной конфигурации. Как настроено, доступ к службе может осуществляться `http://localhost/servicemodelsamples/service.svc` клиентом на том же компьютере. Чтобы к службе могли получить доступ клиенты на удаленных компьютерах, вместо имени localhost необходимо указать полное имя домена. По умолчанию служба не предоставляет метаданных. При этом служба включает поведение <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Использование этого образца  
  
1. Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Запустите образец, выполнив следующие шаги.  
  
    1. Щелкните правой кнопкой мыши проект **службы** и выберите **Назначить запускаемым проектом**, а затем нажмите клавиши **CTRL + F5**.  
  
    2. Дождитесь вывода данных на консоли, подтверждающих запуск и выполнение службы.  
  
    3. Щелкните правой кнопкой мыши проект **клиента** и выберите **Назначить запускаемым проектом**, а затем нажмите клавиши **CTRL + F5**.  
  
> [!IMPORTANT]
> Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры. Этот образец расположен в следующем каталоге.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>См. также

- [Примеры управления AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
- [Упрощенная конфигурация](../../../../docs/framework/wcf/simplified-configuration.md)
