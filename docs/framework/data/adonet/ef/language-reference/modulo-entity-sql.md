---
title: (Остаток от деления) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: b08689b6f5b17950738c557e02f995fa85aeb35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160489"
---
# <a name="modulo-entity-sql"></a>(Остаток от деления) (Entity SQL)
Возвращает остаток от деления значения одного выражения на другое.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Аргументы  
 `dividend`  
 Делимое числовое выражение. `dividend` — любое допустимое выражение любого из числовых типов данных.  
  
 `divisor`  
 Числовое выражение, на которое делится делимое. `divisor` — любое допустимое выражение любого из числовых типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Edm.Int32  
  
## <a name="example"></a>Пример  
 В следующем запросе Entity SQL используется арифметический оператор % для получения остатка от деления одного выражения на другое. Запрос основан на модели AdventureWorks Sales. Для компиляции и запуска этого запроса выполните следующие шаги.  
  
1.  Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
