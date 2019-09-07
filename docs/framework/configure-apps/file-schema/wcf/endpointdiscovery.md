---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398020"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="f462b-101">\<Ендпоинтдисковери ></span><span class="sxs-lookup"><span data-stu-id="f462b-101">\<endpointDiscovery></span></span>
<span data-ttu-id="f462b-102">Указывает различные параметры обнаружения для конечной точки, такие как возможность обнаружения, области и любые пользовательские модули для ее метаданных.</span><span class="sxs-lookup"><span data-stu-id="f462b-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="f462b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f462b-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f462b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> поведения**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f462b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f462b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> поведения**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f462b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ендпоинтдисковери >**</span><span class="sxs-lookup"><span data-stu-id="f462b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f462b-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f462b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f462b-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f462b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f462b-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f462b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f462b-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f462b-112">Attributes</span></span>  
  
|<span data-ttu-id="f462b-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f462b-113">Attribute</span></span>|<span data-ttu-id="f462b-114">Описание</span><span class="sxs-lookup"><span data-stu-id="f462b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f462b-115">enabled</span><span class="sxs-lookup"><span data-stu-id="f462b-115">enabled</span></span>|<span data-ttu-id="f462b-116">Логическое значение, указывающее, включена ли возможность обнаружения в этой конечной точке.</span><span class="sxs-lookup"><span data-stu-id="f462b-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="f462b-117">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="f462b-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f462b-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f462b-118">Child Elements</span></span>  
  
|<span data-ttu-id="f462b-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="f462b-119">Element</span></span>|<span data-ttu-id="f462b-120">Описание</span><span class="sxs-lookup"><span data-stu-id="f462b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f462b-121">\<области ></span><span class="sxs-lookup"><span data-stu-id="f462b-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f462b-122">Коллекция URI областей для этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="f462b-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="f462b-123">С одной конечной точкой можно связать несколько URI областей.</span><span class="sxs-lookup"><span data-stu-id="f462b-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="f462b-124">расширения > [из \<ендпоинтдисковери >] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="f462b-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="f462b-125">Коллекция элементов XML, позволяющая указывать пользовательские метаданные, публикуемые для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="f462b-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="f462b-126">\<типы ></span><span class="sxs-lookup"><span data-stu-id="f462b-126">\<types></span></span>|<span data-ttu-id="f462b-127">Коллекция интерфейсов, которые нужно найти.</span><span class="sxs-lookup"><span data-stu-id="f462b-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f462b-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f462b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f462b-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="f462b-129">Element</span></span>|<span data-ttu-id="f462b-130">Описание</span><span class="sxs-lookup"><span data-stu-id="f462b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f462b-131">\<> поведения</span><span class="sxs-lookup"><span data-stu-id="f462b-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f462b-132">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="f462b-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f462b-133">Примечания</span><span class="sxs-lookup"><span data-stu-id="f462b-133">Remarks</span></span>  
 <span data-ttu-id="f462b-134">Если добавить этот элемент конфигурации в конфигурацию поведения конечной точки и присвоить атрибуту `enabled` значение `true`, то будет включена возможность обнаружения.</span><span class="sxs-lookup"><span data-stu-id="f462b-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="f462b-135">Кроме того, можно использовать [ \<](scopes.md)дочерний элемент области > для указания URI настраиваемых областей, которые можно использовать для фильтрации конечных точек службы во время запроса, [ \<а также расширения >](extensions.md) дочернего элемента для указания пользовательского метаданные, которые должны быть опубликованы вместе со стандартными обнаруживаемыми метаданными (EPR, Контракттипенаме, Биндингнаме, Scope и ListenURI).</span><span class="sxs-lookup"><span data-stu-id="f462b-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="f462b-136">Этот элемент конфигурации зависит [ \<от элемента сервицедисковери >](servicediscovery.md) , который обеспечивает контроль уровня обслуживания для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="f462b-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="f462b-137">Это означает, что параметры этого элемента не учитываются, если [ \<сервицедисковери >](servicediscovery.md) отсутствует в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f462b-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f462b-138">Пример</span><span class="sxs-lookup"><span data-stu-id="f462b-138">Example</span></span>  
 <span data-ttu-id="f462b-139">В следующем примере конфигурации определены области фильтрации и метаданные расширения, которые будут опубликованы для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="f462b-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="f462b-140">См. также</span><span class="sxs-lookup"><span data-stu-id="f462b-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
