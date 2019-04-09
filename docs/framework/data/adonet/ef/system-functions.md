---
title: Системные функции
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 135154d2f5e26cdf7f2e41e8ed2b561bb75f377e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073452"
---
# <a name="system-functions"></a>Системные функции
Поставщик данных платформы .NET Framework для SQL Server (SqlClient) предоставляет следующие системные функции:  
  
|Функция|Описание|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Возвращает значение контрольной суммы. `CHECKSUM` предназначен для построения хэш-индексов.<br /><br /> **Аргументы**<br /><br /> `value`: Объект `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`, или `Guid`. Можно указать одно, два или три значения.<br /><br /> **Возвращаемое значение**<br /><br /> Абсолютное значение заданного выражения.<br /><br /> **Пример**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Возвращает текущую дату и время во внутреннем формате SQL Server для значений типа `DateTime` с точностью 7 в SQL Server 2008 и с точностью 3 в SQL Server 2005.<br /><br /> **Возвращаемое значение**<br /><br /> Текущее значение системных даты и времени как значение типа `DateTime`.<br /><br /> **Пример**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Возвращает имя текущего пользователя.<br /><br /> **Возвращаемое значение**<br /><br /> Строка `String` в ASCII.<br /><br /> **Пример**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Возвращает число байтов, используемых для представления выражения.<br /><br /> **Аргументы**<br /><br /> `expression`: Объект `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, или `Guid`.<br /><br /> **Возвращаемое значение**<br /><br /> Размер свойств (выраженный числом типа `Int32`).<br /><br /> **Пример**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Возвращает имя рабочей станции.<br /><br /> **Возвращаемое значение**<br /><br /> Строка (`String`) в Юникоде.<br /><br /> **Пример**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Определяет, является ли входное выражение действительной датой.<br /><br /> **Аргументы**<br /><br /> `expression`: Объект `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, или `Guid`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Int32`. Один (1), если входное выражение представляет собой допустимую дату. Ноль (0) в противном случае.<br /><br /> **Пример**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Определяет, имеет ли выражение допустимый числовой тип.<br /><br /> **Аргументы**<br /><br /> `expression`: Объект `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, или `Guid`.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Int32`. Один (1), если входное выражение представляет собой допустимую дату. Ноль (0) в противном случае.<br /><br /> **Пример**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Создает уникальное значение типа Guid.<br /><br /> **Возвращаемое значение**<br /><br /> Объект `Guid`.<br /><br /> **Пример**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Возвращает имя пользователя базы данных по указанному идентификационному номеру.<br /><br /> **Аргументы**<br /><br /> `expression`: Идентификационный номер с типом `Int32`, связанный с пользователем базы данных.<br /><br /> **Возвращаемое значение**<br /><br /> Строка (`String`) в Юникоде.<br /><br /> **Пример**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Дополнительные сведения о строковых функциях, поддерживаемых SqlClient, см. в документации к версии SQL Server, указанной в манифесте поставщика SqlClient.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Системные функции (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Системные функции (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Системные функции (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>См. также

- [Язык Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Функции SqlClient для Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
