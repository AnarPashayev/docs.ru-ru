---
title: Упрощенная конфигурация служб WCF
description: Узнайте, как реализовать и настроить типичную службу и клиент с помощью WCF. Служба взаимодействует с помощью конечной точки, указанной в файле конфигурации.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246224"
---
# <a name="simplified-configuration-for-wcf-services"></a>Упрощенная конфигурация служб WCF
В этом примере показано, как реализовать и настроить типичную службу и клиент с помощью Windows Communication Foundation (WCF). Этот образец является основой для всех остальных базовых образцов технологий.  
  
 Эта служба, которая предоставляет конечную точку для взаимодействия со службой, использует упрощенную конфигурацию в .NET Framework 4. До .NET Framework 4 конечная точка обычно определяется в файле конфигурации (Web.config), как показано в следующем примере кода конфигурации.  
  
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
  
 В .NET Framework 4 `<service>` элемент является необязательным. Если конечные точки не заданы в службе, то к службе добавляется конечная точка для каждого базового адреса и реализованного контракта. Базовый адрес добавляется к имени контракта для определения конечной точки, и привязка определяется с помощью схемы адреса. В следующем примере кода показан файл упрощенной конфигурации. Как настроено, доступ к службе может осуществляться `http://localhost/servicemodelsamples/service.svc` клиентом на том же компьютере. Чтобы к службе могли получить доступ клиенты на удаленных компьютерах, вместо имени localhost необходимо указать полное имя домена. По умолчанию служба не предоставляет метаданных. При этом служба включает поведение <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
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
  
1. Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).  
  
3. Запустите образец, выполнив следующие шаги.  
  
    1. Щелкните правой кнопкой мыши проект **службы** и выберите **Назначить запускаемым проектом**, а затем нажмите клавиши **CTRL + F5**.  
  
    2. Дождитесь вывода данных на консоли, подтверждающих запуск и выполнение службы.  
  
    3. Щелкните правой кнопкой мыши проект **клиента** и выберите **Назначить запускаемым проектом**, а затем нажмите клавиши **CTRL + F5**.  
  
> [!IMPORTANT]
> Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>См. также

- [Образцы управления AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Упрощенная конфигурация](../simplified-configuration.md)
