---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: c6ff5b2cfee1d55b9399b97f3b3397e6bbf8eca2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400244"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="45425-101">\<Мексхттпбиндинг ></span><span class="sxs-lookup"><span data-stu-id="45425-101">\<mexHttpBinding></span></span>
<span data-ttu-id="45425-102">Задает параметры для привязки, используемой для обмена сообщениями WS-MetadataExchange (WS-MEX) по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="45425-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="45425-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45425-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45425-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="45425-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="45425-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<привязки >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="45425-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="45425-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Мексхттпбиндинг >**</span><span class="sxs-lookup"><span data-stu-id="45425-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45425-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45425-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45425-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="45425-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45425-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="45425-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45425-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="45425-110">Attributes</span></span>  
  
|<span data-ttu-id="45425-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="45425-111">Attribute</span></span>|<span data-ttu-id="45425-112">Описание</span><span class="sxs-lookup"><span data-stu-id="45425-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="45425-113">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="45425-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="45425-114">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="45425-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="45425-115">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="45425-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="45425-116">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="45425-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="45425-117">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="45425-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="45425-118">Каждая привязка имеет атрибуты `name` и `namespace`, которые совместно однозначно идентифицируют привязку в метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="45425-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="45425-119">Кроме того, это имя является уникальным среди привязок одного типа.</span><span class="sxs-lookup"><span data-stu-id="45425-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="45425-120">Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена.</span><span class="sxs-lookup"><span data-stu-id="45425-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="45425-121">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="45425-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="45425-122">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="45425-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="45425-123">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="45425-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="45425-124">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="45425-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="45425-125">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="45425-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="45425-126">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="45425-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="45425-127">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="45425-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="45425-128">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="45425-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="45425-129">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="45425-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="45425-130">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="45425-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45425-131">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="45425-131">Child Elements</span></span>  
 <span data-ttu-id="45425-132">Нет.</span><span class="sxs-lookup"><span data-stu-id="45425-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45425-133">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="45425-133">Parent Elements</span></span>  
  
|<span data-ttu-id="45425-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="45425-134">Element</span></span>|<span data-ttu-id="45425-135">Описание</span><span class="sxs-lookup"><span data-stu-id="45425-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45425-136">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="45425-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="45425-137">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="45425-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45425-138">Примечания</span><span class="sxs-lookup"><span data-stu-id="45425-138">Remarks</span></span>  
 <span data-ttu-id="45425-139">Эта привязка по существу является привязкой `WSHttpBinding` с отключенной безопасностью.</span><span class="sxs-lookup"><span data-stu-id="45425-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="45425-140">Она поддерживает большинство запросов метаданных.</span><span class="sxs-lookup"><span data-stu-id="45425-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45425-141">См. также</span><span class="sxs-lookup"><span data-stu-id="45425-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="45425-142">Практическое руководство. Публикация метаданных для службы с помощью файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="45425-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="45425-143">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="45425-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="45425-144">Метаданные</span><span class="sxs-lookup"><span data-stu-id="45425-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="45425-145">Привязки</span><span class="sxs-lookup"><span data-stu-id="45425-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45425-146">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="45425-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="45425-147">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="45425-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="45425-148">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="45425-148">\<binding></span></span>](../../../misc/binding.md)
