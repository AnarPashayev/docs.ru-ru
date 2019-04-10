---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 820d357baf8f3e17a10ced84babc6745512e572b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230035"
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
Извлекает ключ ссылки или выражение сущности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Примечания  
 Ключ сущности содержит значения ключа в правильном порядке указанной сущности или ссылки на сущность. На одном и том же типе сущности могут быть основаны разные наборы сущностей, поэтому в каждом наборе сущностей может появиться одинаковый ключ. Для получения уникальной ссылки используйте `REF`. Возвращаемый тип оператора KEY – это тип строки, включающий одно поле для каждого ключа сущности в том же порядке.  
  
 В следующем примере оператору ключа передается ссылка на сущность BadOrder, и он возвращает ключевую часть этой ссылки. В данном случае – тип записи точно с одним полем, соответствующим свойству `Id` .  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Пример  
 В следующем запросе Entity SQL используется оператор KEY с целью извлечения ключевой части выражения со ссылкой на тип. Запрос основан на модели AdventureWorks Sales. Для компиляции и запуска этого запроса выполните следующие шаги.  
  
1.  Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
