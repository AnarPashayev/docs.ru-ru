---
title: Настройка служб с использованием файлов конфигурации
description: Узнайте, как файл конфигурации для службы WCF предоставляет гибкие возможности предоставления данных о поведении конечных точек и служб во время развертывания.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 1a3266ad8890436c9be9d0f2b231aeaca0f9236e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245431"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="e0ca1-103">Настройка служб с использованием файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="e0ca1-103">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="e0ca1-104">Настройка службы Windows Communication Foundation (WCF) с помощью файла конфигурации обеспечивает гибкость предоставления данных о поведении конечных точек и служб в точке развертывания, а не во время разработки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-104">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="e0ca1-105">В этой теме представлено описание основных доступных методов.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-105">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="e0ca1-106">Службу WCF можно настроить с помощью технологии настройки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-106">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="e0ca1-107">Чаще всего XML-элементы добавляются в файл Web.config для сайта службы IIS (IIS), на котором размещена служба WCF.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-107">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="e0ca1-108">Эти элементы позволяют изменять данные, такие как адреса конечных точек (фактические адреса, используемые для взаимодействия со службой), по схеме компьютер-компьютер.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-108">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="e0ca1-109">Кроме того, в состав WCF входит несколько предоставляемых системой элементов, которые позволяют быстро выбрать наиболее простые функции для службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-109">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="e0ca1-110">Начиная с .NET Framework 4, WCF поставляется с новой моделью конфигурации по умолчанию, которая упрощает требования к конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="e0ca1-111">Если не указать конфигурацию WCF для конкретной службы, среда выполнения автоматически настроит службу с помощью некоторых стандартных конечных точек, а также привязки или поведения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="e0ca1-112">На практике написание конфигурации является основной частью программирования приложений WCF.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-112">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="e0ca1-113">Дополнительные сведения см. в разделе [Настройка привязок для служб](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0ca1-113">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="e0ca1-114">Список наиболее часто используемых элементов см. в разделе привязки, [предоставляемые системой](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e0ca1-114">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="e0ca1-115">Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](simplified-configuration.md) и [Упрощенная конфигурация служб WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0ca1-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0ca1-116">При развертывании сценариев параллельного выполнения, в которых развернуты две различные версии службы, необходимо указывать частичные имена сборок, на которые ссылаются файлы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-116">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="e0ca1-117">Это связано с тем, что файл конфигурации совместно используется всеми версиями службы, которые могут выполняться под управлением различных версий платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-117">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="e0ca1-118">System.Configuration: Web.config и App.config</span><span class="sxs-lookup"><span data-stu-id="e0ca1-118">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="e0ca1-119">WCF использует систему конфигурации System.Configфигурации в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-119">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e0ca1-120">При настройке службы в Visual Studio используйте либо файл Web.config, либо файл App.config, чтобы указать параметры.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-120">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="e0ca1-121">Выбор имени файла конфигурации определяется выбранной для службы средой размещения.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-121">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="e0ca1-122">Если служба размещается с помощью IIS, используйте файл Web.config.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-122">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="e0ca1-123">Если служба размещается с помощью другой среды размещения, используйте файл App.config.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-123">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="e0ca1-124">В Visual Studio файл с именем App.config используется для создания окончательного файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-124">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="e0ca1-125">Окончательное имя, которое фактически используется для конфигурации, зависит от имени сборки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-125">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="e0ca1-126">Например, сборка с именем "Cohowinery.exe" имеет имя окончательного файла конфигурации "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="e0ca1-126">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="e0ca1-127">Однако следует изменить только файл App.config.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-127">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="e0ca1-128">Изменения, внесенные в это файл, автоматически вносятся в окончательный файл конфигурации приложения во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-128">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="e0ca1-129">При использовании файла App.config система конфигурации объединяет файл App.config с содержимым файла Machine.config, когда запускается приложение и применяется конфигурация.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-129">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="e0ca1-130">Этот механизм позволяет определить параметры в рамках всего компьютера в файле Machine.config.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-130">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="e0ca1-131">Файл App.config можно использовать для переопределения параметров файла Machine.config. Также предусмотрена возможность блокировки в параметрах файла Machine.config согласно привычной работе.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-131">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="e0ca1-132">Если используется файл конфигурации Web.config, то система объединяет файлы Web.config во всех родительских каталогах вплоть до каталога приложения в применяемой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-132">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="e0ca1-133">Дополнительные сведения о конфигурации и параметрах приоритетов см. в разделе разделы в <xref:System.Configuration> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-133">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="e0ca1-134">Основные разделы файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e0ca1-134">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="e0ca1-135">Основные разделы файла конфигурации включают в себя следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-135">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="e0ca1-136">Разделы привязок и поведения являются необязательными и указываются только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-136">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="e0ca1-137">\<services>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-137">The \<services> Element</span></span>  
 <span data-ttu-id="e0ca1-138">Элемент `services` содержит спецификации для всех служб, которые размещает приложение.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-138">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="e0ca1-139">Начиная с упрощенной модели конфигурации в .NET Framework 4, этот раздел является необязательным.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-139">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="e0ca1-140">\<service>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-140">The \<service> Element</span></span>  
 <span data-ttu-id="e0ca1-141">Каждая служба имеет следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="e0ca1-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-142">`name`.</span></span> <span data-ttu-id="e0ca1-143">Определяет тип, обеспечивающий реализацию контракта службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="e0ca1-144">Это полное имя, состоящее из пространства имен, точки и имени типа,</span><span class="sxs-lookup"><span data-stu-id="e0ca1-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="e0ca1-145">Например, `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="e0ca1-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="e0ca1-147">Задает имя одного из элементов `behavior` , найденных в `behaviors` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="e0ca1-148">Заданное поведение управляет действиями, например, разрешает ли служба олицетворение.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="e0ca1-149">Если значением является пустое имя, или объект `behaviorConfiguration` не указан, то в службу добавляется набор поведений службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="e0ca1-150">\<endpoint>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-150">The \<endpoint> Element</span></span>  
 <span data-ttu-id="e0ca1-151">Для каждой конечной точки требуется адрес, привязка и контракт, представленные следующими атрибутами:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-151">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="e0ca1-152">`address`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-152">`address`.</span></span> <span data-ttu-id="e0ca1-153">Задает универсальный код ресурса (URI) службы, который может быть абсолютным адресом или адресом, указанным относительно базового адреса службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-153">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="e0ca1-154">Если задана пустая строка, это означает, что конечная точка доступна по базовому адресу, который указывается при создании <xref:System.ServiceModel.ServiceHost> для службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-154">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="e0ca1-155">`binding`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-155">`binding`.</span></span> <span data-ttu-id="e0ca1-156">Как правило, задает предоставляемую системой привязку типа <xref:System.ServiceModel.WSHttpBinding>, но также может задавать определяемую пользователем привязку.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-156">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="e0ca1-157">Заданная привязка определяет используемый тип транспорта, безопасности и кодирования, а также поддерживаются ли или включены ли надежные сеансы, транзакции или потоковая передача.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-157">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="e0ca1-158">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-158">`bindingConfiguration`.</span></span> <span data-ttu-id="e0ca1-159">Если требуется изменить значения привязки по умолчанию, можно настроить соответствующий элемент `binding` в элементе `bindings` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-159">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="e0ca1-160">Этому атрибуту должно быть присвоено то же значение, что и атрибуту `name` элемента `binding` , который используется для изменения значений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-160">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="e0ca1-161">Если имя не задано, или в привязке не задан объект `bindingConfiguration` , то в конечной точке используется привязка по умолчанию типа привязки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-161">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="e0ca1-162">`contract`.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-162">`contract`.</span></span> <span data-ttu-id="e0ca1-163">Задает интерфейс, определяющий контракт.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-163">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="e0ca1-164">Это интерфейс, реализованный в типе CLR, который задан атрибутом `name` элемента `service` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-164">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="e0ca1-165">\<bindings>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-165">The \<bindings> Element</span></span>  
 <span data-ttu-id="e0ca1-166">Элемент `bindings` содержит спецификации для всех привязок, которые могут использоваться любой конечной точкой, заданной в любой службе.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-166">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="e0ca1-167">\<binding>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-167">The \<binding> Element</span></span>  
 <span data-ttu-id="e0ca1-168">Элемент `binding` , содержащиеся в элементе `bindings` , могут являться одной из предоставленных системой привязок (см. раздел [System-Provided Bindings](system-provided-bindings.md)) или пользовательской привязкой (см. раздел [Custom Bindings](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="e0ca1-168">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="e0ca1-169">Элемент `binding` имеет атрибут `name` , сопоставляющий привязку с конечной точкой, заданной в атрибуте `bindingConfiguration` элемента `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-169">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="e0ca1-170">Если имя не указано, то привязка будет соответствовать значению по умолчанию для этого типа привязки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-170">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="e0ca1-171">Дополнительные сведения о настройке служб и клиентов см. в разделе [Настройка служб WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0ca1-171">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="e0ca1-172">\<behaviors>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-172">The \<behaviors> Element</span></span>  
 <span data-ttu-id="e0ca1-173">Это элемент контейнера для элементов `behavior` , задающих поведение службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-173">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="e0ca1-174">\<behavior>Элемент</span><span class="sxs-lookup"><span data-stu-id="e0ca1-174">The \<behavior> Element</span></span>  
 <span data-ttu-id="e0ca1-175">Каждый `behavior` элемент определяется `name` атрибутом и предоставляет либо предоставляемое системой поведение, например <`throttling`>, либо пользовательское поведение.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-175">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="e0ca1-176">Если имя не задано, то элемент behavior будет соответствовать поведению по умолчанию для службы или конечной точки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-176">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="e0ca1-177">Практическое руководство. Конфигурации привязок и поведения</span><span class="sxs-lookup"><span data-stu-id="e0ca1-177">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="e0ca1-178">WCF упрощает совместное использование конфигураций между конечными точками с помощью эталонной системы в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-178">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="e0ca1-179">Вместо того, чтобы непосредственно назначать значения конфигурации для конечной точки, значения конфигурации, относящиеся к привязке, группируются в элементах `bindingConfiguration` в разделе `<binding>` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-179">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="e0ca1-180">Конфигурация привязок представляет собой именованную группу параметров привязки.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-180">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="e0ca1-181">Конечные точки могут ссылаться на `bindingConfiguration` по имени.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-181">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e0ca1-182">`name` для `bindingConfiguration` задано в элементе `<binding>` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-182">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="e0ca1-183">`name`Должна быть уникальной строкой в области действия типа привязки — в данном случае [<\> BasicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)или пустое значение для ссылки на привязку по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-183">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="e0ca1-184">Конечная точка содержит ссылки на конфигурацию, задавая для этой строки атрибут `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="e0ca1-184">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="e0ca1-185">`behaviorConfiguration` реализуется аналогичным образом, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-185">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e0ca1-186">Заметьте, что в службу добавляет по умолчанию набор поведений службы.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-186">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="e0ca1-187">Эта система обеспечивает для конечных точек совместные общие конфигурации, не переопределяя параметры.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-187">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="e0ca1-188">Если требуется область на уровне компьютера, создайте конфигурацию привязки или поведения в файле Machine.config. Параметры конфигурации указаны во всех файлах App.config.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-188">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="e0ca1-189">[Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) упрощает создание конфигураций.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-189">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="e0ca1-190">Слияние поведений</span><span class="sxs-lookup"><span data-stu-id="e0ca1-190">Behavior Merge</span></span>  
 <span data-ttu-id="e0ca1-191">Функция слияния поведений упрощает управление поведениями в ситуациях, когда должен постоянно использоваться набор общих поведений.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-191">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="e0ca1-192">Эта функция позволяет задавать поведения на разных уровнях иерархии конфигурации, а также настраивать наследование службами поведений от нескольких уровней иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-192">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="e0ca1-193">Проиллюстрируем это следующим образом: предположим, что в IIS имеется следующая структура виртуальных каталогов:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-193">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="e0ca1-194">`~\Web.config`Файл содержит следующее содержимое:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-194">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e0ca1-195">Кроме того, имеется дочерний файл Web.config, расположенный в папке ~\Child\Web.config, со следующим содержимым:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-195">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e0ca1-196">Служба, расположенная в ~\Child\Service.svc, будет действовать таким образом, как будто бы для нее заданы и поведение serviceDebug, и поведение serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-196">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="e0ca1-197">У службы, расположенной в ~\Service.svc, будет присутствовать только поведение serviceDebug behavior.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-197">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="e0ca1-198">В этой ситуации две коллекции поведений с одним и тем же именем (в данном случае пустой строкой) объединяются.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-198">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="e0ca1-199">Можно также очистить коллекции поведения с помощью \<clear> тега и удалить отдельные поведения из коллекции с помощью \<remove> тега.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-199">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="e0ca1-200">Например, действие следующих двух конфигураций приведет к тому, что в дочерней службе будет только поведение serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="e0ca1-200">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e0ca1-201">Слияние поведений проводится для безымянных коллекций поведений (как показано выше), а также для именованных коллекций поведений.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-201">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="e0ca1-202">Слияние поведения работает в среде размещения IIS, в которой Web.config файлы объединяются иерархически с корневым Web.configным файлом и machine.config. Но он также работает в среде приложения, где machine.config может объединяться с App.configным файлом.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-202">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="e0ca1-203">Слияние поведений применяется в конфигурациях как к поведениям конечных точек, так и к поведениям служб.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-203">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="e0ca1-204">Если коллекция дочерних поведений содержит поведение, которое уже определено в коллекции родительских поведений, то дочернее поведение переопределяет родительское.</span><span class="sxs-lookup"><span data-stu-id="e0ca1-204">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="e0ca1-205">Таким образом, если в родительской коллекции поведения существовала `<serviceMetadata httpGetEnabled="False" />` и Дочерняя коллекция поведений существовала `<serviceMetadata httpGetEnabled="True" />` , дочернее поведение будет переопределять родительское поведение в коллекции поведения, а хттпжетенаблед — «true».</span><span class="sxs-lookup"><span data-stu-id="e0ca1-205">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ca1-206">См. также</span><span class="sxs-lookup"><span data-stu-id="e0ca1-206">See also</span></span>

- [<span data-ttu-id="e0ca1-207">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="e0ca1-207">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="e0ca1-208">Настройка служб WCF</span><span class="sxs-lookup"><span data-stu-id="e0ca1-208">Configuring WCF services</span></span>](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
