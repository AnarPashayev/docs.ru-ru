---
title: Надежный сеанс WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: c682db98ac72019d434e06ae79d87b69c85c275e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006319"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="c7a48-102">Надежный сеанс WS</span><span class="sxs-lookup"><span data-stu-id="c7a48-102">WS Reliable Session</span></span>
<span data-ttu-id="c7a48-103">Данный образец демонстрирует использование надежных сеансов.</span><span class="sxs-lookup"><span data-stu-id="c7a48-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="c7a48-104">Надежные сеансы предоставляют поддержку для надежных сеансов и обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="c7a48-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="c7a48-105">При надежном обмене сообщениями в случае сбоя предпринимается повторная попытка передачи и задаются такие гарантии доставки, как соблюдение порядка получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="c7a48-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="c7a48-106">Сеансы поддерживают состояние для клиентов между вызовами.</span><span class="sxs-lookup"><span data-stu-id="c7a48-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="c7a48-107">Пример реализует сеансы для поддержки состояния клиента и задает гарантии соблюдения очередности доставки сообщений.</span><span class="sxs-lookup"><span data-stu-id="c7a48-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7a48-108">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c7a48-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7a48-109">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="c7a48-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7a48-110">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="c7a48-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7a48-111">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="c7a48-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="c7a48-112">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) , реализующем службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="c7a48-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c7a48-113">Возможности надежного сеанса включаются и настраиваются в файлах конфигурации приложения для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="c7a48-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="c7a48-114">В этом образце служба размещается в службах IIS, а клиентом является консольное приложение (EXE).</span><span class="sxs-lookup"><span data-stu-id="c7a48-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7a48-115">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c7a48-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c7a48-116">В этом образце используется привязка `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="c7a48-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="c7a48-117">Привязка задается в файлах конфигурации клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="c7a48-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="c7a48-118">Тип привязки задается в атрибуте `binding` элемента конечной точки, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c7a48-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c7a48-119">Конечная точка содержит атрибут `bindingConfiguration`, ссылающийся на конфигурацию привязки с именем "Binding1".</span><span class="sxs-lookup"><span data-stu-id="c7a48-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="c7a48-120">Конфигурация привязки разрешает безопасные сеансы, задав `enabled` атрибут [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) для `true`.</span><span class="sxs-lookup"><span data-stu-id="c7a48-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="c7a48-121">Гарантии доставки для упорядоченных сеансов контролируются путем присвоения атрибуту упорядочивания значений `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="c7a48-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="c7a48-122">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="c7a48-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="c7a48-123">Класс реализации службы реализует <xref:System.ServiceModel.InstanceContextMode.PerSession>, создающий экземпляры для поддержания отдельного экземпляра класса для каждого клиента, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="c7a48-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="c7a48-124">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="c7a48-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c7a48-125">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="c7a48-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7a48-126">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="c7a48-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c7a48-127">Установите [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, выполнив следующую команду.</span><span class="sxs-lookup"><span data-stu-id="c7a48-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c7a48-128">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7a48-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="c7a48-129">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7a48-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c7a48-130">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7a48-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
