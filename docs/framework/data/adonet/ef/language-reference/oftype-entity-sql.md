---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: b5600b4cee23945fe60142b370feb35ac1a2efa1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175685"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)

Возвращает коллекцию объектов из выражения запроса, которое относится к заданному типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Аргументы  

 `expression`  
 Любое допустимое выражение запроса, возвращающее коллекцию объектов.  
  
 `test_type`  
 Тип, по которому проверяется каждый объект, возвращаемый `expression` . Для типа должно быть указано пространство имен.  
  
## <a name="return-value"></a>Возвращаемое значение  

 Коллекция объектов, которые имеют тип `test_type`, базовый тип или тип, производный от `test_type`. Если задан параметр ONLY, возвращаются только экземпляры `test_type` или пустая коллекция.  
  
## <a name="remarks"></a>Remarks  

 Выражение `OFTYPE` задает выражение с определением типа, которое применяется для проверки типа по отношению к каждому элементу коллекции.  Выражение `OFTYPE` позволяет получить новую коллекцию указанного типа, содержащую только те элементы, которые были эквивалентны либо этому типу, либо его подтипу.  
  
 Выражение `OFTYPE` представляет собой сокращение следующего выражения запроса.  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Например, если предположить, что тип Manager представляет собой подтип Employee, то следующее выражение позволяет извлечь из коллекции сотрудников данные только менеджеров:  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 Можно также выполнить приведение коллекции с помощью фильтра типов:  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 Все руководители являются менеджерами компании, поэтому полученная в результате коллекция по-прежнему содержит данные всех руководителей, несмотря на то что теперь по своему типу она рассматривается как коллекция менеджеров.  
  
 В следующей таблице показано поведение оператора `OFTYPE` по отношению к некоторым шаблонам. Все исключения активизируются на стороне клиента перед вызовом поставщика.  
  
|Шаблон|Поведение|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(ComplexType), ComplexType)|Активизирует исключение|  
|OFTYPE(Collection(RowType), RowType)|Активизирует исключение|  
  
## <a name="example"></a>Пример  

 В следующем запросе [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператор OFTYPE возвращает коллекцию объектов OnsiteCourse из коллекции объектов Course. Запрос основан на [модели School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>См. также раздел

- [Справочник по Entity SQL](entity-sql-reference.md)
