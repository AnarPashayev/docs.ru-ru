---
title: Практическое руководство. Включение разбиения по страницам результатов службы данных (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780050"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Практическое руководство. Включение разбиения по страницам результатов службы данных (WCF Data Services)
Службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] позволяют ограничить количество сущностей, возвращаемых запросом службы данных. Пределы разбиения на страницы определены в методе, который вызывается при инициализации службы, и могут устанавливаться отдельно для каждого набора сущностей.  
  
 Если включена подкачка страниц, то последняя запись в канале содержит ссылку на следующую страницу данных. Дополнительные сведения см. [в разделе Настройка службы данных](configuring-the-data-service-wcf-data-services.md).  
  
 В этом разделе показывается, как изменить службу данных, чтобы включить разбиение на страницы возвращаемых `Customers` и наборов сущностей `Orders`. В примере этого раздела используется образец службы данных Northwind. Эта служба создается при завершении [краткого руководства по WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Как включить разбиение на страницы возвращаемых клиентов и наборов сущностей Orders  
  
- В коде службы данных замените код местозаполнителя в функции `InitializeService` следующим текстом:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>См. также

- [Загрузка отложенного содержимого](loading-deferred-content-wcf-data-services.md)
- [Практическое руководство. Загрузить результаты, выгруженные по страницам](how-to-load-paged-results-wcf-data-services.md)
