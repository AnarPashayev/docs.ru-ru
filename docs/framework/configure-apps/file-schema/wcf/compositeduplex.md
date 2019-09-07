---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a73085320eaf248887422316e1b7787b8654d71d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400485"
---
# <a name="compositeduplex"></a><span data-ttu-id="35a0a-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="35a0a-101">\<compositeDuplex></span></span>
<span data-ttu-id="35a0a-102">Определяет элемент привязки, который используется, когда клиенту необходимо предоставить службе конечную точку для отправки сообщений обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="35a0a-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="35a0a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35a0a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35a0a-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="35a0a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="35a0a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<привязки >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="35a0a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="35a0a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="35a0a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="35a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Привязка >** </span><span class="sxs-lookup"><span data-stu-id="35a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="35a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="35a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a0a-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35a0a-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35a0a-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="35a0a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="35a0a-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="35a0a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35a0a-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="35a0a-112">Attributes</span></span>  
  
|<span data-ttu-id="35a0a-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="35a0a-113">Attribute</span></span>|<span data-ttu-id="35a0a-114">Описание</span><span class="sxs-lookup"><span data-stu-id="35a0a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35a0a-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="35a0a-115">clientBaseAddress</span></span>|<span data-ttu-id="35a0a-116">Универсальный код ресурса (URI), который задает адрес обратного канала при работе в дуплексном режиме.</span><span class="sxs-lookup"><span data-stu-id="35a0a-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="35a0a-117">Служба использует данный адрес для осуществления контакта и создания подключения к клиенту.</span><span class="sxs-lookup"><span data-stu-id="35a0a-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="35a0a-118">Если этот атрибут не задан, создается адрес`full qualified name+default port\TemporaryIndigoAddress\guid`по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="35a0a-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="35a0a-119">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="35a0a-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35a0a-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="35a0a-120">Child Elements</span></span>  
 <span data-ttu-id="35a0a-121">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="35a0a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35a0a-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="35a0a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="35a0a-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="35a0a-123">Element</span></span>|<span data-ttu-id="35a0a-124">Описание</span><span class="sxs-lookup"><span data-stu-id="35a0a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35a0a-125">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="35a0a-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="35a0a-126">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="35a0a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35a0a-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="35a0a-127">Remarks</span></span>  
 <span data-ttu-id="35a0a-128">Данный элемент конфигурации используется с теми типами транспорта, которые не имеют встроенной поддержки дуплексной связи, например HTTP.</span><span class="sxs-lookup"><span data-stu-id="35a0a-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="35a0a-129">Напротив, протокол TCP имеет встроенную поддержку дуплексной связи, и для него не требуется использовать этот элемент привязки для службы при отправке сообщений обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="35a0a-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="35a0a-130">Для осуществления контакта и установления подключения клиент должен предоставить службе адрес.</span><span class="sxs-lookup"><span data-stu-id="35a0a-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="35a0a-131">Этот адрес клиента предоставляется атрибутом `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="35a0a-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="35a0a-132">Обратите внимание, что Windows Communication Foundation (WCF) автоматически создает атрибут ClientBaseAddress в том случае, если он не был явно задан пользователем.</span><span class="sxs-lookup"><span data-stu-id="35a0a-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35a0a-133">Пример</span><span class="sxs-lookup"><span data-stu-id="35a0a-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="35a0a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="35a0a-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="35a0a-135">Привязки</span><span class="sxs-lookup"><span data-stu-id="35a0a-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="35a0a-136">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="35a0a-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="35a0a-137">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="35a0a-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="35a0a-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35a0a-138">\<customBinding></span></span>](custombinding.md)
