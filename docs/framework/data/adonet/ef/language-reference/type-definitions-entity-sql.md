---
title: Определения типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096027"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="75901-102">Определения типов (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="75901-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="75901-103">Определение типа используется в операторе объявления встраиваемой функции [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75901-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75901-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="75901-104">Remarks</span></span>  
 <span data-ttu-id="75901-105">Оператор объявления для встроенной функции состоит из [ФУНКЦИЯ](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) ключевое слово и идентификатор, представляющий имя функции (например, «MyAvg»), следуют список определений параметров в скобки (для Пример, «dues Collection(Decimal)»).</span><span class="sxs-lookup"><span data-stu-id="75901-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="75901-106">Список определений параметров содержит ноль или более определений параметров.</span><span class="sxs-lookup"><span data-stu-id="75901-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="75901-107">Каждое определение параметра состоит из идентификатора (имя параметра для функции, например «dues»), за которым следует определение типа (например, «Collection(Decimal)»).</span><span class="sxs-lookup"><span data-stu-id="75901-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="75901-108">Определения типов могут представлять:</span><span class="sxs-lookup"><span data-stu-id="75901-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="75901-109">Тип идентификатора (например, «Int32» или «AdventureWorks.Order»).</span><span class="sxs-lookup"><span data-stu-id="75901-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="75901-110">Ключевое слово `COLLECTION`, за которым следует определение другого типа в скобках (например, «Collection(AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="75901-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="75901-111">Ключевое слово ROW, за которым следует список определений свойств в скобках (например, «Row(x AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="75901-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="75901-112">Определения свойств имеют формат "`identifier type_definition`, `identifier type_definition`,...».</span><span class="sxs-lookup"><span data-stu-id="75901-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="75901-113">Ключевое слово REF, за которым следует тип идентификатора в скобках (например, «Ref(AdventureWorks.Order)»).</span><span class="sxs-lookup"><span data-stu-id="75901-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="75901-114">Для оператора определения типа REF требуется присутствие типа сущности в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="75901-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="75901-115">В качестве аргумента нельзя указать тип-примитив.</span><span class="sxs-lookup"><span data-stu-id="75901-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="75901-116">Определения типов также можно вкладывать друг в друга (например, «Collection(Row(x Ref(AdventureWorks.Order)))»).</span><span class="sxs-lookup"><span data-stu-id="75901-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="75901-117">Определения типов имеют следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="75901-117">The type definition options are:</span></span>  
  
-   `IdentifierName supported_type`<span data-ttu-id="75901-118">, или</span><span class="sxs-lookup"><span data-stu-id="75901-118">, or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="75901-119">КОЛЛЕКЦИИ (`type_definition`), или</span><span class="sxs-lookup"><span data-stu-id="75901-119">COLLECTION(`type_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="75901-120">СТРОКИ (`property_definition`), или</span><span class="sxs-lookup"><span data-stu-id="75901-120">ROW(`property_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="75901-121">REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="75901-121">REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="75901-122">Параметр, определяющий свойство, - `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="75901-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="75901-123">Поддерживаются все типы в текущем пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="75901-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="75901-124">Включаются как типы-примитивы, так и типы сущностей.</span><span class="sxs-lookup"><span data-stu-id="75901-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="75901-125">В поддерживаемые типы сущностей входят только типы сущностей текущего пространства имен.</span><span class="sxs-lookup"><span data-stu-id="75901-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="75901-126">Сюда не входят типы-примитивы.</span><span class="sxs-lookup"><span data-stu-id="75901-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="75901-127">Примеры</span><span class="sxs-lookup"><span data-stu-id="75901-127">Examples</span></span>  
 <span data-ttu-id="75901-128">Ниже приводится пример простого определения типа.</span><span class="sxs-lookup"><span data-stu-id="75901-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="75901-129">Ниже приводится пример определения типа COLLECTION.</span><span class="sxs-lookup"><span data-stu-id="75901-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="75901-130">Ниже приводится пример определения типа ROW.</span><span class="sxs-lookup"><span data-stu-id="75901-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="75901-131">Ниже приводится пример определения типа REF.</span><span class="sxs-lookup"><span data-stu-id="75901-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="75901-132">См. также</span><span class="sxs-lookup"><span data-stu-id="75901-132">See also</span></span>

- [<span data-ttu-id="75901-133">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="75901-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="75901-134">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="75901-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
