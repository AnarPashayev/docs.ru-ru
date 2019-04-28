---
title: <add> из <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704496"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="0dfee-102">\<Добавить > из \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="0dfee-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="0dfee-103">Представляет сопоставление протокола по умолчанию между схемой транспортного протокола (например, http, net.tcp, net.pipe, и т.д.) и привязкой Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0dfee-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="0dfee-104">При создании конечных точек по умолчанию во время выполнения, WCF просматривает заданные сопоставления и решает, какую привязку необходимо использовать для определенного базового адреса.</span><span class="sxs-lookup"><span data-stu-id="0dfee-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="0dfee-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0dfee-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0dfee-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="0dfee-106">\<protocolMapping></span></span>  
<span data-ttu-id="0dfee-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0dfee-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfee-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0dfee-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dfee-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0dfee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0dfee-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0dfee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dfee-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0dfee-111">Attributes</span></span>  
  
|<span data-ttu-id="0dfee-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="0dfee-112">Element</span></span>|<span data-ttu-id="0dfee-113">Описание</span><span class="sxs-lookup"><span data-stu-id="0dfee-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0dfee-114">привязка</span><span class="sxs-lookup"><span data-stu-id="0dfee-114">binding</span></span>|<span data-ttu-id="0dfee-115">Строка, в которой указан тип привязки, используемый для конечной точки во время создания конечной точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0dfee-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="0dfee-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0dfee-116">bindingConfiguration</span></span>|<span data-ttu-id="0dfee-117">Строка, содержащая имя раздела конфигурации привязки, на который будет установлена ссылка.</span><span class="sxs-lookup"><span data-stu-id="0dfee-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="0dfee-118">scheme</span><span class="sxs-lookup"><span data-stu-id="0dfee-118">scheme</span></span>|<span data-ttu-id="0dfee-119">Схема транспортного протокола, которая будет использоваться для конечной точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0dfee-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dfee-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0dfee-120">Child Elements</span></span>  
 <span data-ttu-id="0dfee-121">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0dfee-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dfee-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0dfee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0dfee-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="0dfee-123">Element</span></span>|<span data-ttu-id="0dfee-124">Описание</span><span class="sxs-lookup"><span data-stu-id="0dfee-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dfee-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="0dfee-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="0dfee-126">Представляет раздел конфигурации для определения сопоставлений протоколов по умолчанию между схемами транспортных протоколов (например, http, net.tcp, net.pipe, и т.д.) и привязками Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0dfee-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0dfee-127">Пример</span><span class="sxs-lookup"><span data-stu-id="0dfee-127">Example</span></span>  
 <span data-ttu-id="0dfee-128">В следующем примере конфигурации показано сопоставление протокола по умолчанию в файле machine.config.</span><span class="sxs-lookup"><span data-stu-id="0dfee-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="0dfee-129">Это сопоставление по умолчанию можно переопределить на уровне компьютера путем изменения файла machine.config.</span><span class="sxs-lookup"><span data-stu-id="0dfee-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="0dfee-130">Или же, если необходимо переопределить это сопоставление только в области приложения, можно отменить этот раздел в файле конфигурации приложения и изменить сопоставление для отдельных схем протокола.</span><span class="sxs-lookup"><span data-stu-id="0dfee-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="0dfee-131">См. также</span><span class="sxs-lookup"><span data-stu-id="0dfee-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
