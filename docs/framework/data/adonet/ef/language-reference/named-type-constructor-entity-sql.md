---
title: Конструктор именованных типов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c673b58ee5811e3d3b74b3744d3f5291888e2253
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197785"
---
# <a name="named-type-constructor-entity-sql"></a>Конструктор именованных типов (Entity SQL)

Используется для создания экземпляров номинальных типов концептуальной модели, например сложных типов или типов сущностей.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Аргументы  

 `identifier`  
 Значение, представляющее собой простой или заключенный в кавычки идентификатор. Дополнительные сведения см. в разделе [идентификаторы](identifiers-entity-sql.md) .  
  
 `expression`  
 Атрибуты типа, которые, как предполагается, должны располагаться в таком же порядке, как и в декларации этого типа.  
  
## <a name="return-value"></a>Возвращаемое значение  

 Экземпляры именованных сложных типов и типов сущностей.  
  
## <a name="remarks"></a>Remarks  

 В следующих примерах показано, как создавать номинальные и сложные типы.  
  
 Приведенное далее выражение создает экземпляр типа `Person` .  
  
 `Person("abc", 12)`  
  
 Приведенное далее выражение создает экземпляр сложного типа.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Приведенное далее выражение создает экземпляр вложенного сложного типа.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Приведенное далее выражение создает экземпляр сущности с вложенным сложным типом.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 В следующем примере показано, как инициализировать свойство сложного типа значением null:`MyModel.ZipCode(‘98118’, null)`.  
  
## <a name="example"></a>Пример  

 В следующем запросе Entity SQL конструктор именованного типа используется для создания экземпляра типа концептуальной модели. Запрос основан на модели AdventureWorks Sales. Для компиляции и запуска этого запроса выполните следующие шаги.  
  
1. Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a>См. также раздел

- [Сборка типов](constructing-types-entity-sql.md)
- [Справочник по Entity SQL](entity-sql-reference.md)
