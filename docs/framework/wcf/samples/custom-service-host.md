---
title: Пользовательский узел службы
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 8302c3c829883da954d200526ca641eb4c169f98
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052030"
---
# <a name="custom-service-host"></a><span data-ttu-id="5b6a5-102">Пользовательский узел службы</span><span class="sxs-lookup"><span data-stu-id="5b6a5-102">Custom Service Host</span></span>
<span data-ttu-id="5b6a5-103">Этот образец показывает, как применять пользовательский производный класс для класса <xref:System.ServiceModel.ServiceHost>, чтобы изменять поведение службы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="5b6a5-104">Такой подход обеспечивает поддерживающую повторное использование альтернативу настройке большого числа служб одинаковым образом.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="5b6a5-105">Кроме того, в этом примере демонстрируется, как с помощью класса <xref:System.ServiceModel.Activation.ServiceHostFactory> применять пользовательский объект ServiceHost в среде размещения IIS или службы активации Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="5b6a5-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b6a5-106">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b6a5-107">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5b6a5-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b6a5-108">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b6a5-109">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="5b6a5-110">Сценарий</span><span class="sxs-lookup"><span data-stu-id="5b6a5-110">About the scenario</span></span>
 <span data-ttu-id="5b6a5-111">Чтобы предотвратить непреднамеренное раскрытие потенциально конфиденциальных метаданных службы, конфигурация по умолчанию для служб Windows Communication Foundation (WCF) отключает публикацию метаданных.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="5b6a5-112">Такое поведение является безопасным по умолчанию, но также означает, что нельзя использовать средство импорта метаданных (например, Svcutil.exe) для создания клиентского кода, необходимого для вызова службы, если в конфигурации не включено явное поведение публикации метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service's metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="5b6a5-113">Включение публикации метаданных для большого числа служб связано с добавлением одинаковых элементов конфигурации для всех служб по отдельности, что приводит к появлению значительного объема повторяющейся информации конфигураций.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="5b6a5-114">Вместо конфигурации всех служб по отдельности можно написать принудительный код, один раз включающий публикацию метаданных, а затем использовать его повторно для нескольких других служб.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="5b6a5-115">Для этого создается новый класс, наследуемый от класса <xref:System.ServiceModel.ServiceHost>, переопределяющий метод `ApplyConfiguration`() так, чтобы принудительно добавить поведение публикации метаданных.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b6a5-116">Для ясности этот образец демонстрирует создание незащищенной конечной точки публикации метаданных.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="5b6a5-117">Такие конечные точки потенциально доступны для анонимных пользователей, не прошедших проверку подлинности, и необходимо соблюдать осторожность перед развертыванием таких конечных точек, чтобы обеспечить оптимальное раскрытие метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service's metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="5b6a5-118">Реализация пользовательского ServiceHost</span><span class="sxs-lookup"><span data-stu-id="5b6a5-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="5b6a5-119">Класс <xref:System.ServiceModel.ServiceHost> предоставляет несколько полезных виртуальных методов, которые наследующие классы могут переопределять, чтобы изменять поведение службы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="5b6a5-120">Например, метод `ApplyConfiguration`() выполняет чтение сведений конфигурации службы из хранилища конфигураций и соответствующим образом изменяет объект <xref:System.ServiceModel.Description.ServiceDescription> ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="5b6a5-121">Реализация по умолчанию считывает конфигурацию из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-121">The default implementation reads configuration from the application's configuration file.</span></span> <span data-ttu-id="5b6a5-122">Пользовательские реализации могут переопределять метод `ApplyConfiguration`() для дополнительного изменения<xref:System.ServiceModel.Description.ServiceDescription> с помощью императивного кода или даже полностью заменять хранилище конфигураций по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="5b6a5-123">Например, чтобы считать конфигурацию конечной точки службы из базы данных, а не файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-123">For example, to read a service's endpoint configuration from a database instead of the application's configuration file.</span></span>  
  
 <span data-ttu-id="5b6a5-124">В этом примере мы хотим создать пользовательский ServiceHost, добавляющий ServiceMetadataBehavior (который включает публикацию метаданных), даже если это поведение явно не Добавлено в файл конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior (which enables metadata publishing) even if this behavior is not explicitly added in the service's configuration file.</span></span> <span data-ttu-id="5b6a5-125">Для этого создайте новый класс, который наследует от <xref:System.ServiceModel.ServiceHost> и переопределяет `ApplyConfiguration` ().</span><span class="sxs-lookup"><span data-stu-id="5b6a5-125">To accomplish this, create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="5b6a5-126">Так как мы не будем пропускать все настройки, предоставленные в файле конфигурации приложения, первое, что делает переопределение `ApplyConfiguration` (), вызывает базовую реализацию.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-126">Because we do not want to ignore any configuration that has been provided in the application's configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="5b6a5-127">После выполнения этого метода можно принудительно добавить в описание поведение <xref:System.ServiceModel.Description.ServiceMetadataBehavior> с помощью следующего принудительного кода.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="5b6a5-128">Наконец, переопределение `ApplyConfiguration`() должно добавить конечную точку метаданных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="5b6a5-129">По соглашению для каждого URI в коллекции BaseAddresses узла службы создается одна конечная точка метаданных.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-129">By convention, one metadata endpoint is created for each URI in the service host's BaseAddresses collection.</span></span>  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="5b6a5-130">Использование пользовательского ServiceHost в резидентной службе</span><span class="sxs-lookup"><span data-stu-id="5b6a5-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="5b6a5-131">Выполненную реализацию пользовательского ServiceHost можно использовать для добавления поведения публикации метаданных к любой службе, разместив эту службу внутри экземпляра `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="5b6a5-132">В следующем примере кода демонстрируется его использование с резидентной службой.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="5b6a5-133">Наш пользовательский узел по-прежнему считывает конфигурацию конечной точки службы из файла конфигурации приложения, как если бы мы использовали класс по умолчанию <xref:System.ServiceModel.ServiceHost> для размещения службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-133">Our custom host still reads the service's endpoint configuration from the application's configuration file, as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="5b6a5-134">Но так как в пользовательское основное приложение добавлена логика, включающая публикацию метаданных, нет необходимости явно включать поведение публикации метаданных в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="5b6a5-135">Этот подход удобен при создании приложения, содержащего несколько служб, для которых нужно включить публикацию метаданных. Он позволяет не повторять несколько раз запись одинаковых элементов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="5b6a5-136">Использование пользовательского ServiceHost в службах IIS или WAS</span><span class="sxs-lookup"><span data-stu-id="5b6a5-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="5b6a5-137">Использовать пользовательский узел службы в резидентных сценариях нетрудно, потому что за создание и открытие экземпляра основного приложения службы отвечает в итоге код вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="5b6a5-138">Однако в среде IIS или WAS инфраструктура WCF динамически создает экземпляр узла службы в ответ на входящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service's host in response to incoming messages.</span></span> <span data-ttu-id="5b6a5-139">В этой среде размещения также можно использовать пользовательские узлы служб, но для этого требуется дополнительный код в виде ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="5b6a5-140">В следующем коде приведен класс, наследуемый от <xref:System.ServiceModel.Activation.ServiceHostFactory>, возвращающий экземпляры пользовательского `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="5b6a5-141">Как видите, реализация пользовательского ServiceHostFactory проста.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-141">As you can see, implementing a custom ServiceHostFactory is straightforward.</span></span> <span data-ttu-id="5b6a5-142">Вся пользовательская логика находится внутри реализации ServiceHost; фабрика возвращает экземпляр производного класса.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="5b6a5-143">Чтобы использовать настраиваемую фабрику с реализацией службы, необходимо добавить некоторые дополнительные метаданные в SVC-файл службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-143">To use a custom factory with a service implementation, we must add some additional metadata to the service's .svc file.</span></span>  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="5b6a5-144">Здесь мы добавили `Factory` к `@ServiceHost` директиве дополнительный атрибут и передали имя типа CLR нашей пользовательской фабрике в качестве значения атрибута.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute's value.</span></span> <span data-ttu-id="5b6a5-145">Когда IIS или WAS получает сообщение для этой службы, инфраструктура хостинга WCF сначала создает экземпляр ServiceHostFactory, а затем создает объект узла службы, вызывая `ServiceHostFactory.CreateServiceHost()` .</span><span class="sxs-lookup"><span data-stu-id="5b6a5-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiates the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="5b6a5-146">Выполнение примера</span><span class="sxs-lookup"><span data-stu-id="5b6a5-146">Running the sample</span></span>  
 <span data-ttu-id="5b6a5-147">Несмотря на то, что этот пример обеспечивает полностью функциональную реализацию клиента и службы, точка примера заключается в том, чтобы продемонстрировать, как изменить поведение службы во время выполнения с помощью пользовательского узла. выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-147">Although this sample does provide a fully functional client and service implementation, the point of the sample is to illustrate how to alter a service's run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="5b6a5-148">Наблюдение за результатом пользовательского узла</span><span class="sxs-lookup"><span data-stu-id="5b6a5-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="5b6a5-149">Откройте файл Web.config службы и убедитесь, что в конфигурации нет явного включения метаданных для службы.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="5b6a5-150">Откройте SVC-файл службы и убедитесь, что его @ServiceHost директива содержит атрибут Factory, указывающий имя пользовательского ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="5b6a5-151">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="5b6a5-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="5b6a5-152">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6a5-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5b6a5-153">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6a5-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="5b6a5-154">После построения решения запустите Setup.bat, чтобы настроить приложение ServiceModelSamples в IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="5b6a5-155">Теперь каталог ServiceModelSamples должен отображаться как приложение IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="5b6a5-156">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6a5-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="5b6a5-157">Чтобы удалить приложение IIS 7,0, запустите *Cleanup.bat*.</span><span class="sxs-lookup"><span data-stu-id="5b6a5-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b6a5-158">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5b6a5-158">See also</span></span>

- [<span data-ttu-id="5b6a5-159">Практическое руководство. Размещение службы WCF в IIS</span><span class="sxs-lookup"><span data-stu-id="5b6a5-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
