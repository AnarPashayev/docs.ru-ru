---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203136"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="21813-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="21813-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="21813-102">Задает параметры для привязки, используемой для обмена сообщениями WS-MetadataExchange (WS-MEX) посредством HTTPS.</span><span class="sxs-lookup"><span data-stu-id="21813-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="21813-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="21813-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="21813-104">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="21813-104">\<bindings></span></span>  
<span data-ttu-id="21813-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="21813-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21813-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="21813-106">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21813-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="21813-107">Attributes and Elements</span></span>  
 <span data-ttu-id="21813-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="21813-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21813-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="21813-109">Attributes</span></span>  
  
|<span data-ttu-id="21813-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="21813-110">Attribute</span></span>|<span data-ttu-id="21813-111">Описание</span><span class="sxs-lookup"><span data-stu-id="21813-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="21813-112">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="21813-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="21813-113">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21813-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21813-114">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21813-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="21813-115">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="21813-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="21813-116">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="21813-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="21813-117">Каждая привязка имеет атрибуты `name` и `namespace`, которые совместно однозначно идентифицируют привязку в метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="21813-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="21813-118">Кроме того, это имя является уникальным среди привязок одного типа.</span><span class="sxs-lookup"><span data-stu-id="21813-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="21813-119">Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена.</span><span class="sxs-lookup"><span data-stu-id="21813-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="21813-120">Дополнительные сведения о конфигурации по умолчанию и безымянных привязках и поведениях см. в разделе [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="21813-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="21813-121">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="21813-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="21813-122">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21813-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21813-123">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21813-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="21813-124">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="21813-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="21813-125">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21813-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21813-126">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="21813-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="21813-127">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="21813-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="21813-128">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="21813-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="21813-129">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="21813-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21813-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="21813-130">Child Elements</span></span>  
 <span data-ttu-id="21813-131">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="21813-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21813-132">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="21813-132">Parent Elements</span></span>  
  
|<span data-ttu-id="21813-133">Элемент</span><span class="sxs-lookup"><span data-stu-id="21813-133">Element</span></span>|<span data-ttu-id="21813-134">Описание</span><span class="sxs-lookup"><span data-stu-id="21813-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21813-135">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="21813-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="21813-136">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="21813-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21813-137">Примечания</span><span class="sxs-lookup"><span data-stu-id="21813-137">Remarks</span></span>  
 <span data-ttu-id="21813-138">Эта привязка по существу является привязкой `WSHttpBinding`, которая поддерживает безопасность уровня транспорта с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="21813-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="21813-139">Дополнительные сведения о настройке и использовании такой конечной точки метаданных см. в разделе [как: Настройка пользовательских WS-Metadata Exchange привязки](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [как: Получение метаданных через - MEX привязку, не](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), образец [конечной точки метаданных Secure Custom](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="21813-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21813-140">См. также</span><span class="sxs-lookup"><span data-stu-id="21813-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="21813-141">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="21813-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="21813-142">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="21813-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="21813-143">Практическое руководство. Настройка пользовательской привязки для обмена WS-Metadata</span><span class="sxs-lookup"><span data-stu-id="21813-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="21813-144">Практическое руководство. Получение метаданных через привязку, не использующую MEX</span><span class="sxs-lookup"><span data-stu-id="21813-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="21813-145">Пользовательская конечная точка защищенных метаданных</span><span class="sxs-lookup"><span data-stu-id="21813-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="21813-146">Метаданные</span><span class="sxs-lookup"><span data-stu-id="21813-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="21813-147">Привязки</span><span class="sxs-lookup"><span data-stu-id="21813-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="21813-148">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="21813-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="21813-149">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="21813-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="21813-150">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="21813-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
