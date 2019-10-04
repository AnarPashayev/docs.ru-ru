---
title: Краткий справочник по Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833878"
---
# <a name="entity-sql-quick-reference"></a>Краткий справочник по Entity SQL
В этом разделе содержится краткий справочник по запросам [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Запросы в этом разделе основаны на модели AdventureWorks Sales.  
  
## <a name="literals"></a>Литералы  
  
### <a name="string"></a>Строковое  
 Существуют строковые литералы в Юникоде и не в Юникоде. Строки в Юникоде добавляются в начало с префиксом N. Например, `N'hello'`.  
  
 Ниже приведен пример строкового литерала не в Юникоде:  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 В литералах DateTime обязательными являются и часть даты, и часть времени. Значения по умолчанию отсутствуют.  
  
 Пример:  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|Понедельник, 25.12.06, 01:01:00|  
  
### <a name="integer"></a>Integer  
 Целочисленные литералы могут иметь тип Int32 (123), UInt32 (123U), Int64 (123L) и UInt64 (123UL).  
  
 Пример:  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Другой  
 Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает и другие типы литералов - Guid, Binary, Float/Double, Decimal и `null`. Литералы NULL в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] считаются совместимыми с любым из других типов в концептуальной модели.  
  
## <a name="type-constructors"></a>Конструкторы типов  
  
### <a name="row"></a>ROW  
 [Строка](row-entity-sql.md) конструирует анонимное, структурно типизированное значение (запись) как в: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Пример:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Результат  
  
|ProductID|name|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 Коллекции [мультинаборов](multiset-entity-sql.md) , например:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Пример:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Результат  
  
|ProductID|name|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Object  
 [Конструктор именованного типа](named-type-constructor-entity-sql.md) конструирует (именованные) определяемые пользователем объекты, такие как `person("abc", 12)`.  
  
 Пример:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Результат  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Ссылки  
  
### <a name="ref"></a>REF  
 [Ref](ref-entity-sql.md) создает ссылку на экземпляр типа сущности. Например, следующий запрос возвращает ссылки на каждую сущность Order в наборе сущностей Orders:  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 В следующем примере оператор извлечения свойства (.) используется для доступа к свойству сущности. При использовании этого оператора автоматически выполняется разыменование ссылки.  
  
 Пример:  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Результат  
  
|Значение|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) разыменование ссылочного значения и выдает результат разыменования. Например, следующий запрос возвращает сущности Order для каждой из записей Order в наборе сущностей Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.  
  
 Пример:  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Результат  
  
|Значение|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF и KEY  
 [CREATEREF](createref-entity-sql.md) создает ссылку, передавая ключ. [Key](key-entity-sql.md) извлекает ключевую часть выражения со ссылкой на тип.  
  
 Пример:  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 Результат  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Функции  
  
### <a name="canonical"></a>Канонические  
 Пространство имен для [канонических функций](canonical-functions.md) — EDM, как в `Edm.Length("string")`. Если не импортировано другое пространство имен, содержащее функцию, имя которой совпадает с именем канонической функции, то указывать пространство имен не обязательно. Если в двух пространствах имен имеется функция с тем же именем, то пользователь должен указать полное имя функции.  
  
 Пример:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Результат  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Функции поставщиков данных (Майкрософт)  
 [Функции, относящиеся к поставщику (Майкрософт)](../sqlclient-for-ef-functions.md) , находятся в пространстве имен `SqlServer`.  
  
 Пример:  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Результат  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Пространства имен  
 [Использование](using-entity-sql.md) задает пространства имен, используемые в выражении запроса.  
  
 Пример:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Разбивка на страницы  
 Разбиение на страницы может быть выражено путем объявления вложенных предложений [Skip](skip-entity-sql.md) и [Limit](limit-entity-sql.md) в предложении [ORDER BY](order-by-entity-sql.md) .  
  
 Пример:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Результат  
  
|id|name|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Группирование  
 [Группирование по](group-by-entity-sql.md) задает группы, в которые должны быть помещены объекты, возвращаемые выражением запроса ([SELECT](select-entity-sql.md)).  
  
 Пример:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Результат  
  
|имя|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>Навигация  
 Оператор навигации по связям позволяет переходить по связям от одной сущности (исходный элемент) к другой (конечный элемент). [Переход](navigate-entity-sql.md) принимает тип отношения, который имеет значение \<namespace >. \<relationship имя типа >. Функция Navigate возвращает значение ref @ no__t-0T >, если количество элементов с начала до конца равно 1. Если число элементов в конец равно n, будет возвращена коллекция < ref @ no__t-0T > >.  
  
 Пример:  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Результат  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>SELECT VALUE и SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает предложение SELECT VALUE, позволяющее пропустить неявное построение строки. В предложении SELECT VALUE может быть указан только один элемент. При использовании такого предложения оболочка строк не создается вокруг элементов в предложении SELECT, а коллекция требуемой формы может быть создана, например: `SELECT VALUE a`.  
  
 Пример:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Результат  
  
|name|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 Язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает также конструктор строк, позволяющий создавать произвольные строки. Предложение SELECT принимает один или несколько элементов в проекции и возвращает запись данных с полями, например: `SELECT a, b, c`.  
  
 Пример:  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|name|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>Выражение варианта выбора  
 [Выражение CASE](case-entity-sql.md) вычисляет набор логических выражений для определения результата.  
  
 Пример:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Результат  
  
|Значение|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](entity-sql-reference.md)
- [Общие сведения об Entity SQL](entity-sql-overview.md)
