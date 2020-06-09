---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 619c7e793ff94efffcb72774cf3e367df377a3a3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600897"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="40810-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="40810-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="40810-103">В этом образце показано, как создать привязку, предназначенную для поддержки сценариев работы с потоками при использовании транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="40810-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="40810-104">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="40810-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40810-105">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="40810-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40810-106">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="40810-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="40810-107">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="40810-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40810-108">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="40810-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="40810-109">Ниже приводятся действия по созданию и настройке новой стандартной привязки.</span><span class="sxs-lookup"><span data-stu-id="40810-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="40810-110">Создание новой стандартной привязки</span><span class="sxs-lookup"><span data-stu-id="40810-110">Create a new standard binding</span></span>

    <span data-ttu-id="40810-111">Стандартные привязки в Windows Communication Foundation (WCF), такие как basicHttpBinding, и netTcpBinding, настраивают базовые транспорты и стек каналов для конкретных требований.</span><span class="sxs-lookup"><span data-stu-id="40810-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="40810-112">В этом образце привязка `WSStreamedHttpBinding` настраивает стек каналов на поддержку потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="40810-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="40810-113">По умолчанию функции WS-Security и надежного обмена сообщениями не добавляются в стек каналов, поскольку обе эти функции не поддерживаются при потоковой передаче.</span><span class="sxs-lookup"><span data-stu-id="40810-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="40810-114">Новая привязка реализуется в классе `WSStreamedHttpBinding`, наследуемом от <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="40810-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="40810-115">`WSStreamedHttpBinding` содержит следующие элементы привязки: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> и <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="40810-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="40810-116">Класс предоставляет метод `CreateBindingElements()` для настройки результирующего стека привязок, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="40810-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. <span data-ttu-id="40810-117">Добавление поддержки конфигурации</span><span class="sxs-lookup"><span data-stu-id="40810-117">Add configuration support</span></span>

    <span data-ttu-id="40810-118">Для предоставления транспорта через конфигурацию в образце реализуется два дополнительных класса -`WSStreamedHttpBindingConfigurationElement` и `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="40810-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="40810-119">Класс `WSStreamedHttpBindingSection` представляет собой <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , который предоставляет `WSStreamedHttpBinding` системе конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="40810-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="40810-120">Основная часть реализации делегируется классу `WSStreamedHttpBindingConfigurationElement`, наследуемому от класса <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="40810-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="40810-121">Класс `WSStreamedHttpBindingConfigurationElement` имеет свойства, соответствующие свойствам класса `WSStreamedHttpBinding`, и функции для сопоставления каждого элемента конфигурации привязке.</span><span class="sxs-lookup"><span data-stu-id="40810-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="40810-122">Зарегистрируйте обработчик в системе конфигурации, добавив в файл конфигурации службы следующий раздел.</span><span class="sxs-lookup"><span data-stu-id="40810-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="40810-123">После этого на обработчик можно сослаться из раздела конфигурации serviceModel.</span><span class="sxs-lookup"><span data-stu-id="40810-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40810-124">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="40810-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="40810-125">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="40810-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="40810-126">Убедитесь, что выполнены действия, перечисленные в [процедуре однократной настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40810-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="40810-127">Убедитесь, что выполнены инструкции по [установке сертификата сервера службы IIS (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="40810-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="40810-128">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40810-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="40810-129">Чтобы запустить пример в конфигурации с несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40810-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

6. <span data-ttu-id="40810-130">При отображении окна клиента введите "Sample.txt".</span><span class="sxs-lookup"><span data-stu-id="40810-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="40810-131">Копия файла "Sample.txt" должна находиться в каталоге пользователя.</span><span class="sxs-lookup"><span data-stu-id="40810-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="40810-132">Образец службы WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="40810-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="40810-133">Образец службы, использующей привязку `WSStreamedHttpBinding`, расположен в подкаталоге службы.</span><span class="sxs-lookup"><span data-stu-id="40810-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="40810-134">Реализация `OperationContract` использует `MemoryStream` для извлечения всех данных из входящего потока перед возвратом `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="40810-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="40810-135">Служба размещается в IIS.</span><span class="sxs-lookup"><span data-stu-id="40810-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="40810-136">Образец клиента WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="40810-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="40810-137">Клиент, используемый для взаимодействия со службой с помощью привязки `WSStreamedHttpBinding`, расположен в подкаталоге клиента.</span><span class="sxs-lookup"><span data-stu-id="40810-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="40810-138">Поскольку сертификат, используемый в этом примере, является тестовым сертификатом, созданным с помощью Makecert. exe, оповещение системы безопасности отображается при попытке доступа к HTTPS-адресу в браузере, например `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="40810-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="40810-139">Чтобы разрешить клиенту WCF работать с тестовым сертификатом, к клиенту был добавлен дополнительный код для подавления оповещения системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="40810-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="40810-140">При использовании рабочих сертификатов этот код и соответствующие классы не требуются.</span><span class="sxs-lookup"><span data-stu-id="40810-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
