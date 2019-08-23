---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8a59f651318e18411b1485fc4eebeb7a550afca0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919858"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="f6179-101">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="f6179-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="f6179-102">Представляет коллекцию элементов конфигурации, задающих сквозные фильтры, которые предоставляют механизм для выбора соответствующих привязок службы IIS (IIS) при размещении приложения Windows Communication Foundation (WCF) в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="f6179-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f6179-103">\<baseAddressPrefixFilters > не распознает "localhost", используйте вместо этого полное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="f6179-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="f6179-104">\<системой. > ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f6179-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6179-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f6179-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6179-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6179-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6179-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f6179-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f6179-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f6179-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6179-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f6179-109">Attributes</span></span>  
 <span data-ttu-id="f6179-110">Нет.</span><span class="sxs-lookup"><span data-stu-id="f6179-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f6179-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f6179-111">Child Elements</span></span>  
  
|<span data-ttu-id="f6179-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="f6179-112">Element</span></span>|<span data-ttu-id="f6179-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f6179-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6179-114">\<add></span><span class="sxs-lookup"><span data-stu-id="f6179-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="f6179-115">Добавляет элемент конфигурации, который задает префиксный фильтр для базовых адресов, используемых узлом службы.</span><span class="sxs-lookup"><span data-stu-id="f6179-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6179-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f6179-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f6179-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="f6179-117">Element</span></span>|<span data-ttu-id="f6179-118">Описание</span><span class="sxs-lookup"><span data-stu-id="f6179-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6179-119">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f6179-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="f6179-120">Определяет, какой тип среда размещения служб создает для конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="f6179-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6179-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="f6179-121">Remarks</span></span>  
 <span data-ttu-id="f6179-122">Префиксный фильтр предоставляет способ для общих поставщиков услуг размещения задать, какие URI должны использоваться службой.</span><span class="sxs-lookup"><span data-stu-id="f6179-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="f6179-123">Это дает возможность общим узлам размещать несколько приложений с разными базовыми адресами для одной схемы на одном узле.</span><span class="sxs-lookup"><span data-stu-id="f6179-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="f6179-124">Веб-узлы IIS являются контейнерами виртуальных приложений, содержащими виртуальные каталоги.</span><span class="sxs-lookup"><span data-stu-id="f6179-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="f6179-125">Доступ к приложению на узле можно осуществлять через одну или несколько привязок службы IIS.</span><span class="sxs-lookup"><span data-stu-id="f6179-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="f6179-126">Привязки IIS предоставляют два блока данных: протокол привязки и данные привязки.</span><span class="sxs-lookup"><span data-stu-id="f6179-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="f6179-127">Протокол привязки (например, HTTP) определяет схему, посредством которой осуществляется связь, а данные привязки (например, IP-адрес, порт, заголовок узла) содержат сведения, используемые для доступа к узлу.</span><span class="sxs-lookup"><span data-stu-id="f6179-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="f6179-128">IIS поддерживает задание нескольких привязок IIS для каждого узла, что позволяет использовать несколько базовых адресов для каждой схемы.</span><span class="sxs-lookup"><span data-stu-id="f6179-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="f6179-129">Так как служба WCF, размещенная на сайте, допускает привязку только к одному базовому адресу для каждой схемы, можно использовать функцию фильтрации префиксов, чтобы выбрать необходимый базовый адрес размещенной службы.</span><span class="sxs-lookup"><span data-stu-id="f6179-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="f6179-130">Входящие базовые адреса, предоставляемые IIS, фильтруются с использованием дополнительного фильтра списка префиксов.</span><span class="sxs-lookup"><span data-stu-id="f6179-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="f6179-131">Например, узел может содержать следующие базовые адреса.</span><span class="sxs-lookup"><span data-stu-id="f6179-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="f6179-132">Для задания префиксного фильтра на уровне домена приложений можно использовать следующий файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f6179-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="f6179-133">В этом примере `net.tcp://test1.fabrikam.com:8000` и `http://test2.fabrikam.com:9000` являются единственными базовыми адресами для соответствующих схем, которые могут пропускаться.</span><span class="sxs-lookup"><span data-stu-id="f6179-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="f6179-134">Если префикс не задан, по умолчанию пропускаются все адреса.</span><span class="sxs-lookup"><span data-stu-id="f6179-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="f6179-135">При задании префикса разрешается прохождение данных только с соответствующего базового адреса для данной схемы.</span><span class="sxs-lookup"><span data-stu-id="f6179-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6179-136">Фильтр не поддерживает какие-либо подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="f6179-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="f6179-137">Кроме того, среди базовых адресов, предоставляемых IIS, могут присутствовать адреса, привязанные к другим схемам, не представленным в списке `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="f6179-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="f6179-138">Эти адреса не фильтруются.</span><span class="sxs-lookup"><span data-stu-id="f6179-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6179-139">См. также</span><span class="sxs-lookup"><span data-stu-id="f6179-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="f6179-140">Размещение</span><span class="sxs-lookup"><span data-stu-id="f6179-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
