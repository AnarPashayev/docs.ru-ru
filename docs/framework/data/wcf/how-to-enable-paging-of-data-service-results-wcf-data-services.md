---
title: Практическое руководство. Включить разбиение на страницы результатов службы данных (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: edc150d118153849dd84eb40f1443d842c7d346d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517843"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="7e226-102">Практическое руководство. Включить разбиение на страницы результатов службы данных (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="7e226-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
<span data-ttu-id="7e226-103">Службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] позволяют ограничить количество сущностей, возвращаемых запросом службы данных.</span><span class="sxs-lookup"><span data-stu-id="7e226-103">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="7e226-104">Пределы разбиения на страницы определены в методе, который вызывается при инициализации службы, и могут устанавливаться отдельно для каждого набора сущностей.</span><span class="sxs-lookup"><span data-stu-id="7e226-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="7e226-105">Если включена подкачка страниц, то последняя запись в канале содержит ссылку на следующую страницу данных.</span><span class="sxs-lookup"><span data-stu-id="7e226-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="7e226-106">Дополнительные сведения см. в разделе [Настройка службы данных](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7e226-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="7e226-107">В этом разделе показывается, как изменить службу данных, чтобы включить разбиение на страницы возвращаемых `Customers` и наборов сущностей `Orders`.</span><span class="sxs-lookup"><span data-stu-id="7e226-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="7e226-108">В примере этого раздела используется образец службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="7e226-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="7e226-109">Эта служба создается после завершения [краткое руководство по службам данных WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7e226-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="7e226-110">Как включить разбиение на страницы возвращаемых клиентов и наборов сущностей Orders</span><span class="sxs-lookup"><span data-stu-id="7e226-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="7e226-111">В коде службы данных замените код местозаполнителя в функции `InitializeService` следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="7e226-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="7e226-112">См. также</span><span class="sxs-lookup"><span data-stu-id="7e226-112">See also</span></span>

- [<span data-ttu-id="7e226-113">Загрузка отложенного содержимого</span><span class="sxs-lookup"><span data-stu-id="7e226-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="7e226-114">Практическое руководство. Загрузка разбитых на страницы результатов</span><span class="sxs-lookup"><span data-stu-id="7e226-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
