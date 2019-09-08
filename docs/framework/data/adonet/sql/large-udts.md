---
title: Большие, определяемые пользователем типы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 33f4263c747ac2590234493ec7cb9e6048ed2b96
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794023"
---
# <a name="large-udts"></a><span data-ttu-id="ea9ed-102">Большие, определяемые пользователем типы</span><span class="sxs-lookup"><span data-stu-id="ea9ed-102">Large UDTs</span></span>
<span data-ttu-id="ea9ed-103">Определяемые пользователем типы данных (UDT) позволяют разработчику расширить систему скалярных типов путем сохранения в базе данных SQL Server объектов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="ea9ed-104">Определяемые пользователем типы могут содержать несколько элементов в отличие от традиционных псевдонимов типов данных, состоящих из одного системного типа данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea9ed-105">Чтобы воспользоваться расширенной поддержкой SqlClient определяемых пользователем типов данных большого размера, необходимо установить .NET Framework 3.5 с пакетом обновления 1 (SP1) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="ea9ed-106">Ранее максимальный размер определяемых пользователем типов данных был ограничен 8 килобайтами.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="ea9ed-107">В SQL Server 2008 это ограничение было снято для определяемых пользователем типов данных в формате <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="ea9ed-108">Полную документацию по определяемым пользователем типам данных см. в электронной документации по SQL Server для используемой версии SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ea9ed-109">**Электронная документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ea9ed-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="ea9ed-110">Определяемые пользователем типы CLR</span><span class="sxs-lookup"><span data-stu-id="ea9ed-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="ea9ed-111">Загрузка схем определяемых пользователем типов данных с помощью метода GetSchema</span><span class="sxs-lookup"><span data-stu-id="ea9ed-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="ea9ed-112">Метод <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> класса <xref:System.Data.SqlClient.SqlConnection> возвращает сведения о схеме базы данных в <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="ea9ed-113">Дополнительные сведения см. в разделе [SQL Server коллекции схем](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="ea9ed-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="ea9ed-114">Значения столбца GetSchemaTable для определяемых пользователем типов данных</span><span class="sxs-lookup"><span data-stu-id="ea9ed-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="ea9ed-115">Метод <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> класса <xref:System.Data.SqlClient.SqlDataReader> возвращает объект <xref:System.Data.DataTable> с описанием метаданных столбцов.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="ea9ed-116">В приведенной ниже таблице описаны различия метаданных столбцов для определяемых пользователем типов данных в SQL Server 2005 и SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="ea9ed-117">Столбец SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="ea9ed-117">SqlDataReader column</span></span>|<span data-ttu-id="ea9ed-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="ea9ed-118">SQL Server 2005</span></span>|<span data-ttu-id="ea9ed-119">SQL Server 2008 и более поздние версии</span><span class="sxs-lookup"><span data-stu-id="ea9ed-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="ea9ed-120">Возможны разные варианты</span><span class="sxs-lookup"><span data-stu-id="ea9ed-120">Varies</span></span>|<span data-ttu-id="ea9ed-121">Возможны разные варианты</span><span class="sxs-lookup"><span data-stu-id="ea9ed-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="ea9ed-122">255</span><span class="sxs-lookup"><span data-stu-id="ea9ed-122">255</span></span>|<span data-ttu-id="ea9ed-123">255</span><span class="sxs-lookup"><span data-stu-id="ea9ed-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="ea9ed-124">255</span><span class="sxs-lookup"><span data-stu-id="ea9ed-124">255</span></span>|<span data-ttu-id="ea9ed-125">255</span><span class="sxs-lookup"><span data-stu-id="ea9ed-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="ea9ed-126">Экземпляр определяемого пользователем типа данных</span><span class="sxs-lookup"><span data-stu-id="ea9ed-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="ea9ed-127">Экземпляр определяемого пользователем типа данных</span><span class="sxs-lookup"><span data-stu-id="ea9ed-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="ea9ed-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="ea9ed-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="ea9ed-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="ea9ed-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="ea9ed-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="ea9ed-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="ea9ed-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="ea9ed-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="ea9ed-132">Имя из трех частей, указанное как *Database. SchemaName. TypeName*.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="ea9ed-133">Возможны разные варианты</span><span class="sxs-lookup"><span data-stu-id="ea9ed-133">Varies</span></span>|<span data-ttu-id="ea9ed-134">Возможны разные варианты</span><span class="sxs-lookup"><span data-stu-id="ea9ed-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="ea9ed-135">Вопросы, связанные с SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="ea9ed-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="ea9ed-136">Объект <xref:System.Data.SqlClient.SqlDataReader>, начиная с SQL Server 2008, был расширен для поддержки загрузки значений определяемых пользователем типов данных большого размера.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="ea9ed-137">Способ обработки значений определяемых пользователем типов данных большого размера объектом <xref:System.Data.SqlClient.SqlDataReader> зависит от используемой версии SQL Server, а также от значения параметра `Type System Version` в строке подключения.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="ea9ed-138">Дополнительные сведения см. в разделе <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="ea9ed-139">Следующие методы <xref:System.Data.SqlClient.SqlDataReader> возвращают <xref:System.Data.SqlTypes.SqlBinary> вместо определяемого пользователем типа, если в SQL Server 2005 установлен аргумент `Type System Version`:</span><span class="sxs-lookup"><span data-stu-id="ea9ed-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="ea9ed-140">Следующие методы возвращают массив `Byte[]` вместо определяемого пользователем типа, если в SQL Server 2005 установлен аргумент `Type System Version`:</span><span class="sxs-lookup"><span data-stu-id="ea9ed-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="ea9ed-141">Обратите внимание, что для текущей версии ADO.NET преобразования не выполняются.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="ea9ed-142">Указание параметров SqlParameters</span><span class="sxs-lookup"><span data-stu-id="ea9ed-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="ea9ed-143">Следующие свойства <xref:System.Data.SqlClient.SqlParameter> были расширены для работы с большими определяемыми пользователем типами.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="ea9ed-144">Свойство SqlParameter</span><span class="sxs-lookup"><span data-stu-id="ea9ed-144">SqlParameter Property</span></span>|<span data-ttu-id="ea9ed-145">Описание</span><span class="sxs-lookup"><span data-stu-id="ea9ed-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="ea9ed-146">Возвращает или задает объект, представляющий собой значение параметра.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="ea9ed-147">Значение по умолчанию — null.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-147">The default is null.</span></span> <span data-ttu-id="ea9ed-148">Свойство может принимать значения `SqlBinary`, `Byte[]` или управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="ea9ed-149">Возвращает или задает объект, представляющий собой значение параметра.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="ea9ed-150">Значение по умолчанию — null.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-150">The default is null.</span></span> <span data-ttu-id="ea9ed-151">Свойство может принимать значения `SqlBinary`, `Byte[]` или управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="ea9ed-152">Возвращает или задает размер значения параметра для разрешения.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="ea9ed-153">Значение по умолчанию — 0.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-153">The default value is 0.</span></span> <span data-ttu-id="ea9ed-154">Свойство может быть целым числом, представляющим размер значения параметра.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="ea9ed-155">Для определяемых пользователем типов данных большого размера оно может равняться действительному размеру определяемого пользователем типа или принимать значение -1 - для неизвестных.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="ea9ed-156">Пример извлечения данных</span><span class="sxs-lookup"><span data-stu-id="ea9ed-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="ea9ed-157">В приведенном ниже фрагменте кода демонстрируется извлечение данных определяемого пользователем типа большого размера.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="ea9ed-158">Предполагается, что в переменной `connectionString` хранится допустимая строка подключения к базе данных SQL Server, а в переменной `commandString` - допустимая инструкция SELECT, в которой столбец первичного ключа указан первым.</span><span class="sxs-lookup"><span data-stu-id="ea9ed-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea9ed-159">См. также</span><span class="sxs-lookup"><span data-stu-id="ea9ed-159">See also</span></span>

- [<span data-ttu-id="ea9ed-160">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="ea9ed-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="ea9ed-161">Извлечение сведений о схеме базы данных</span><span class="sxs-lookup"><span data-stu-id="ea9ed-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="ea9ed-162">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="ea9ed-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="ea9ed-163">Двоичные данные и данные большого объема SQL Server</span><span class="sxs-lookup"><span data-stu-id="ea9ed-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="ea9ed-164">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ea9ed-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
