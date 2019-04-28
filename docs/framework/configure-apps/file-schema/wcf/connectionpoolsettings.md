---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: b1ff302a46605cb78fe567a63f66723ed757f147
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704314"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="8c634-101">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="8c634-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="8c634-102">Задает дополнительные параметры пула подключений для привязки именованного канала.</span><span class="sxs-lookup"><span data-stu-id="8c634-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="8c634-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8c634-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8c634-104">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="8c634-104">\<bindings></span></span>  
<span data-ttu-id="8c634-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c634-105">\<customBinding></span></span>  
<span data-ttu-id="8c634-106">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="8c634-106">\<binding></span></span>  
<span data-ttu-id="8c634-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="8c634-107">\<namePipeTransport></span></span>  
<span data-ttu-id="8c634-108">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="8c634-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c634-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8c634-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c634-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8c634-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c634-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8c634-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c634-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8c634-112">Attributes</span></span>  
  
|<span data-ttu-id="8c634-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8c634-113">Attribute</span></span>|<span data-ttu-id="8c634-114">Описание</span><span class="sxs-lookup"><span data-stu-id="8c634-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="8c634-115">Строка, определяющая имя пула подключений, используемого для исходящих каналов.</span><span class="sxs-lookup"><span data-stu-id="8c634-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="8c634-116">В потоковом режиме общий доступ к подключениям не предоставляется, то есть пул подключений отключен.</span><span class="sxs-lookup"><span data-stu-id="8c634-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="8c634-117">Значение по умолчанию - строка «default».</span><span class="sxs-lookup"><span data-stu-id="8c634-117">The default is a "default" string.</span></span> <span data-ttu-id="8c634-118">Это значение можно изменить, чтобы изолировать подключения для конкретного клиента в отдельные группы.</span><span class="sxs-lookup"><span data-stu-id="8c634-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="8c634-119">Положительное значение <xref:System.TimeSpan>, указывающее максимальное время бездействия для подключения перед его закрытием.</span><span class="sxs-lookup"><span data-stu-id="8c634-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="8c634-120">Значение по умолчанию - 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="8c634-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="8c634-121">Положительное целое число, указывающее максимальное число подключений к удаленной конечной точке, инициированных одной службой.</span><span class="sxs-lookup"><span data-stu-id="8c634-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="8c634-122">Соединения сверх лимита помещаются в очередь до высвобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8c634-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="8c634-123">Параметр `idleTimeout` ограничивает продолжительность времени, в течение которого подключения остаются в очереди до возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="8c634-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="8c634-124">Значение по умолчанию — 10.</span><span class="sxs-lookup"><span data-stu-id="8c634-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="8c634-125">Этот атрибут ограничивает число одновременных активных подключений клиента к конкретной конечной точке службы.</span><span class="sxs-lookup"><span data-stu-id="8c634-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="8c634-126">В случае превышения этого значения при наличии большего числа активных соединений клиентов служба может прекратить отвечать на запросы клиента.</span><span class="sxs-lookup"><span data-stu-id="8c634-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="8c634-127">В таком случае это значение следует скорректировать, чтобы оно было больше предполагаемого максимума одновременных подключений клиента к конкретной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="8c634-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c634-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8c634-128">Child Elements</span></span>  
 <span data-ttu-id="8c634-129">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8c634-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c634-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8c634-130">Parent Elements</span></span>  
  
|<span data-ttu-id="8c634-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="8c634-131">Element</span></span>|<span data-ttu-id="8c634-132">Описание</span><span class="sxs-lookup"><span data-stu-id="8c634-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c634-133">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="8c634-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="8c634-134">Определяет транспорт, вызывающий передачу сообщений с использованием именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="8c634-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c634-135">См. также</span><span class="sxs-lookup"><span data-stu-id="8c634-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8c634-136">Транспорты</span><span class="sxs-lookup"><span data-stu-id="8c634-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="8c634-137">Выбор транспорта</span><span class="sxs-lookup"><span data-stu-id="8c634-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="8c634-138">Привязки</span><span class="sxs-lookup"><span data-stu-id="8c634-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8c634-139">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="8c634-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8c634-140">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="8c634-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8c634-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c634-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
