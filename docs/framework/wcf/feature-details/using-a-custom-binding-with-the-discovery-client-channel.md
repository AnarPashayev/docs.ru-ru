---
title: Использование пользовательской привязки для клиентского канала обнаружения
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 49983c3ab303d3839350af72b1aa4821c071fe99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595041"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="b944a-102">Использование пользовательской привязки для клиентского канала обнаружения</span><span class="sxs-lookup"><span data-stu-id="b944a-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="b944a-103">При использовании пользовательской привязки к <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> необходимо определить поставщик <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, который будет создавать экземпляры <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="b944a-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="b944a-104">Создание DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="b944a-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="b944a-105">Объект <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> отвечает за создание <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> экземпляров по запросу.</span><span class="sxs-lookup"><span data-stu-id="b944a-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="b944a-106">Чтобы определить поставщика конечной точки обнаружения, создайте класс из <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, переопределив метод <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A>, а затем вернув новую конечную точку обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b944a-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="b944a-107">В следующем примере показан процесс создания поставщика конечной точки обнаружения.</span><span class="sxs-lookup"><span data-stu-id="b944a-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 <span data-ttu-id="b944a-108">После того как поставщик конечной точки обнаружения определен, можно создать пользовательскую привязку и добавить <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, который содержит ссылки на поставщик конечной точки обнаружения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b944a-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 <span data-ttu-id="b944a-109">Дополнительные сведения об использовании канала клиента обнаружения см. в разделе [Использование клиентского канала обнаружения](using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="b944a-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b944a-110">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="b944a-110">See also</span></span>

- [<span data-ttu-id="b944a-111">Общие сведения об обнаружении WCF</span><span class="sxs-lookup"><span data-stu-id="b944a-111">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="b944a-112">Использование клиентского канала обнаружения</span><span class="sxs-lookup"><span data-stu-id="b944a-112">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
