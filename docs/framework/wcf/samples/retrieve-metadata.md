---
title: Извлечение метаданных
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: f35bb14b9338197828189a1d91d5653fd1680b86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208687"
---
# <a name="retrieve-metadata"></a><span data-ttu-id="51a3a-102">Извлечение метаданных</span><span class="sxs-lookup"><span data-stu-id="51a3a-102">Retrieve Metadata</span></span>
<span data-ttu-id="51a3a-103">В этом образце показана реализация клиента, динамически извлекающего метаданные из службы для выбора конечной точки для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="51a3a-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="51a3a-104">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="51a3a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="51a3a-105">Служба была изменена предоставляет две конечные точки — конечную точку по базовому адресу с использованием `basicHttpBinding` привязки и защищенную конечную точку в {*baseaddress*} / secure с использованием `wsHttpBinding` привязки.</span><span class="sxs-lookup"><span data-stu-id="51a3a-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="51a3a-106">Вместо выполнения настройки адресов и привязок конечных точек клиента, клиент динамически извлекает метаданные для службы с помощью класса <xref:System.ServiceModel.Description.MetadataExchangeClient>, а затем импортирует эти метаданные в виде <xref:System.ServiceModel.Description.ServiceEndpointCollection>, используя класс <xref:System.ServiceModel.Description.WsdlImporter>.</span><span class="sxs-lookup"><span data-stu-id="51a3a-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51a3a-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="51a3a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="51a3a-108">Клиентское приложение использует импортированную <xref:System.ServiceModel.Description.ServiceEndpointCollection>, чтобы создать клиенты для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="51a3a-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="51a3a-109">Клиентское приложение выполняет итерацию в каждой извлеченной конечной точке и взаимодействует с каждой конечной точкой, реализующей контракт `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="51a3a-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="51a3a-110">Соответствующим адресу и привязке предоставляется извлеченная конечная точка; таким образом выполняется настройка взаимодействия клиента с каждой конечной точкой, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="51a3a-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 <span data-ttu-id="51a3a-111">В окне консольного приложения клиента отображаются операции, передаваемые в каждую из конечных точек, с указанием пути адреса и именем привязки.</span><span class="sxs-lookup"><span data-stu-id="51a3a-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51a3a-112">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="51a3a-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="51a3a-113">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a3a-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="51a3a-114">Чтобы создать выпуск решения на C#, C++ или Visual Basic .NET, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a3a-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="51a3a-115">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a3a-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51a3a-116">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="51a3a-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51a3a-117">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="51a3a-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="51a3a-118">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="51a3a-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51a3a-119">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="51a3a-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
