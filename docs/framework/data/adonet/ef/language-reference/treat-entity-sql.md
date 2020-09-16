---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 566ac875aec17e4d0aa22ec1962053aeb6ae2a2e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558853"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="f4676-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f4676-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="f4676-103">Обрабатывает объект некоторого базового типа, как объект указанного производного типа.</span><span class="sxs-lookup"><span data-stu-id="f4676-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4676-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4676-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4676-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f4676-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f4676-106">Любое допустимое выражение запроса, возвращающее сущность.</span><span class="sxs-lookup"><span data-stu-id="f4676-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4676-107">Тип указанного выражения должен быть подтипом указанного типа данных, либо тип данных должен быть подтипом типа выражения.</span><span class="sxs-lookup"><span data-stu-id="f4676-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="f4676-108">Тип сущности.</span><span class="sxs-lookup"><span data-stu-id="f4676-108">An entity type.</span></span> <span data-ttu-id="f4676-109">Для типа должно быть указано пространство имен.</span><span class="sxs-lookup"><span data-stu-id="f4676-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4676-110">Указанное выражение должно быть подтипом указанного типа данных, либо тип данных должен быть подтипом данного выражения.</span><span class="sxs-lookup"><span data-stu-id="f4676-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4676-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f4676-111">Return Value</span></span>  
 <span data-ttu-id="f4676-112">Значение указанного типа данных.</span><span class="sxs-lookup"><span data-stu-id="f4676-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4676-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="f4676-113">Remarks</span></span>  
 <span data-ttu-id="f4676-114">Оператор TREAT предназначен для приведения связанных классов к базовому типу.</span><span class="sxs-lookup"><span data-stu-id="f4676-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="f4676-115">Например, если тип `Employee` является производным от типа `Person` , а «p» относится к типу `Person`, то выражение `TREAT(p AS NamespaceName.Employee)` приводит общий экземпляр типа `Person` к типу `Employee`. Иными словами, он позволяет обрабатывать «p» как тип `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f4676-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="f4676-116">Оператор TREAT используется в сценариях наследования, в которых можно выполнить запрос наподобие следующего.</span><span class="sxs-lookup"><span data-stu-id="f4676-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="f4676-117">Этот запрос приводит сущности `Person` к типу `Employee` .</span><span class="sxs-lookup"><span data-stu-id="f4676-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="f4676-118">Если значение «p» фактически не относится к типу `Employee`, то выражение имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="f4676-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4676-119">Указанное выражение `Employee` должно быть подтипом указанного типа данных `Person` , либо тип данных должен быть подтипом выражения.</span><span class="sxs-lookup"><span data-stu-id="f4676-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="f4676-120">В противном случае это выражение вызовет ошибку во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="f4676-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="f4676-121">Следующая таблица показывает, каким образом оператор TREAT работает с некоторыми стандартными и не очень часто используемыми конструкциями.</span><span class="sxs-lookup"><span data-stu-id="f4676-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="f4676-122">Все исключения формируются на стороне клиента перед вызовом поставщика.</span><span class="sxs-lookup"><span data-stu-id="f4676-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="f4676-123">Шаблон</span><span class="sxs-lookup"><span data-stu-id="f4676-123">Pattern</span></span>|<span data-ttu-id="f4676-124">Поведение</span><span class="sxs-lookup"><span data-stu-id="f4676-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="f4676-125">Возвращает `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="f4676-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="f4676-126">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="f4676-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="f4676-127">Создает исключение/</span><span class="sxs-lookup"><span data-stu-id="f4676-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="f4676-128">Возвращает значение `EntityType` или `null`.</span><span class="sxs-lookup"><span data-stu-id="f4676-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="f4676-129">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="f4676-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="f4676-130">Создает исключение.</span><span class="sxs-lookup"><span data-stu-id="f4676-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4676-131">Пример</span><span class="sxs-lookup"><span data-stu-id="f4676-131">Example</span></span>  
 <span data-ttu-id="f4676-132">В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор TREAT используется для преобразования объекта типа Course в коллекцию объектов типа OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="f4676-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="f4676-133">Запрос основан на [модели School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4676-133">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="f4676-134">См. также</span><span class="sxs-lookup"><span data-stu-id="f4676-134">See also</span></span>

- [<span data-ttu-id="f4676-135">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4676-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f4676-136">Допускающие значения NULL структурированные типы</span><span class="sxs-lookup"><span data-stu-id="f4676-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
