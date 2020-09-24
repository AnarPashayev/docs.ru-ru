---
title: Практическое руководство. Создание службы данных с использованием поставщика отражений (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 6bab9d9be484cf90cb85df63a1b237b5cc39a5e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152771"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="8618b-102">Практическое руководство. Создание службы данных с использованием поставщика отражений (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="8618b-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>

<span data-ttu-id="8618b-103">WCF Data Services позволяет определить модель данных, основанную на произвольных классах, если эти классы предоставляются как объекты, реализующие <xref:System.Linq.IQueryable%601> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="8618b-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="8618b-104">Дополнительные сведения см. в разделе [поставщики служб данных](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8618b-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8618b-105">Пример</span><span class="sxs-lookup"><span data-stu-id="8618b-105">Example</span></span>  

 <span data-ttu-id="8618b-106">Следующий пример определяет модель данных, включающую сущности `Orders` и `Items`.</span><span class="sxs-lookup"><span data-stu-id="8618b-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="8618b-107">Класс контейнера сущностей `OrderItemData` имеет два публичных метода, которые возвращают интерфейсы <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="8618b-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="8618b-108">Эти интерфейсы являются наборами сущностей типа `Orders` и типами сущностей `Items`.</span><span class="sxs-lookup"><span data-stu-id="8618b-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="8618b-109">Сущность `Order` может включать несколько сущностей `Items`, поэтому тип сущности `Orders` имеет свойство навигации `Items`, возвращающее коллекцию объектов `Items`.</span><span class="sxs-lookup"><span data-stu-id="8618b-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="8618b-110">Класс контейнера сущностей `OrderItemData` является универсальным типом класса <xref:System.Data.Services.DataService%601>, производным которого является класс `OrderItems` службы данных.</span><span class="sxs-lookup"><span data-stu-id="8618b-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8618b-111">Поскольку пример демонстрирует поставщика данных в памяти и изменения не сохраняются за пределами текущих экземпляров объектов, реализация интерфейса <xref:System.Data.Services.IUpdatable> не приносит никаких выгод.</span><span class="sxs-lookup"><span data-stu-id="8618b-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="8618b-112">Пример, в котором реализуется <xref:System.Data.Services.IUpdatable> интерфейс, см. [в разделе инструкции. Создание службы данных с помощью LINQ to SQL источника данных](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8618b-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="8618b-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8618b-113">See also</span></span>

- [<span data-ttu-id="8618b-114">Практическое руководство. Создание службы данных с использованием источника данных LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8618b-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="8618b-115">Поставщики служб данных</span><span class="sxs-lookup"><span data-stu-id="8618b-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="8618b-116">Практическое руководство. Создание службы данных с использованием источника данных Entity Framework ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8618b-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
