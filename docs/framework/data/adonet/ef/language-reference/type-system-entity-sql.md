---
title: Система типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0f7dae9e57132929737d752c67694cd369b79d9e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319241"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="ec2a9-102">Система типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ec2a9-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ec2a9-103">поддерживает несколько типов:</span><span class="sxs-lookup"><span data-stu-id="ec2a9-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="ec2a9-104">Типы-примитивы (простые типы), такие как `Int32` и `String.`</span><span class="sxs-lookup"><span data-stu-id="ec2a9-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="ec2a9-105">Номинальные типы, которые определяются в схеме, например <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> и <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="ec2a9-106">Анонимные типы, которые явно не определяются в схеме: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> и <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="ec2a9-107">В этом разделе обсуждаются анонимные типы, которые не определены в схеме явным образом, но поддерживаются Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="ec2a9-108">Сведения о примитивных и номинальных типах см. в разделе [типы концептуальной модели (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="ec2a9-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="ec2a9-109">Строки</span><span class="sxs-lookup"><span data-stu-id="ec2a9-109">Rows</span></span>  
 <span data-ttu-id="ec2a9-110">Структура строки зависит от последовательности типизированных и именованных элементов, из которых состоит строка.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="ec2a9-111">Тип строки не имеет идентификатора и не может наследоваться.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="ec2a9-112">Экземпляры строк одинакового типа считаются равными, если равны соответствующие элементы этих строк.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="ec2a9-113">Со строками не связаны операции, отличные от проверки равнозначности их структуры, к тому же они не имеют эквивалентов в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="ec2a9-114">Запросы могут возвращать структуры, содержащие строки или коллекции строк.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="ec2a9-115">API определения привязки между запросами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] и базовым языком определяет способ реализации строк в запросе, вырабатывающем этот результат.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="ec2a9-116">Сведения о создании экземпляра строки см. в разделе [Построение типов](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ec2a9-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="ec2a9-117">Коллекции</span><span class="sxs-lookup"><span data-stu-id="ec2a9-117">Collections</span></span>  
 <span data-ttu-id="ec2a9-118">Типы коллекций представляют ноль и более экземпляров других объектов.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="ec2a9-119">Сведения о создании коллекции см. в разделе [Построение типов](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ec2a9-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="ec2a9-120">Ссылки</span><span class="sxs-lookup"><span data-stu-id="ec2a9-120">References</span></span>  
 <span data-ttu-id="ec2a9-121">Ссылка - это логический указатель на отдельную сущность в определенном наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 <span data-ttu-id="ec2a9-122">Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает следующие операторы для конструирования, деконструирования и перехода по ссылкам.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-122">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="ec2a9-123">REF</span><span class="sxs-lookup"><span data-stu-id="ec2a9-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="ec2a9-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ec2a9-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="ec2a9-125">KEY</span><span class="sxs-lookup"><span data-stu-id="ec2a9-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="ec2a9-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="ec2a9-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="ec2a9-127">По ссылке можно переходить с помощью оператора доступа к элементам «точка» (`.`).</span><span class="sxs-lookup"><span data-stu-id="ec2a9-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="ec2a9-128">В следующем фрагменте извлекается свойство Id (объекта Order) путем перехода по свойству r (сокращение от reference).</span><span class="sxs-lookup"><span data-stu-id="ec2a9-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="ec2a9-129">Если ссылка имеет значение NULL или цель ссылки не существует, результатом становится NULL.</span><span class="sxs-lookup"><span data-stu-id="ec2a9-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2a9-130">См. также</span><span class="sxs-lookup"><span data-stu-id="ec2a9-130">See also</span></span>

- [<span data-ttu-id="ec2a9-131">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ec2a9-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ec2a9-132">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ec2a9-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ec2a9-133">CAST</span><span class="sxs-lookup"><span data-stu-id="ec2a9-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="ec2a9-134">Спецификации CSDL, SSDL и MSL</span><span class="sxs-lookup"><span data-stu-id="ec2a9-134">CSDL, SSDL, and MSL Specifications</span></span>](csdl-ssdl-and-msl-specifications.md)
