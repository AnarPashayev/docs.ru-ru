---
title: Поведение публикации метаданных
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 20922636f140e0ac9faff55bf94c0b2633a8070d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309333"
---
# <a name="metadata-publishing-behavior"></a>Поведение публикации метаданных
Образец поведения публикации метаданных демонстрирует, как управлять возможностями публикации метаданных службы. Чтобы предотвратить непреднамеренное разглашение потенциально важных метаданных службы, конфигурация по умолчанию для служб Windows Communication Foundation (WCF) отключает публикацию метаданных. Такое расширение функциональности по умолчанию защищено, но это также означает, что при этом невозможно использовать средство импорта метаданных (например, Svcutil.exe) для создания клиентского кода, необходимого для вызова службы, если поведение публикации не включено явно в конфигурации.  
  
> [!IMPORTANT]
>  Для ясности этот образец демонстрирует создание незащищенной конечной точки публикации метаданных. Такие конечные точки являются потенциально доступными для анонимных не прошедших проверку подлинности потребителей, поэтому перед развертыванием таких конечных точек следует соблюдать осторожность и убедиться, что публичное раскрытие метаданных службы уместно. См. в разделе [конечной точки метаданных Secure Custom](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) образец для примера, который защищает конечную точку метаданных.  
  
 Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md), который реализует `ICalculator` контракт службы. В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Чтобы отобразить метаданные для службы, параметр <xref:System.ServiceModel.Description.ServiceMetadataBehavior> должен быть сконфигурирован в службе. При наличии такого поведения можно публиковать метаданные, конфигурируя конечную точку для предоставления контракта <xref:System.ServiceModel.Description.IMetadataExchange> как реализации протокола WS-MetadataExchange (MEX). Для удобства этому контракту присвоено сокращенное имя конфигурации "IMetadataExchange". В этом образце используется привязка `mexHttpBinding`, являющаяся удобной стандартной привязкой, эквивалентной `wsHttpBinding` с режимом безопасности, которому присвоено значение `None`. Относительный адрес «MEX» используется в конечной точке, которая при разрешении относительно служб базового адреса приводит к созданию адреса конечной точки `http://localhost/servicemodelsamples/service.svc/mex`. Ниже приводится конфигурация поведения:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Ниже приводится описание конечной точки MEX.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Этот образец присваивает свойству <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> логическое значение `true`, а также предоставляет метаданные службы, используя HTTP GET. Чтобы включить конечную точку метаданных HTTP GET, службе должен быть присвоен базовый HTTP-адрес. Для доступа к метаданным используется строка запроса `?wsdl` для базового адреса службы. К примеру, чтобы увидеть WSDL для службы в веб-браузере используется адрес `http://localhost/servicemodelsamples/service.svc?wsdl`. Кроме того, можно использовать это поведение, чтобы предоставить метаданные по протоколу HTTPS, присваивая свойству <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> логическое значение `true`. Это потребует наличия базового HTTPS-адреса.  
  
 Для доступа к использования конечной точки MEX службы [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Это позволит создать клиент, основанный на метаданных службы.  
  
 Для доступа к метаданных службы, с помощью HTTP GET, введите в браузере `http://localhost/servicemodelsamples/service.svc?wsdl`.  
  
 При удалении этого поведения и попытке открыть службу будет получено исключение. Происходит ошибка, поскольку конечная точка, настроенная с контрактом `IMetadataExchange`, не имеет реализации при отсутствии поведения.  
  
 Если свойству `HttpGetEnabled` присваивается логическое значение `false`, будет отображена справочная страница CalculatorService вместо метаданных службы.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
