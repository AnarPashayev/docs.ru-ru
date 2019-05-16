---
title: Практическое руководство. Размещение службы WCF в управляемой службе Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: b21033cff53f0cb59710b70923c14b8a539923a1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636495"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="31054-102">Практическое руководство. Размещение службы WCF в управляемой службе Windows</span><span class="sxs-lookup"><span data-stu-id="31054-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="31054-103">В этом разделе описаны основные шаги, необходимые для создания службы Windows Communication Foundation (WCF), которая размещается службой Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="31054-104">Сценарий реализуется с помощью управляемой службе Windows, варианта, является долго выполняющейся службы WCF, размещенных за пределами Internet Information Services (IIS) в защищенной среде, которая не является сообщением активации размещения.</span><span class="sxs-lookup"><span data-stu-id="31054-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="31054-105">Вместо этого время существования службы контролируется операционной системой.</span><span class="sxs-lookup"><span data-stu-id="31054-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="31054-106">Данный вариант размещения доступен во всех версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="31054-107">Службами Windows можно управлять при помощи Microsoft.ManagementConsole.SnapIn в консоли управления (MMC) и можно настроить их автоматический запуск при загрузке системы.</span><span class="sxs-lookup"><span data-stu-id="31054-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="31054-108">Этот вариант размещения предполагает регистрацию домена приложения (AppDomain), на котором размещена служба WCF в управляемой службе Windows, так что время существования процесса службы контролируется диспетчером управления службами (SCM) для служб Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="31054-109">Код службы включает в себя реализацию службы контракта службы, класс службы Windows и класс установщика.</span><span class="sxs-lookup"><span data-stu-id="31054-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="31054-110">Класс реализации службы, `CalculatorService`, — это служба WCF.</span><span class="sxs-lookup"><span data-stu-id="31054-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="31054-111">Класс `CalculatorWindowsService` является службой Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="31054-112">Чтобы считаться службой Windows, этот класс наследует от класса `ServiceBase` и реализует методы `OnStart` и `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="31054-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="31054-113">В методе `OnStart` создается объект <xref:System.ServiceModel.ServiceHost> для типа `CalculatorService` и открывается.</span><span class="sxs-lookup"><span data-stu-id="31054-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="31054-114">В методе `OnStop` служба останавливается и освобождается.</span><span class="sxs-lookup"><span data-stu-id="31054-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="31054-115">Ведущее приложение также отвечает за предоставление базового адреса для узла службы, настроенного в параметрах приложения.</span><span class="sxs-lookup"><span data-stu-id="31054-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="31054-116">Класс установщика, унаследованный от класса <xref:System.Configuration.Install.Installer>, позволяет выполнить установку программы как службы Windows с помощью Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="31054-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="31054-117">Создание службы и предоставление кода размещения</span><span class="sxs-lookup"><span data-stu-id="31054-117">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="31054-118">Создание новой Visual Studio **консольное приложение** проект с именем **службы**.</span><span class="sxs-lookup"><span data-stu-id="31054-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="31054-119">Измените имя файла Program.cs на Service.cs.</span><span class="sxs-lookup"><span data-stu-id="31054-119">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="31054-120">Изменить пространство имен для `Microsoft.ServiceModel.Samples`.</span><span class="sxs-lookup"><span data-stu-id="31054-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="31054-121">Добавьте ссылки на следующие сборки:</span><span class="sxs-lookup"><span data-stu-id="31054-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="31054-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="31054-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="31054-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="31054-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="31054-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="31054-124">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="31054-125">Добавьте следующие операторы using в файл Service.cs.</span><span class="sxs-lookup"><span data-stu-id="31054-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="31054-126">Определите контракт службы `ICalculator`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="31054-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="31054-127">Реализуйте контракт службы в классе с именем `CalculatorService`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="31054-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="31054-128">Создайте новый класс с именем `CalculatorWindowsService`, производный от класса <xref:System.ServiceProcess.ServiceBase>.</span><span class="sxs-lookup"><span data-stu-id="31054-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="31054-129">Добавьте локальную переменную с именем `serviceHost`, чтобы создать ссылку на экземпляр <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="31054-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="31054-130">Определите метод `Main`, который вызывает `ServiceBase.Run(new CalculatorWindowsService)`.</span><span class="sxs-lookup"><span data-stu-id="31054-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="31054-131">Переопределите метод <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, создав и открыв новый экземпляр <xref:System.ServiceModel.ServiceHost>, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="31054-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="31054-132">Переопределите метод <xref:System.ServiceProcess.ServiceBase.OnStop%2A>, закрывающий <xref:System.ServiceModel.ServiceHost>, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="31054-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="31054-133">Создайте новый класс с именем `ProjectInstaller`, производный от <xref:System.Configuration.Install.Installer> и помеченный атрибутом <xref:System.ComponentModel.RunInstallerAttribute>, установленным в значение `true`.</span><span class="sxs-lookup"><span data-stu-id="31054-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="31054-134">Это позволяет устанавливать службу Windows программой Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="31054-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="31054-135">Удалите класс `Service`, созданный при создании проекта.</span><span class="sxs-lookup"><span data-stu-id="31054-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="31054-136">Добавьте в проект файл конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="31054-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="31054-137">Замените содержимое этого файла следующим XML-кодом конфигурации.</span><span class="sxs-lookup"><span data-stu-id="31054-137">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="31054-138">Щелкните правой кнопкой мыши файл App.config в **обозревателе решений** и выберите **свойства**.</span><span class="sxs-lookup"><span data-stu-id="31054-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="31054-139">В разделе **Копировать в выходной каталог** выберите **копировать, если новее**.</span><span class="sxs-lookup"><span data-stu-id="31054-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="31054-140">В этом примере конечные точки явно задаются в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="31054-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="31054-141">Если в службу не добавлена ни одна конечная точка, то среда выполнения добавляет конечные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="31054-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="31054-142">В этом примере, поскольку для службы параметр <xref:System.ServiceModel.Description.ServiceMetadataBehavior> установлен в значение `true`, в ней также будет включена публикация метаданных.</span><span class="sxs-lookup"><span data-stu-id="31054-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="31054-143">Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](../../../../docs/framework/wcf/simplified-configuration.md) и [Упрощенная конфигурация служб WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="31054-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="31054-144">Установка и запуск службы</span><span class="sxs-lookup"><span data-stu-id="31054-144">Install and run the service</span></span>

