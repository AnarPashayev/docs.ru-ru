---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: b81c9f3c4260f415f057cd74b6f113d88f635978
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936288"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="4844c-101">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="4844c-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="4844c-102">Этот элемент определяет тип, который среда размещения служб создает для определенного транспорта.</span><span class="sxs-lookup"><span data-stu-id="4844c-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="4844c-103">Если этот элемент является пустым, используется тип, применяемый по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4844c-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="4844c-104">Этот элемент может применяться только на уровне файлов конфигурации приложения или компьютера.</span><span class="sxs-lookup"><span data-stu-id="4844c-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="4844c-105">\<системой. > ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4844c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4844c-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="4844c-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4844c-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4844c-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4844c-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4844c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4844c-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4844c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4844c-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4844c-110">Attributes</span></span>  
  
|<span data-ttu-id="4844c-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4844c-111">Attribute</span></span>|<span data-ttu-id="4844c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="4844c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4844c-113">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="4844c-113">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="4844c-114">Логическое значение, указывающее, включен ли режим совместимости ASP.NET для текущего приложения.</span><span class="sxs-lookup"><span data-stu-id="4844c-114">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="4844c-115">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="4844c-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4844c-116">Если этот атрибут имеет значение `true`, запросы к службам Windows Communication Foundation (WCF) проходят через конвейер HTTP ASP.NET, и связь по протоколам, отличным от HTTP, запрещена.</span><span class="sxs-lookup"><span data-stu-id="4844c-116">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="4844c-117">Дополнительные сведения см. в разделе [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="4844c-117">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="4844c-118">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="4844c-118">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="4844c-119">Целое число, указывающее минимальный объем свободной памяти, который должен быть доступен системе, прежде чем служба WCF сможет быть активирована.</span><span class="sxs-lookup"><span data-stu-id="4844c-119">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="4844c-120">**Внимание!**  <xref:System.Security.SecurityException> Если указать этот атрибут вместе с частичным доверием в файле Web. config службы WCF, то при запуске службы будет возникать исключение.</span><span class="sxs-lookup"><span data-stu-id="4844c-120">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="4844c-121">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="4844c-121">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="4844c-122">Логическое значение, которое определяет, разрешается ли использование нескольких привязок IIS для одного узла.</span><span class="sxs-lookup"><span data-stu-id="4844c-122">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="4844c-123">Службы IIS состоят из веб-узлов, являющихся контейнерами виртуальных приложений, содержащих виртуальные каталоги.</span><span class="sxs-lookup"><span data-stu-id="4844c-123">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="4844c-124">Доступ к приложению на узле можно осуществлять через одну или несколько привязок IIS.</span><span class="sxs-lookup"><span data-stu-id="4844c-124">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="4844c-125">Привязка IIS предоставляет два блока данных: протокол привязки и данные привязки.</span><span class="sxs-lookup"><span data-stu-id="4844c-125">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="4844c-126">Протокол привязки определяет схему, посредством которой осуществляется связь, а данные привязки содержат сведения, используемые для доступа к узлу.</span><span class="sxs-lookup"><span data-stu-id="4844c-126">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="4844c-127">Примером протокола привязки является HTTP, в котором данные привязки могут содержать IP-адрес, порт, заголовок узла и т. п.</span><span class="sxs-lookup"><span data-stu-id="4844c-127">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="4844c-128">IIS поддерживает задание нескольких привязок IIS для каждого узла, что позволяет использовать несколько базовых адресов для каждой схемы.</span><span class="sxs-lookup"><span data-stu-id="4844c-128">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="4844c-129">Однако служба Windows Communication Foundation (WCF), размещенная на сайте, позволяет привязать только к одному baseAddress на схему.</span><span class="sxs-lookup"><span data-stu-id="4844c-129">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="4844c-130">Чтобы включить несколько привязок IIS на сайт для службы Windows Communication Foundation (WCF), присвойте этому атрибуту `true`значение.</span><span class="sxs-lookup"><span data-stu-id="4844c-130">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="4844c-131">Следует иметь в виду, что привязки к нескольким узлам поддерживаются только в протоколе HTTP.</span><span class="sxs-lookup"><span data-stu-id="4844c-131">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="4844c-132">Адрес конечной точки в файле конфигурации должен быть полным URI.</span><span class="sxs-lookup"><span data-stu-id="4844c-132">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4844c-133">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4844c-133">Child Elements</span></span>  
  
|<span data-ttu-id="4844c-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="4844c-134">Element</span></span>|<span data-ttu-id="4844c-135">Описание</span><span class="sxs-lookup"><span data-stu-id="4844c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4844c-136">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="4844c-136">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="4844c-137">Коллекция элементов конфигурации, которые задают префиксные фильтры для базовых адресов, используемых узлом службы.</span><span class="sxs-lookup"><span data-stu-id="4844c-137">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="4844c-138">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="4844c-138">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="4844c-139">Раздел конфигурации, в котором описываются параметры активации.</span><span class="sxs-lookup"><span data-stu-id="4844c-139">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="4844c-140">\<Транспортконфигуратионтипес ></span><span class="sxs-lookup"><span data-stu-id="4844c-140">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="4844c-141">Коллекция элементов конфигурации, которые определяют тип конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="4844c-141">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4844c-142">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4844c-142">Parent Elements</span></span>  
  
