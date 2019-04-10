---
title: Практическое руководство. Импорт метаданных в конечные точки службы
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: afee3f2236db99b14c0e840d987e4862a260568e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318290"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="42ba6-102">Практическое руководство. Импорт метаданных в конечные точки службы</span><span class="sxs-lookup"><span data-stu-id="42ba6-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="42ba6-103">В этом разделе объясняется, как импортировать метаданные в коллекцию конечных точек службы и использовать службы, определенные в [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="42ba6-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="42ba6-104">Кроме того, в этом разделе демонстрируется создание клиентского приложения, импортирующего метаданные из службы, а затем вызывающего в службе метод `Add`.</span><span class="sxs-lookup"><span data-stu-id="42ba6-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="42ba6-105">Импорт метаданных в конечные точки службы</span><span class="sxs-lookup"><span data-stu-id="42ba6-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="42ba6-106">Объявите объект <xref:System.ServiceModel.EndpointAddress> и инициализируйте его с помощью универсального кода ресурса (URI) для адреса обмена метаданными (MEX) этой службы.</span><span class="sxs-lookup"><span data-stu-id="42ba6-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="42ba6-107">Создайте клиент <xref:System.ServiceModel.Description.MetadataExchangeClient>, передающий адрес MEX, и вызовите метод <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="42ba6-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="42ba6-108">Это позволяет извлечь метаданные из службы.</span><span class="sxs-lookup"><span data-stu-id="42ba6-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="42ba6-109">Создайте устройство импорта <xref:System.ServiceModel.Description.WsdlImporter>, передающее ранее извлеченные метаданные, и вызовите метод <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="42ba6-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="42ba6-110">Эти действия позволяют создать коллекцию объектов <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="42ba6-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="42ba6-111">В зависимости от потребностей также можно было вызвать метод <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> или <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A></span><span class="sxs-lookup"><span data-stu-id="42ba6-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="42ba6-112">После импорта метаданных невозможно будет создать клиентский канал или экспортировать метаданные.</span><span class="sxs-lookup"><span data-stu-id="42ba6-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="42ba6-113">Это объясняется тем, что на данном этапе не имеется никакой информации о типе.</span><span class="sxs-lookup"><span data-stu-id="42ba6-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="42ba6-114">Информация о типе требуется для фактического взаимодействия со службой или экспорта метаданных.</span><span class="sxs-lookup"><span data-stu-id="42ba6-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="42ba6-115">Для создания сведений о типе необходимо создать код, показанный в шагах 4 и 5.</span><span class="sxs-lookup"><span data-stu-id="42ba6-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="42ba6-116">Кроме того, можно использовать вспомогательный класс <xref:System.ServiceModel.Description.MetadataResolver>.</span><span class="sxs-lookup"><span data-stu-id="42ba6-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="42ba6-117">Дополнительные сведения см. в разделе [Как Использование MetadataResolver для динамического получения метаданных привязки](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="42ba6-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="42ba6-118">Создайте информацию о типе для каждого контракта.</span><span class="sxs-lookup"><span data-stu-id="42ba6-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="42ba6-119">Теперь этой информацией можно пользоваться.</span><span class="sxs-lookup"><span data-stu-id="42ba6-119">Now you can use this information.</span></span> <span data-ttu-id="42ba6-120">В следующем примере кода создается исходный код C#.</span><span class="sxs-lookup"><span data-stu-id="42ba6-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="42ba6-121">См. также</span><span class="sxs-lookup"><span data-stu-id="42ba6-121">See also</span></span>

- [<span data-ttu-id="42ba6-122">Метаданные</span><span class="sxs-lookup"><span data-stu-id="42ba6-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="42ba6-123">Начало работы</span><span class="sxs-lookup"><span data-stu-id="42ba6-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
