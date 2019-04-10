---
title: Практическое руководство. Настройка службы Windows Communication Foundation на совместное использование портов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: bc0c822659ee57ac8dd87a2adddcd32e934ea4fb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302408"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="1d885-102">Практическое руководство. Настройка службы Windows Communication Foundation на совместное использование портов</span><span class="sxs-lookup"><span data-stu-id="1d885-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="1d885-103">— Это самый простой способ использования порта net.tcp:// в приложении Windows Communication Foundation (WCF) для предоставления службы с помощью <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="1d885-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="1d885-104">Эта привязка предоставляет свойство <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A>, которое определяет, включено ли совместное использование порта net.tcp:// для службы, настраиваемой с этой привязкой.</span><span class="sxs-lookup"><span data-stu-id="1d885-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="1d885-105">Следующая процедура показывает, как использовать класс <xref:System.ServiceModel.NetTcpBinding>, чтобы открыть конечную точку по универсальному коду ресурса (URI) net.tcp://localhost/MyService, сначала в коде, а затем с помощью элементов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1d885-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="1d885-106">Включение совместного использования порта net.tcp:// в привязке NetTcpBinding с помощью кода</span><span class="sxs-lookup"><span data-stu-id="1d885-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="1d885-107">Создать службу, реализующую контракт с именем `IMyService` и назовите его `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="1d885-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="1d885-108">Создайте экземпляр класса <xref:System.ServiceModel.NetTcpBinding> и задайте для свойства <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="1d885-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="1d885-109">Создайте <xref:System.ServiceModel.ServiceHost> и добавьте в него конечную точку службы для `MyService`, использующей привязку <xref:System.ServiceModel.NetTcpBinding>, поддерживающую совместное использование порта, и ожидающей передачи данных по универсальному коду ресурса (URI) адреса конечной точки "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="1d885-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1d885-110">В этом примере используется TCP-порт 808 по умолчанию, так как в универсальном коде ресурса (URI) адреса конечной точки не указан другой номер порта.</span><span class="sxs-lookup"><span data-stu-id="1d885-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="1d885-111">Так как в транспортной привязке явно включено совместное использование порта, эта служба может использовать порт 808 совместно с другими службами в других процессах.</span><span class="sxs-lookup"><span data-stu-id="1d885-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="1d885-112">Если бы совместное использование порта не было бы разрешено и порт 808 уже использовался бы другим приложением, то при открытии данной службы она бы создала исключение <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="1d885-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="1d885-113">Включение совместного использования порта net.tcp:// в привязке NetTcpBinding с помощью конфигурации</span><span class="sxs-lookup"><span data-stu-id="1d885-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="1d885-114">В следующем примере показано, как включить совместное использование порта и добавить конечную точку службы с помощью элементов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1d885-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d885-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1d885-115">See also</span></span>

- [<span data-ttu-id="1d885-116">Совместное использование портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1d885-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="1d885-117">Практическое руководство. Включение службы совместного использования портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1d885-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
