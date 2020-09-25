---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 3360ad4ca7306a8cc1b7d6948204f825ff9a93c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203622"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)

Определяет, имеет ли выражение запроса значение null.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Аргументы  

 `expression`  
 Любое допустимое выражение запроса. Не может быть коллекцией, содержать элементы коллекции или тип записи со свойствами типа коллекции.  
  
 NOT  
 Логически инвертирует результат EDM.Boolean для IS NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  

 Значение `true`, если выражение `expression` возвращает значение NULL, либо значение `false` - в противном случае.  
  
## <a name="remarks"></a>Remarks  

 Ключевое слово `IS NULL` позволяет определить, имеет ли элемент внешнего соединения значение NULL.  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 Ключевое слово `IS NULL` позволяет определить, имеет ли элемент фактическое значение.  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 В следующей таблице показан эффект применения оператора `IS NULL` в различных конструкциях. Все исключения формируются на стороне клиента перед вызовом поставщика.  
  
|Шаблон|Поведение|  
|-------------|--------------|  
|null IS NULL|Возвращает `true`.|  
|TREAT (null AS EntityType) IS NULL|Возвращает `true`.|  
|TREAT (null AS ComplexType) IS NULL|Вызывает ошибку.|  
|TREAT (null AS RowType) IS NULL|Вызывает ошибку.|  
|EntityType IS NULL|Возвращает значение `true` или `false`.|  
|ComplexType IS NULL|Вызывает ошибку.|  
|RowType IS NULL|Вызывает ошибку.|  
  
## <a name="example"></a>Пример  

 Следующий [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запрос использует оператор is not null, чтобы определить, имеет ли выражение запроса значение, не равное NULL. Запрос основан на модели AdventureWorks Sales. Для компиляции и запуска этого запроса выполните следующие шаги.  
  
1. Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>См. также раздел

- [Справочник по Entity SQL](entity-sql-reference.md)