|<span data-ttu-id="4844c-143">Элемент</span><span class="sxs-lookup"><span data-stu-id="4844c-143">Element</span></span>|<span data-ttu-id="4844c-144">Описание</span><span class="sxs-lookup"><span data-stu-id="4844c-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4844c-145">serviceModel</span><span class="sxs-lookup"><span data-stu-id="4844c-145">serviceModel</span></span>|<span data-ttu-id="4844c-146">Корневой элемент всех элементов конфигурации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4844c-146">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4844c-147">Примечания</span><span class="sxs-lookup"><span data-stu-id="4844c-147">Remarks</span></span>  
 <span data-ttu-id="4844c-148">По умолчанию службы WCF выполняются параллельно с ASP.NET в размещенных доменах приложений (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="4844c-148">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="4844c-149">Хотя WCF и ASP.NET могут существовать вместе в одном домене приложений, по умолчанию конвейер HTTP ASP.NET не обрабатывает запросы WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-149">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="4844c-150">В результате несколько элементов платформы приложений ASP.NET будут недоступны службам WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-150">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="4844c-151">К ним относятся:</span><span class="sxs-lookup"><span data-stu-id="4844c-151">These include</span></span>  
  
- <span data-ttu-id="4844c-152">Авторизация файла/URL-адреса ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4844c-152">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="4844c-153">Олицетворение ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4844c-153">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="4844c-154">Состояние сеанса на основании файлов Cookie</span><span class="sxs-lookup"><span data-stu-id="4844c-154">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="4844c-155">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="4844c-155">HttpContext.Current</span></span>  
  
- <span data-ttu-id="4844c-156">Расширяемость конвейера через настраиваемый элемент HttpModule</span><span class="sxs-lookup"><span data-stu-id="4844c-156">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="4844c-157">Если службам WCF нужно функционировать в контексте ASP.NET и взаимодействовать только по протоколу HTTP, можно использовать режим совместимости ASP.NET WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-157">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="4844c-158">Этот режим включается, когда атрибут `aspNetCompatibilityEnabled` имеет значение `true` на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="4844c-158">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="4844c-159">В реализации службы должна быть объявлена возможность выполнения в режиме совместимости с помощью класса <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4844c-159">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="4844c-160">Если режим совместимости включен, это приводит к следующему.</span><span class="sxs-lookup"><span data-stu-id="4844c-160">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="4844c-161">Авторизация файла/URL-адреса ASP.NET принудительно выполняется до авторизации WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-161">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="4844c-162">Решение об авторизации основано на удостоверении запроса уровня транспорта.</span><span class="sxs-lookup"><span data-stu-id="4844c-162">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="4844c-163">Удостоверения уровня сообщения не учитываются.</span><span class="sxs-lookup"><span data-stu-id="4844c-163">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="4844c-164">Операции служб WCF начинают выполняться в контексте олицетворения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4844c-164">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="4844c-165">Если для конкретной службы включены и олицетворение ASP.NET, и олицетворение WCF, применяется контекст олицетворения WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-165">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="4844c-166">HttpContext.Current может использоваться из кода службы WCF, и предотвращается представление службами конечных точек, работающих по протоколу, отличному от HTTP.</span><span class="sxs-lookup"><span data-stu-id="4844c-166">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="4844c-167">Запросы WCF обрабатываются конвейером ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4844c-167">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="4844c-168">Элемент HttpModules, заданный для обработки входящих запросов, также может обрабатывать запросы WCF.</span><span class="sxs-lookup"><span data-stu-id="4844c-168">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="4844c-169">Они могут включать компоненты платформы ASP.NET (например, <xref:System.Web.SessionState.SessionStateModule>), а также настраиваемые модули сторонних поставщиков.</span><span class="sxs-lookup"><span data-stu-id="4844c-169">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4844c-170">Пример</span><span class="sxs-lookup"><span data-stu-id="4844c-170">Example</span></span>  
 <span data-ttu-id="4844c-171">В следующем образце кода показано, как включить режим совместимости ASP.</span><span class="sxs-lookup"><span data-stu-id="4844c-171">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="4844c-172">Код</span><span class="sxs-lookup"><span data-stu-id="4844c-172">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="4844c-173">См. также</span><span class="sxs-lookup"><span data-stu-id="4844c-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="4844c-174">Размещение</span><span class="sxs-lookup"><span data-stu-id="4844c-174">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="4844c-175">Службы WCF и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4844c-175">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
