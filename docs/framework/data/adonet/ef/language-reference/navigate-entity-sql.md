---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 993c07b824d30c89773c5cfea90c7c194c6b3869
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760419"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

Производит переход по связи, установленной между сущностями.

## <a name="syntax"></a>Синтаксис

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Аргументы

`instance-expression` Экземпляр сущности.

`relationship-type` Имя типа связи из языка CSDL файла определения концептуальной схемы. `relationship-type` Принимается в качестве \<пространства имен >.\< имя_типа_связи >.

`to` Конец связи.

`from` Начало этой связи.

## <a name="return-value"></a>Возвращаемое значение

Если количество элементов в конечной составляющей связи равно 1, то будет возвращено значение `Ref<T>`. Если же количество элементов в конечной составляющей связи равно n, то будет возвращено значение `Collection<Ref<T>>`.

## <a name="remarks"></a>Примечания

Связи являются конструкция первого класса в модели [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] . Связи могут устанавливаться между двумя или несколькими типами сущностей, а пользователи могут переходить по связи от одного элемента (от одной сущности) к другому. `from` и `to` являются необязательными при том условии, что нет неоднозначности в разрешении имен в пределах связи.

Оператор NAVIGATE является допустимым в пространствах O и C.

Конструкция перехода имеет следующую общую форму.

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

Пример:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Здесь OrderCustomer является значением параметра `relationship`, а Customer и Order являются элементами связи `to-end` (customer) и `from-end` (order). Если OrderCustomer был отношений n: 1, то типом результата выражения перехода будет Ref\<клиента >.

Для этого выражение существует следующая упрощенная форма.

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Аналогичным образом в запросе следующей формы выражение перехода вернет значение Collection < Ref\<порядок >>.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Выражение экземпляра должно иметь тип сущности или ссылки.

## <a name="example"></a>Пример

В следующем запросе Entity SQL оператор NAVIGATE используется для перехода по связи, заданной между типами сущностей Address и SalesOrderHeader. Запрос основан на модели AdventureWorks Sales. Для компиляции и запуска этого запроса выполните следующие шаги.

1. Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Практическое руководство. Перейдите связям с помощью оператора Navigate](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
