---
title: Сопоставления типов данных SQL Server
ms.date: 03/30/2017
ms.assetid: fafdc31a-f435-4cd3-883f-1dfadd971277
ms.openlocfilehash: 04a3bbd9ba18b30a24b425888cce78597deb068a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583722"
---
# <a name="sql-server-data-type-mappings"></a>Сопоставления типов данных SQL Server
В SQL Server и .NET Framework используются различные системы типов. Например, максимальная разрядность структуры .NET Framework <xref:System.Decimal> составляет 28, в то время как максимальная разрядность десятичных и числовых типов данных SQL Server - 38. Чтобы обеспечить целостность данных при чтении и записи, объект <xref:System.Data.SqlClient.SqlDataReader> предоставляет характерные для SQL Server типизированные методы доступа, возвращающие объекты <xref:System.Data.SqlTypes>, а также методы доступа, возвращающие типы .NET Framework. Типы данных SQL Server и .NET Framework также представлены перечислениями в классах <xref:System.Data.DbType> и <xref:System.Data.SqlDbType>, которые можно использовать при указании типов данных <xref:System.Data.SqlClient.SqlParameter>.  
  
 В следующей таблице показаны выводимые типы .NET Framework, <xref:System.Data.DbType> и <xref:System.Data.SqlDbType> перечисления и методы доступа для <xref:System.Data.SqlClient.SqlDataReader>.  
  
|Тип ядра СУБД SQL Server|Тип платформы .NET Framework|Перечисление SqlDbType|Типизированный метод доступа SqlDataReader SqlTypes|Перечисление DbType|Типизированный метод доступа SqlDataReader DbType|  
|-------------------------------------|-------------------------|---------------------------|-------------------------------------------|------------------------|-----------------------------------------|  
|bigint|Int64|<xref:System.Data.SqlDbType.BigInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt64%2A>|<xref:System.Data.DbType.Int64>|<xref:System.Data.SqlClient.SqlDataReader.GetInt64%2A>|  
|binary|Byte[]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|bit|Boolean|<xref:System.Data.SqlDbType.Bit>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBoolean%2A>|<xref:System.Data.DbType.Boolean>|<xref:System.Data.SqlClient.SqlDataReader.GetBoolean%2A>|  
|char|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.Char>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.AnsiStringFixedLength>,<br /><br /> <xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|Дата <sup>1</sup><br /><br /> (SQL Server 2008 и более поздние версии)|DateTime|<xref:System.Data.SqlDbType.Date> <sup>1</sup>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.Date> <sup>1</sup>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime|DateTime|<xref:System.Data.SqlDbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime2<br /><br /> (SQL Server 2008 и более поздние версии)|DateTime|<xref:System.Data.SqlDbType.DateTime2>|Нет|<xref:System.Data.DbType.DateTime2>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetimeoffset<br /><br /> (SQL Server 2008 и более поздние версии)|DateTimeOffset|<xref:System.Data.SqlDbType.DateTimeOffset>|Нет|<xref:System.Data.DbType.DateTimeOffset>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|  
|decimal|Десятичное число|<xref:System.Data.SqlDbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|FILESTREAM attribute (varbinary(max))|Byte[]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|float|Double|<xref:System.Data.SqlDbType.Float>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDouble%2A>|<xref:System.Data.DbType.Double>|<xref:System.Data.SqlClient.SqlDataReader.GetDouble%2A>|  
|image|Byte[]|<xref:System.Data.SqlDbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|int|Int32|<xref:System.Data.SqlDbType.Int>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt32%2A>|<xref:System.Data.DbType.Int32>|<xref:System.Data.SqlClient.SqlDataReader.GetInt32%2A>|  
|money|Десятичное число|<xref:System.Data.SqlDbType.Money>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nchar|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.NChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.StringFixedLength>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|ntext|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.NText>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|числовой|Десятичное число|<xref:System.Data.SqlDbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nvarchar|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.NVarChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|действительные|Single|<xref:System.Data.SqlDbType.Real>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlSingle%2A>|<xref:System.Data.DbType.Single>|<xref:System.Data.SqlClient.SqlDataReader.GetFloat%2A>|  
|rowversion|Byte[]|<xref:System.Data.SqlDbType.Timestamp>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|smalldatetime|Datetime|<xref:System.Data.SqlDbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|smallint|Int16|<xref:System.Data.SqlDbType.SmallInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt16%2A>|<xref:System.Data.DbType.Int16>|<xref:System.Data.SqlClient.SqlDataReader.GetInt16%2A>|  
|smallmoney|Десятичное число|<xref:System.Data.SqlDbType.SmallMoney>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|sql_variant|Объект <sup>2</sup>|<xref:System.Data.SqlDbType.Variant>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A> <sup>2</sup>|<xref:System.Data.DbType.Object>|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A> <sup>2</sup>|  
|текст|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.Text>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|время<br /><br /> (SQL Server 2008 и более поздние версии)|TimeSpan|<xref:System.Data.SqlDbType.Time>|Нет|<xref:System.Data.DbType.Time>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|отметка времени|Byte[]|<xref:System.Data.SqlDbType.Timestamp>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|tinyint|Byte|<xref:System.Data.SqlDbType.TinyInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlByte%2A>|<xref:System.Data.DbType.Byte>|<xref:System.Data.SqlClient.SqlDataReader.GetByte%2A>|  
|uniqueidentifier|Guid|<xref:System.Data.SqlDbType.UniqueIdentifier>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlGuid%2A>|<xref:System.Data.DbType.Guid>|<xref:System.Data.SqlClient.SqlDataReader.GetGuid%2A>|  
|varbinary|Byte[]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|varchar|String<br /><br /> Char[]|<xref:System.Data.SqlDbType.VarChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.AnsiString>, <xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|xml|Xml|<xref:System.Data.SqlDbType.Xml>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>|<xref:System.Data.DbType.Xml>|Нет|  
  
<sup>1</sup> нельзя задать `DbType` свойство `SqlParameter` для `SqlDbType.Date`.  
<sup>2</sup> используйте конкретный типизированный метод доступа, если известен базовый тип `sql_variant`.  
  
## <a name="sql-server-documentation"></a>Документация по SQL Server

Дополнительные сведения о типах данных SQL Server см. в разделе [типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql).
  
## <a name="see-also"></a>См. также

- [Типы данных SQL Server и ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Двоичные данные и данные большого объема SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [Сопоставления типов данных в ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Настройка параметров и типы данных параметров](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](https://go.microsoft.com/fwlink/?LinkId=217917)
