---
title: Упрощенная конфигурация служб WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 47af8dcba35ba31f25597c946596b0cbcac93b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304263"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="8b15d-102">Упрощенная конфигурация служб WCF</span><span class="sxs-lookup"><span data-stu-id="8b15d-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="8b15d-103">В этом примере показано, как реализовать и настроить типизированные службы и клиента с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8b15d-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="8b15d-104">Этот образец является основой для всех остальных базовых образцов технологий.</span><span class="sxs-lookup"><span data-stu-id="8b15d-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="8b15d-105">Эта служба, которая предоставляет конечную точку для взаимодействия со службой, использует упрощенную конфигурацию в [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b15d-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="8b15d-106">До [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] конечная точка определяется в файле конфигурации (Web.config). См. следующий пример кода конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8b15d-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="8b15d-107">В [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] элемент `<service>` является необязательным.</span><span class="sxs-lookup"><span data-stu-id="8b15d-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="8b15d-108">Если конечные точки не заданы в службе, то к службе добавляется конечная точка для каждого базового адреса и реализованного контракта.</span><span class="sxs-lookup"><span data-stu-id="8b15d-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="8b15d-109">Базовый адрес добавляется к имени контракта для определения конечной точки, и привязка определяется с помощью схемы адреса.</span><span class="sxs-lookup"><span data-stu-id="8b15d-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="8b15d-110">В следующем примере кода показан файл упрощенной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8b15d-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="8b15d-111">Настроенный таким образом, служба может осуществляться с `http://localhost/servicemodelsamples/service.svc` клиентом на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="8b15d-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="8b15d-112">Чтобы к службе могли получить доступ клиенты на удаленных компьютерах, вместо имени localhost необходимо указать полное имя домена.</span><span class="sxs-lookup"><span data-stu-id="8b15d-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="8b15d-113">По умолчанию служба не предоставляет метаданных.</span><span class="sxs-lookup"><span data-stu-id="8b15d-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="8b15d-114">При этом служба включает поведение <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="8b15d-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="8b15d-115">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="8b15d-115">To use this sample</span></span>  
  
1. <span data-ttu-id="8b15d-116">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b15d-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8b15d-117">Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b15d-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8b15d-118">Запустите образец, выполнив следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="8b15d-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="8b15d-119">Щелкните правой кнопкой мыши **службы** проекта и выберите **Назначить запускаемым проектом**, затем нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8b15d-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="8b15d-120">Дождитесь вывода данных на консоли, подтверждающих запуск и выполнение службы.</span><span class="sxs-lookup"><span data-stu-id="8b15d-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="8b15d-121">Щелкните правой кнопкой мыши **клиента** проекта и выберите **Назначить запускаемым проектом**, затем нажмите клавишу **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8b15d-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8b15d-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8b15d-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8b15d-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8b15d-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8b15d-124">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8b15d-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b15d-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8b15d-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="8b15d-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8b15d-126">See also</span></span>

- [<span data-ttu-id="8b15d-127">Образцы управления AppFabric</span><span class="sxs-lookup"><span data-stu-id="8b15d-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="8b15d-128">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="8b15d-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