1. <span data-ttu-id="31054-145">Постройте решение, чтобы создать исполняемый файл `Service.exe`.</span><span class="sxs-lookup"><span data-stu-id="31054-145">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="31054-146">Откройте командную строку разработчика для Visual Studio и перейдите в каталог проекта.</span><span class="sxs-lookup"><span data-stu-id="31054-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="31054-147">В командной строке введите `installutil bin\service.exe`, чтобы установить службу Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="31054-148">В командной строке введите `services.msc`, чтобы получить доступ к диспетчеру служб.</span><span class="sxs-lookup"><span data-stu-id="31054-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="31054-149">Служба Windows должна появиться в списке служб с именем WCFWindowsServiceSample.</span><span class="sxs-lookup"><span data-stu-id="31054-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="31054-150">Службы WCF только может отвечать клиентам, если запущена служба Windows.</span><span class="sxs-lookup"><span data-stu-id="31054-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="31054-151">Чтобы запустить службу, щелкните правой кнопкой мыши его в диспетчер управления Службами и выберите «Start» или тип **net start WCFWindowsServiceSample** в командной строке.</span><span class="sxs-lookup"><span data-stu-id="31054-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="31054-152">Чтобы внести изменения в службу, необходимо предварительно остановить ее и удалить.</span><span class="sxs-lookup"><span data-stu-id="31054-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="31054-153">Чтобы остановить службу, щелкните правой кнопкой мыши в Диспетчере служб и выберите «Остановить», или **тип net stop WCFWindowsServiceSample** в командной строке.</span><span class="sxs-lookup"><span data-stu-id="31054-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="31054-154">Учтите, что если остановить службу Windows, а затем запустить клиент, то когда клиент попытается обратиться к службе, будет вызвано исключение <xref:System.ServiceModel.EndpointNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="31054-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="31054-155">Чтобы удалить тип службы Windows **installutil /u bin\service.exe** в командной строке.</span><span class="sxs-lookup"><span data-stu-id="31054-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="31054-156">Пример</span><span class="sxs-lookup"><span data-stu-id="31054-156">Example</span></span>

<span data-ttu-id="31054-157">Ниже приведен полный листинг кода, используемый в этом разделе:</span><span class="sxs-lookup"><span data-stu-id="31054-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="31054-158">Как и в случае резидентного размещения, среда размещения службы Windows требует, чтобы код размещения являлся частью приложения.</span><span class="sxs-lookup"><span data-stu-id="31054-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="31054-159">Служба реализуется как консольное приложение и содержит собственный код размещения.</span><span class="sxs-lookup"><span data-stu-id="31054-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="31054-160">В других средах размещения, таких как служба активации Windows (WAS), размещающих в IIS, писать код размещения необязательно.</span><span class="sxs-lookup"><span data-stu-id="31054-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="31054-161">См. также</span><span class="sxs-lookup"><span data-stu-id="31054-161">See also</span></span>

- [<span data-ttu-id="31054-162">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="31054-162">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="31054-163">Размещение в управляемом приложении</span><span class="sxs-lookup"><span data-stu-id="31054-163">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [<span data-ttu-id="31054-164">Размещение служб</span><span class="sxs-lookup"><span data-stu-id="31054-164">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="31054-165">Функции размещения Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="31054-165">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
