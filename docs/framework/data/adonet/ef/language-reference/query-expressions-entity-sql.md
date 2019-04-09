---
title: Выражения запросов (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5f89028b9c501dd840f1dc9445418e4757967db8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146917"
---
# <a name="query-expressions-entity-sql"></a>Выражения запросов (Entity SQL)
Выражение запроса объединяет в едином синтаксисе множество разных операторов запросов. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] предоставляет различные типы выражений, включая следующие: [литералы](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [параметры](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [переменных](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), операторы, [функции](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), операторы работы с наборами и т. д. Дополнительные сведения см. в разделе [Справочник по Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Предложения  
 Выражение запроса состоит из предложений, которые последовательно применяют операции к набору объектов. Они основаны на предложениях, из которых состоят стандартные инструкции выбора языка SQL: [ВЫБЕРИТЕ](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [ГДЕ](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [группировать по](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), и [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Область  
 Имена, определенные в предложении FROM, появляются в области FROM в порядке перечисления, слева направо. В списке JOIN выражения могут ссылаться на имена, которые определены в списке ранее. Открытые свойства элементов, определяемых в предложении FROM, в область FROM не добавляются: в ссылке на них следует всегда использовать имя с псевдонимом. Но обычно все части выражения выбора находятся в области FROM.  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
