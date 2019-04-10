---
title: Пользовательский перехватчик сообщений
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344277"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="59334-102">Пользовательский перехватчик сообщений</span><span class="sxs-lookup"><span data-stu-id="59334-102">Custom Message Interceptor</span></span>
<span data-ttu-id="59334-103">Данный образец демонстрирует использование модели расширяемости канала.</span><span class="sxs-lookup"><span data-stu-id="59334-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="59334-104">В частности, показано, как реализовать пользовательский элемент привязки, который создает фабрики и прослушиватели каналов для перехвата всех входящих и исходящих сообщений в определенной точке стека времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="59334-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="59334-105">В состав образца входят клиент и сервер, которые демонстрируют использование этих пользовательских фабрик.</span><span class="sxs-lookup"><span data-stu-id="59334-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="59334-106">В этом образце служба и клиент являются консольными программами (EXE).</span><span class="sxs-lookup"><span data-stu-id="59334-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="59334-107">Как клиент, так и служба используют общую библиотеку (DLL), которая содержит пользовательский элемент привязки и ассоциированные с ним объекты времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="59334-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59334-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="59334-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59334-109">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="59334-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59334-110">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="59334-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="59334-111">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="59334-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59334-112">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="59334-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="59334-113">Образец описана процедура, предлагаемая для создания пользовательского многоуровневого канала в Windows Communication Foundation (WCF), с помощью инфраструктуры канала и согласно рекомендации по WCF.</span><span class="sxs-lookup"><span data-stu-id="59334-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="59334-114">Чтобы создать пользовательский многоуровневый канал, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="59334-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="59334-115">Выберите формы канала, которые будут поддерживать фабрика и прослушиватель каналов.</span><span class="sxs-lookup"><span data-stu-id="59334-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="59334-116">Создайте фабрику и прослушиватель каналов, которые поддерживают выбранную форму канала.</span><span class="sxs-lookup"><span data-stu-id="59334-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="59334-117">Присоедините элемент привязки, добавляющий пользовательский многоуровневый канал в стек каналов.</span><span class="sxs-lookup"><span data-stu-id="59334-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="59334-118">Добавьте раздел расширения элементов привязки, чтобы представить новый элемент привязки системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="59334-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="59334-119">Формы каналов</span><span class="sxs-lookup"><span data-stu-id="59334-119">Channel Shapes</span></span>  
 <span data-ttu-id="59334-120">При создании пользовательского многоуровневого канала в первую очередь необходимо решить, какие формы требуются для канала.</span><span class="sxs-lookup"><span data-stu-id="59334-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="59334-121">Данным инспектором сообщений поддерживается любая форма, поддерживаемая уровнем ниже (например, если уровень ниже может выполнить построение метода <xref:System.ServiceModel.Channels.IOutputChannel> и интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, то также предоставляется метод <xref:System.ServiceModel.Channels.IOutputChannel> и интерфейс <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="59334-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="59334-122">Фабрика и прослушиватель каналов</span><span class="sxs-lookup"><span data-stu-id="59334-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="59334-123">Следующий шаг создания пользовательского многоуровневого канала - реализация интерфейса <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов и интерфейса <xref:System.ServiceModel.Channels.IChannelListener> для каналов служб.</span><span class="sxs-lookup"><span data-stu-id="59334-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="59334-124">Эти классы получают внутреннюю фабрику и прослушиватель и делегируют все вызовы внутренней фабрике и прослушивателю, кроме `OnCreateChannel` и `OnAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="59334-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="59334-125">Добавление элемента привязки</span><span class="sxs-lookup"><span data-stu-id="59334-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="59334-126">В образце определен пользовательский элемент привязки: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="59334-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> `InterceptingBindingElement` <span data-ttu-id="59334-127">принимает `ChannelMessageInterceptor` качестве входных данных и использует этот `ChannelMessageInterceptor` для обработки сообщений, проходящих через него.</span><span class="sxs-lookup"><span data-stu-id="59334-127">takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="59334-128">Только этот класс должен быть открытым.</span><span class="sxs-lookup"><span data-stu-id="59334-128">This is the only class that must be public.</span></span> <span data-ttu-id="59334-129">Фабрика, прослушиватель и каналы - все они могут являться внутренними реализациями открытых интерфейсов времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="59334-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="59334-130">Добавление поддержки конфигурации</span><span class="sxs-lookup"><span data-stu-id="59334-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="59334-131">Для интеграции с конфигурацией привязки библиотека определяет обработчик раздела конфигурации в качестве раздела расширения элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="59334-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="59334-132">Файлы конфигурации клиента и сервера должны зарегистрировать расширение элемента привязки в системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="59334-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="59334-133">Реализации, требующие предоставить их элементы привязки в системе конфигурации, могут наследовать от этого класса.</span><span class="sxs-lookup"><span data-stu-id="59334-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="59334-134">Добавление политики</span><span class="sxs-lookup"><span data-stu-id="59334-134">Adding Policy</span></span>  
 <span data-ttu-id="59334-135">Для интеграции с системой политики `InterceptingBindingElement` реализует расширение IPolicyExportExtension, чтобы сообщить об участии в создании политики.</span><span class="sxs-lookup"><span data-stu-id="59334-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="59334-136">Чтобы поддержать импорт политики на созданном клиенте, пользователь может зарегистрировать производный класс `InterceptingBindingElementImporter` и переопределить `CreateMessageInterceptor`(), чтобы создать принадлежащий им класс `ChannelMessageInterceptor` с разрешенной политикой.</span><span class="sxs-lookup"><span data-stu-id="59334-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="59334-137">Пример Инспектор сообщений</span><span class="sxs-lookup"><span data-stu-id="59334-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="59334-138">Включенный в пример образец реализации `ChannelMessageInspector` удаляет сообщения.</span><span class="sxs-lookup"><span data-stu-id="59334-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="59334-139">Его можно открыть из конфигурации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="59334-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="59334-140">Клиент и сервер используют заново созданный раздел конфигурации, чтобы добавить пользовательские фабрики в самый нижний уровень принадлежащих им стеков канала времени выполнения (расположенные над транспортным уровнем).</span><span class="sxs-lookup"><span data-stu-id="59334-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="59334-141">Клиент использует библиотеку `MessageInterceptor`, чтобы добавить пользовательский заголовок даже в нумерованные сообщения.</span><span class="sxs-lookup"><span data-stu-id="59334-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="59334-142">С другой стороны, служба использует библиотеку `MessageInterceptor`, чтобы удалять любые сообщения, которые не содержат этот специальный заголовок.</span><span class="sxs-lookup"><span data-stu-id="59334-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="59334-143">Клиент должен предоставить результат своей работы после запуска службы и последующего запуска клиента.</span><span class="sxs-lookup"><span data-stu-id="59334-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="59334-144">Клиент отправляет отчет службе о 10 различных значениях скорости ветра, но только половина этих значений помечена специальным заголовком.</span><span class="sxs-lookup"><span data-stu-id="59334-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="59334-145">Служба должна предоставить следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="59334-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59334-146">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="59334-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="59334-147">Установите [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, выполнив следующую команду.</span><span class="sxs-lookup"><span data-stu-id="59334-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="59334-148">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59334-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="59334-149">Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59334-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="59334-150">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59334-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="59334-151">Первым запустите файл Service.exe, затем Client.exe и наблюдайте результат в обоих окнах консоли.</span><span class="sxs-lookup"><span data-stu-id="59334-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
