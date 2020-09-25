---
title: набор сущностей
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 6286d3707a8506e7a389359a5aa361c152e75212
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194796"
---
# <a name="entity-set"></a><span data-ttu-id="7522a-102">набор сущностей</span><span class="sxs-lookup"><span data-stu-id="7522a-102">entity set</span></span>

<span data-ttu-id="7522a-103">*Набор сущностей* — это логический контейнер для экземпляров [типа сущности](entity-type.md) и экземпляров любого типа, производного от этого типа сущности.</span><span class="sxs-lookup"><span data-stu-id="7522a-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="7522a-104">(Дополнительные сведения о производных типах см. в разделе [EDM: наследование](entity-data-model-inheritance.md).) Связь между типом сущности и набором сущностей аналогична связи между строкой и таблицей в реляционной базе данных: как строка, тип сущности Описывает структуру данных, и, как и таблица, набор сущностей содержит экземпляры данной структуры.</span><span class="sxs-lookup"><span data-stu-id="7522a-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="7522a-105">Набор сущностей не является конструктом моделирования данных; он не описывает структуру данных.</span><span class="sxs-lookup"><span data-stu-id="7522a-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="7522a-106">Вместо этого набор сущностей обеспечивает конструкт для среды размещения или хранения (например, для среды CLR или базы данных сервера SQL), позволяя группировать экземпляры типа сущности так, чтобы они были сопоставлены хранилищу данных.</span><span class="sxs-lookup"><span data-stu-id="7522a-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="7522a-107">Набор сущностей определяется в [контейнере сущностей](entity-container.md), который является логической группировкой наборов сущностей и [наборов ассоциаций](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="7522a-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="7522a-108">Чтобы экземпляр типа сущности существовал в наборе сущности, должны быть выполнены следующие условия.</span><span class="sxs-lookup"><span data-stu-id="7522a-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="7522a-109">Тип экземпляра является либо тем же, что и тип сущности, в котором находится набор сущностей, либо подтипом типа сущности.</span><span class="sxs-lookup"><span data-stu-id="7522a-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="7522a-110">[Ключ сущности](entity-key.md) для экземпляра уникален в пределах набора сущностей.</span><span class="sxs-lookup"><span data-stu-id="7522a-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="7522a-111">Экземпляр не существует ни в каком другом наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="7522a-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7522a-112">Несколько наборов сущностей могут быть определены при помощи одного и того же типа сущности, однако экземпляр одного типа сущности может существовать только в одном наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="7522a-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="7522a-113">Нет необходимости определять набор сущностей для каждого типа сущности в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="7522a-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7522a-114">Пример</span><span class="sxs-lookup"><span data-stu-id="7522a-114">Example</span></span>  

 <span data-ttu-id="7522a-115">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="7522a-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="7522a-117">На следующей схеме показаны два набора сущностей (`Books` и `Publishers`) и набор ассоциаций (`PublishedBy`), основанный на приведенной выше концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="7522a-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="7522a-118">Бизнес-аналитика в `Books` наборе сущностей представляет экземпляр `Book` типа сущности во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="7522a-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="7522a-119">Аналогичным образом PJ представляет `Publisher` экземпляр в `Publishers` наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="7522a-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="7522a-120">Бипж представляет экземпляр `PublishedBy` ассоциации в `PublishedBy` наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="7522a-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Снимок экрана, на котором показан пример набора.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="7522a-122">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="7522a-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7522a-123">Далее язык CSDL определяет контейнер сущностей с одним набором сущностей для каждого типа сущностей в приведенной выше концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="7522a-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="7522a-124">Обратите внимание, что имя и тип сущности для каждого набора сущностей определены при помощи атрибутов XML.</span><span class="sxs-lookup"><span data-stu-id="7522a-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="7522a-125">Предусмотрена возможность определять несколько наборов сущностей на тип (модель MEST).</span><span class="sxs-lookup"><span data-stu-id="7522a-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="7522a-126">Далее язык CSDL определяет контейнер сущностей с двумя наборами сущностей для типа сущности `Book`.</span><span class="sxs-lookup"><span data-stu-id="7522a-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7522a-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7522a-127">See also</span></span>

- [<span data-ttu-id="7522a-128">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="7522a-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7522a-129">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="7522a-129">Entity Data Model</span></span>](entity-data-model.md)
