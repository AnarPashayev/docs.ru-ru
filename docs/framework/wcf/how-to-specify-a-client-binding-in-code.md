---
title: Практическое руководство. Задание привязки клиента в коде
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303444"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="c80a7-102">Практическое руководство. Задание привязки клиента в коде</span><span class="sxs-lookup"><span data-stu-id="c80a7-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="c80a7-103">В этом примере создается клиент, предназначенный для использования службы калькулятора, и привязка этого клиента задается императивно в коде.</span><span class="sxs-lookup"><span data-stu-id="c80a7-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="c80a7-104">Клиент обращается к службе `CalculatorService`, которая реализует интерфейс `ICalculator`; как служба, так и клиент используют класс <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="c80a7-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="c80a7-105">В приведенной процедуре предполагается, что служба калькулятора выполняется.</span><span class="sxs-lookup"><span data-stu-id="c80a7-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="c80a7-106">Сведения о создании службы, см. в разделе [как: Указание привязки службы в конфигурации](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c80a7-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="c80a7-107">Он также использует [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) предоставляет для автоматического создания компонентов клиента.</span><span class="sxs-lookup"><span data-stu-id="c80a7-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="c80a7-108">Этот инструмент создает код клиента для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="c80a7-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="c80a7-109">Клиент создается в два этапа.</span><span class="sxs-lookup"><span data-stu-id="c80a7-109">The client is built in two parts.</span></span> <span data-ttu-id="c80a7-110">Программа Svcutil.exe генерирует класс `ClientCalculator`, реализующий интерфейс `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="c80a7-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="c80a7-111">Затем данное клиентское приложение создается путем создания экземпляра класса `ClientCalculator` и задания привязки и адреса для службы в коде.</span><span class="sxs-lookup"><span data-stu-id="c80a7-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="c80a7-112">Копию исходного кода в этом примере, см. в разделе [basicbinding обеспечением](../../../docs/framework/wcf/samples/basicbinding.md) образца.</span><span class="sxs-lookup"><span data-stu-id="c80a7-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="c80a7-113">Задание пользовательской привязки в коде</span><span class="sxs-lookup"><span data-stu-id="c80a7-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="c80a7-114">Из командной строки запустите программу Svcutil.exe, чтобы создать код из метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="c80a7-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="c80a7-115">Создаваемый клиент содержит интерфейс `ICalculator`, определяющий контракт службы, которому должна удовлетворять реализация клиента.</span><span class="sxs-lookup"><span data-stu-id="c80a7-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="c80a7-116">Создаваемый клиент также содержит реализацию класса `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="c80a7-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="c80a7-117">Создайте экземпляр класса `ClientCalculator`, использующего класс <xref:System.ServiceModel.BasicHttpBinding> в клиентском приложении, и вызовите операции службы по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="c80a7-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="c80a7-118">Скомпилируйте и запустите клиент.</span><span class="sxs-lookup"><span data-stu-id="c80a7-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80a7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c80a7-119">See also</span></span>

- [<span data-ttu-id="c80a7-120">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="c80a7-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
