---
title: Активация TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 065c4706d0a52414c4abed85044ce06ad3efe35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007751"
---
# <a name="tcp-activation"></a><span data-ttu-id="541cc-102">Активация TCP</span><span class="sxs-lookup"><span data-stu-id="541cc-102">TCP Activation</span></span>

<span data-ttu-id="541cc-103">Этот образец демонстрирует размещение службы, использующей службу активации Windows (WAS) для активации службы, которая осуществляет взаимодействие по протоколу net.tcp.</span><span class="sxs-lookup"><span data-stu-id="541cc-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="541cc-104">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="541cc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="541cc-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="541cc-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="541cc-106">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="541cc-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="541cc-107">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="541cc-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="541cc-108">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="541cc-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="541cc-109">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="541cc-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="541cc-110">Пример содержит консольную программу клиента (EXE) и библиотеку службы (DLL), размещаемую в рабочем процессе, активируемом службой WAS.</span><span class="sxs-lookup"><span data-stu-id="541cc-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="541cc-111">Действия клиента отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="541cc-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="541cc-112">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="541cc-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="541cc-113">Контракт определяется интерфейсом `ICalculator`, который предоставляет математические операции (сложение, вычитание, умножение и деление), как показано ниже в образце кода:</span><span class="sxs-lookup"><span data-stu-id="541cc-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="541cc-114">Реализация службы выполняет вычисления и возвращает соответствующий результат:</span><span class="sxs-lookup"><span data-stu-id="541cc-114">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="541cc-115">В этом образце используется вариант привязки net.tcp с включенным совместным использованием порта TCP и отключенным механизмом безопасности.</span><span class="sxs-lookup"><span data-stu-id="541cc-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="541cc-116">Если требуется использовать безопасную привязку TCP, измените режим безопасности сервера на требуемое значение и снова запустите svcutil.exe на клиенте, чтобы получить обновленный файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="541cc-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="541cc-117">В следующем образце показана конфигурация для службы:</span><span class="sxs-lookup"><span data-stu-id="541cc-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="541cc-118">Конечная точка клиента настраивается так, как показано в следующем образце кода:</span><span class="sxs-lookup"><span data-stu-id="541cc-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="541cc-119">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="541cc-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="541cc-120">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="541cc-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="541cc-121">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="541cc-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="541cc-122">Убедитесь, что установлена платформа [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541cc-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> <span data-ttu-id="541cc-123">Для активации WAS требуются службы [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541cc-123">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] is required for WAS activation.</span></span>

2. <span data-ttu-id="541cc-124">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="541cc-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="541cc-125">Кроме того необходимо установить компоненты не HTTP Активация WCF:</span><span class="sxs-lookup"><span data-stu-id="541cc-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="541cc-126">В меню **Пуск** выберите **Панель управления**.</span><span class="sxs-lookup"><span data-stu-id="541cc-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="541cc-127">Выберите **программы и компоненты**.</span><span class="sxs-lookup"><span data-stu-id="541cc-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="541cc-128">Нажмите кнопку **отключение компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="541cc-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="541cc-129">Разверните **Microsoft .NET Framework 3.0** узел и проверьте **не-HTTP активация Windows Communication Foundation** функции.</span><span class="sxs-lookup"><span data-stu-id="541cc-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="541cc-130">Настройте службу WAS на поддержку активации по протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="541cc-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="541cc-131">Для удобства два нижеописанных действия выполняются в пакетом файле AddNetTcpSiteBinding.cmd, расположенном в каталоге с образцами.</span><span class="sxs-lookup"><span data-stu-id="541cc-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="541cc-132">Для поддержки активации по net.tcp веб-узел по умолчанию необходимо сначала привязать к порту net.tcp.</span><span class="sxs-lookup"><span data-stu-id="541cc-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="541cc-133">Сделать это позволяет программа Appcmd.exe, которая устанавливается с набором инструментов управления IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="541cc-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="541cc-134">В командной строке с правами администратора выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="541cc-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="541cc-135">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="541cc-135">This command is a single line of text.</span></span> <span data-ttu-id="541cc-136">Она добавляет привязку сайта к протоколу net.tcp в веб-сайт по умолчанию, ожидающий передачи данных по протоколу TCP на порту 808 с любым именем узла.</span><span class="sxs-lookup"><span data-stu-id="541cc-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="541cc-137">Несмотря на то что все приложения в узле имеют общую привязку к протоколу net.tcp, включать поддержку net.tcp можно для каждого приложения отдельно.</span><span class="sxs-lookup"><span data-stu-id="541cc-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="541cc-138">Для включения протокола net.tcp для приложения /servicemodelsample необходимо выполнить следующую команду из командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="541cc-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="541cc-139">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="541cc-139">This command is a single line of text.</span></span> <span data-ttu-id="541cc-140">Эта команда позволяет приложению/servicemodelsamples, осуществлять доступ к оба `http://localhost/servicemodelsamples` и `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="541cc-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="541cc-141">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="541cc-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="541cc-142">Чтобы запустить образец в конфигурации с одной или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="541cc-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="541cc-143">Удалите привязку сайта к протоколу net.tcp, добавленную ранее для данного образца.</span><span class="sxs-lookup"><span data-stu-id="541cc-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="541cc-144">Для удобства два нижеописанных действия выполняются в пакетом файле RemoveNetTcpSiteBinding.cmd, расположенном в каталоге с образцами.</span><span class="sxs-lookup"><span data-stu-id="541cc-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="541cc-145">Удалите протокол net.tcp из списка разрешенных протоколов, выполнив следующую команду в окне командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="541cc-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="541cc-146">Эта команда вводится как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="541cc-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="541cc-147">Удалите привязку узла к протоколу net.tcp, выполнив следующую команду в окне командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="541cc-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="541cc-148">Эта команда должна вводиться как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="541cc-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="541cc-149">См. также</span><span class="sxs-lookup"><span data-stu-id="541cc-149">See also</span></span>

- [<span data-ttu-id="541cc-150">Образцы размещения AppFabric и сохраняемости</span><span class="sxs-lookup"><span data-stu-id="541cc-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
