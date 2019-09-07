---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8247dd62f4dda853487fe52f00f8f548b627c075
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399399"
---
# <a name="transactionflow"></a><span data-ttu-id="1f1f4-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="1f1f4-101">\<transactionFlow></span></span>
<span data-ttu-id="1f1f4-102">Задает поддержку потока транзакций для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="1f1f4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f1f4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f1f4-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f1f4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f1f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<привязки >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1f1f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1f1f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="1f1f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="1f1f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Привязка >** </span><span class="sxs-lookup"><span data-stu-id="1f1f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1f1f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="1f1f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1f4-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f1f4-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f1f4-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1f1f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1f1f4-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f1f4-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f1f4-112">Attributes</span></span>  
  
|<span data-ttu-id="1f1f4-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1f1f4-113">Attribute</span></span>|<span data-ttu-id="1f1f4-114">Описание</span><span class="sxs-lookup"><span data-stu-id="1f1f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f1f4-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="1f1f4-115">transactionProtocol</span></span>|<span data-ttu-id="1f1f4-116">Задает используемый протокол транзакций.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="1f1f4-117">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="1f1f4-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f1f4-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1f1f4-118">-   OleTransactions</span></span><br /><span data-ttu-id="1f1f4-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1f1f4-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1f1f4-120">Значение по умолчанию - OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="1f1f4-121">Это атрибут типа <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f1f4-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1f1f4-122">Child Elements</span></span>  
 <span data-ttu-id="1f1f4-123">Нет.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f1f4-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1f1f4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1f1f4-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f1f4-125">Element</span></span>|<span data-ttu-id="1f1f4-126">Описание</span><span class="sxs-lookup"><span data-stu-id="1f1f4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f1f4-127">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="1f1f4-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1f1f4-128">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f1f4-129">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f1f4-129">Remarks</span></span>  
 <span data-ttu-id="1f1f4-130">Этот элемент позволяет включить или отключить входящий поток транзакций в параметрах привязки конечной точки, а также задать необходимый формат протокола для входящих транзакций.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="1f1f4-131">Дополнительные сведения об использовании этого элемента конфигурации см. в разделе [Конфигурация транзакций ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) и [Включение потока транзакций](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="1f1f4-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1f1f4-132">При использовании протокола `OleTransactions` для реализации потока транзакций от одной конечной точки к другой время ожидания транзакции может быть потеряно, если целевая конечная точка попытается запустить поток снова, используя любой протокол, отличный от `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="1f1f4-133">Это может привести к тому, что время ожидания для всех узлов, находящихся ниже перехода OleTransactions, окажется больше, чем ожидалось.</span><span class="sxs-lookup"><span data-stu-id="1f1f4-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1f4-134">См. также</span><span class="sxs-lookup"><span data-stu-id="1f1f4-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1f1f4-135">Конфигурация транзакции ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f1f4-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="1f1f4-136">Включение потока транзакций</span><span class="sxs-lookup"><span data-stu-id="1f1f4-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="1f1f4-137">Привязки</span><span class="sxs-lookup"><span data-stu-id="1f1f4-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f1f4-138">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="1f1f4-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1f1f4-139">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="1f1f4-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1f1f4-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1f1f4-140">\<customBinding></span></span>](custombinding.md)
