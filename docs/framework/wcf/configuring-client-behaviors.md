---
title: Настройка поведений клиентов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193659"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="82845-102">Настройка поведений клиентов</span><span class="sxs-lookup"><span data-stu-id="82845-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="82845-103">Windows Communication Foundation (WCF) настраивает поведение двумя способами: путем ссылки на конфигурации поведения, которые определены в `<behavior>` разделе в файле конфигурации клиентского приложения — либо программным способом в вызывающем объекте приложение.</span><span class="sxs-lookup"><span data-stu-id="82845-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="82845-104">В этом разделе описываются оба подхода.</span><span class="sxs-lookup"><span data-stu-id="82845-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="82845-105">При использовании файла конфигурации конфигурация поведения представляет собой именованную коллекцию параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="82845-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="82845-106">Имя каждой из конфигураций поведения должно быть уникальным.</span><span class="sxs-lookup"><span data-stu-id="82845-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="82845-107">Эта строка используется в атрибуте `behaviorConfiguration` конфигурации конечной точки, чтобы связать конечную точку с поведением.</span><span class="sxs-lookup"><span data-stu-id="82845-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82845-108">Пример</span><span class="sxs-lookup"><span data-stu-id="82845-108">Example</span></span>  
 <span data-ttu-id="82845-109">В следующем фрагменте кода конфигурации определяется поведение с именем `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="82845-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="82845-110">Конечная точка клиента ссылается на это поведение в атрибуте `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="82845-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="82845-111">Управление поведениями программным образом</span><span class="sxs-lookup"><span data-stu-id="82845-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="82845-112">Можно также настраивать или вставлять поведения программным образом путем поиска соответствующего `Behaviors` свойства на объекте клиента Windows Communication Foundation (WCF) или на объекте фабрики каналов клиента перед открытием клиента.</span><span class="sxs-lookup"><span data-stu-id="82845-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82845-113">Пример</span><span class="sxs-lookup"><span data-stu-id="82845-113">Example</span></span>  
 <span data-ttu-id="82845-114">В следующем примере кода показано, как программным образом вставить поведение, обратившись к свойству <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> объекта <xref:System.ServiceModel.Description.ServiceEndpoint>, возвращаемого свойством <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> до создания объекта канала.</span><span class="sxs-lookup"><span data-stu-id="82845-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="82845-115">См. также</span><span class="sxs-lookup"><span data-stu-id="82845-115">See also</span></span>

- [<span data-ttu-id="82845-116">\<варианты поведения ></span><span class="sxs-lookup"><span data-stu-id="82845-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
