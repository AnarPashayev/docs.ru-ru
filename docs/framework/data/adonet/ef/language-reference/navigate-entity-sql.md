---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249941"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="74d3a-102">NAVIGATE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="74d3a-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="74d3a-103">Производит переход по связи, установленной между сущностями.</span><span class="sxs-lookup"><span data-stu-id="74d3a-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="74d3a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74d3a-104">Syntax</span></span>

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="74d3a-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="74d3a-105">Arguments</span></span>

<span data-ttu-id="74d3a-106">`instance-expression`Экземпляр сущности.</span><span class="sxs-lookup"><span data-stu-id="74d3a-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="74d3a-107">`relationship-type`Имя типа связи из CSDL-файла языка определения схемы.</span><span class="sxs-lookup"><span data-stu-id="74d3a-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="74d3a-108">Является полным именем \<> пространства имен.\< `relationship-type` имя типа отношения >.</span><span class="sxs-lookup"><span data-stu-id="74d3a-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="74d3a-109">`to`Конец связи.</span><span class="sxs-lookup"><span data-stu-id="74d3a-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="74d3a-110">`from`Начало связи.</span><span class="sxs-lookup"><span data-stu-id="74d3a-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="74d3a-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="74d3a-111">Return Value</span></span>

<span data-ttu-id="74d3a-112">Если количество элементов в конечной составляющей связи равно 1, то будет возвращено значение `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="74d3a-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="74d3a-113">Если же количество элементов в конечной составляющей связи равно n, то будет возвращено значение `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="74d3a-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="74d3a-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="74d3a-114">Remarks</span></span>

<span data-ttu-id="74d3a-115">Связи — это конструкции первого класса в EDM (EDM).</span><span class="sxs-lookup"><span data-stu-id="74d3a-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="74d3a-116">Связи могут устанавливаться между двумя или несколькими типами сущностей, а пользователи могут переходить по связи от одного элемента (от одной сущности) к другому.</span><span class="sxs-lookup"><span data-stu-id="74d3a-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="74d3a-117">`from` и `to` являются необязательными при том условии, что нет неоднозначности в разрешении имен в пределах связи.</span><span class="sxs-lookup"><span data-stu-id="74d3a-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="74d3a-118">Оператор NAVIGATE является допустимым в пространствах O и C.</span><span class="sxs-lookup"><span data-stu-id="74d3a-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="74d3a-119">Конструкция перехода имеет следующую общую форму.</span><span class="sxs-lookup"><span data-stu-id="74d3a-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="74d3a-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span><span class="sxs-lookup"><span data-stu-id="74d3a-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="74d3a-121">Например:</span><span class="sxs-lookup"><span data-stu-id="74d3a-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="74d3a-122">Здесь OrderCustomer является значением параметра `relationship`, а Customer и Order являются элементами связи `to-end` (customer) и `from-end` (order).</span><span class="sxs-lookup"><span data-stu-id="74d3a-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="74d3a-123">Если ордеркустомер является отношением n:1, то тип результата выражения Navigate является ссылочным\<> клиента.</span><span class="sxs-lookup"><span data-stu-id="74d3a-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="74d3a-124">Для этого выражение существует следующая упрощенная форма.</span><span class="sxs-lookup"><span data-stu-id="74d3a-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="74d3a-125">Аналогично, в запросе следующей формы выражение Navigate выдает коллекцию < порядок ссылок\<> >.</span><span class="sxs-lookup"><span data-stu-id="74d3a-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="74d3a-126">Выражение экземпляра должно иметь тип сущности или ссылки.</span><span class="sxs-lookup"><span data-stu-id="74d3a-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="74d3a-127">Пример</span><span class="sxs-lookup"><span data-stu-id="74d3a-127">Example</span></span>

<span data-ttu-id="74d3a-128">В следующем запросе Entity SQL оператор NAVIGATE используется для перехода по связи, заданной между типами сущностей Address и SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="74d3a-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="74d3a-129">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="74d3a-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="74d3a-130">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="74d3a-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="74d3a-131">Выполните процедуру, описанную в [разделе инструкции. Выполнение запроса, возвращающего Структуралтипе](../how-to-execute-a-query-that-returns-structuraltype-results.md)результаты.</span><span class="sxs-lookup"><span data-stu-id="74d3a-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="74d3a-132">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="74d3a-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a><span data-ttu-id="74d3a-133">См. также</span><span class="sxs-lookup"><span data-stu-id="74d3a-133">See also</span></span>

- [<span data-ttu-id="74d3a-134">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74d3a-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="74d3a-135">Практическое руководство. Навигация по связям с помощью оператора Navigate</span><span class="sxs-lookup"><span data-stu-id="74d3a-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
