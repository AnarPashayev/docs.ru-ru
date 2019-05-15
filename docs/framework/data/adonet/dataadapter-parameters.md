---
title: Параметры DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 0cdca872e9e76b7491dc571209292a692a06d8f8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583750"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="77890-102">Параметры DataAdapter</span><span class="sxs-lookup"><span data-stu-id="77890-102">DataAdapter Parameters</span></span>
<span data-ttu-id="77890-103">Класс <xref:System.Data.Common.DbDataAdapter> имеет четыре свойства, которые служат для получения данных из источника данных и обновления данных в нем: свойство <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> возвращает данные из источника данных, а свойства <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> и <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> используются для управления изменениями в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="77890-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="77890-104">Свойство `SelectCommand` должно быть установлено до вызова метода `Fill` объекта `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="77890-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="77890-105">Свойства `InsertCommand`, `UpdateCommand` или `DeleteCommand` должны быть установлены до вызова метода `Update` объекта `DataAdapter` в зависимости от того, какие изменения были сделаны в данных в <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="77890-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="77890-106">Например, если добавлены строки, свойство `InsertCommand` должно быть установлено перед вызовом метода `Update`.</span><span class="sxs-lookup"><span data-stu-id="77890-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="77890-107">Если метод `Update` обрабатывает вставленную, обновленную или удаленную строку, `DataAdapter` использует соответствующее свойство `Command` для обработки действия.</span><span class="sxs-lookup"><span data-stu-id="77890-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="77890-108">Текущие данные об измененной строке передаются в объект `Command` через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="77890-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="77890-109">При обновлении строки в источнике данных вызывается инструкция UPDATE, которая использует уникальный идентификатор для идентификации строки в таблице, чтобы обновить.</span><span class="sxs-lookup"><span data-stu-id="77890-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="77890-110">Уникальным идентификатором обычно является значение поля первичного ключа.</span><span class="sxs-lookup"><span data-stu-id="77890-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="77890-111">Инструкция UPDATE использует параметры, содержащие и уникальный идентификатор, и столбцы и обновляемые значения, как показано в следующей инструкции Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="77890-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="77890-112">Синтаксис местозаполнителей параметров зависит от источника данных.</span><span class="sxs-lookup"><span data-stu-id="77890-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="77890-113">В этом примере показаны местозаполнители для источника данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="77890-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="77890-114">Для параметров <xref:System.Data.OleDb> и <xref:System.Data.Odbc> в качестве местозаполнителей используйте вопросительный знак (?).</span><span class="sxs-lookup"><span data-stu-id="77890-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="77890-115">В этом примере Visual Basic `CompanyName` обновляется значение `@CompanyName` для строки где `CustomerID` равен значению `@CustomerID` параметра.</span><span class="sxs-lookup"><span data-stu-id="77890-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="77890-116">Параметры получают данные из измененной строки, используя <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> свойство <xref:System.Data.SqlClient.SqlParameter> объекта.</span><span class="sxs-lookup"><span data-stu-id="77890-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="77890-117">Далее представлены параметры для предыдущего образца инструкции UPDATE.</span><span class="sxs-lookup"><span data-stu-id="77890-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="77890-118">В коде предполагается, что переменная `adapter` представляет действительный объект <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="77890-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="77890-119">Метод `Add` коллекции `Parameters` принимает имя параметра, тип данных, размер (если он применим к типу) и имя <xref:System.Data.Common.DbParameter.SourceColumn%2A> из `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="77890-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="77890-120">Обратите внимание, что <xref:System.Data.Common.DbParameter.SourceVersion%2A> параметра `@CustomerID` установлена в `Original`.</span><span class="sxs-lookup"><span data-stu-id="77890-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="77890-121">Это гарантирует, что существующая строка в источнике данных обновляется, если значение идентифицирующих столбцов изменилось в измененном <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="77890-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="77890-122">В этом случае значение строки `Original` будет соответствовать текущему значению в источнике данных и значение строки `Current` будет содержать обновленное значение.</span><span class="sxs-lookup"><span data-stu-id="77890-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="77890-123">`SourceVersion` для параметра `@CompanyName` не установлена и использует значение по умолчанию строки `Current`.</span><span class="sxs-lookup"><span data-stu-id="77890-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77890-124">Для обоих `Fill` операций `DataAdapter` и `Get` методы `DataReader`, тип .NET Framework выводится из типа, возвращаемого из поставщика данных .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77890-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="77890-125">Выводимые типы .NET Framework и методы доступа для типов данных Microsoft SQL Server, OLE DB и ODBC описываются в [сопоставления типов данных в ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="77890-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="77890-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="77890-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="77890-127">`SourceColumn` и `SourceVersion` могут быть посланы как аргументы в конструктор `Parameter` или установлены как свойства существующих `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="77890-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="77890-128">`SourceColumn` является именем <xref:System.Data.DataColumn> из <xref:System.Data.DataRow>, где значение `Parameter` будет получено.</span><span class="sxs-lookup"><span data-stu-id="77890-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="77890-129">`SourceVersion` задает версию `DataRow`, которую `DataAdapter` использует для получения значения.</span><span class="sxs-lookup"><span data-stu-id="77890-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="77890-130">В следующей таблице показаны значения перечисления <xref:System.Data.DataRowVersion>, доступные для использования с `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="77890-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="77890-131">Перечисление DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="77890-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="77890-132">Описание</span><span class="sxs-lookup"><span data-stu-id="77890-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="77890-133">Параметр использует текущее значение столбца.</span><span class="sxs-lookup"><span data-stu-id="77890-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="77890-134">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77890-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="77890-135">Параметр использует `DefaultValue` столбца.</span><span class="sxs-lookup"><span data-stu-id="77890-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="77890-136">Параметр использует исходное значение столбца.</span><span class="sxs-lookup"><span data-stu-id="77890-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="77890-137">Параметр использует предложенное значение.</span><span class="sxs-lookup"><span data-stu-id="77890-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="77890-138">В примере кода для `SqlClient` в следующем разделе определяется параметр для <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, в котором столбец `CustomerID` используется как `SourceColumn` для двух параметров: `@CustomerID` (`SET CustomerID = @CustomerID`) и `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="77890-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="77890-139">`@CustomerID` Параметр используется для обновления **CustomerID** текущее значение в столбце `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="77890-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="77890-140">В результате `CustomerID` `SourceColumn` с `SourceVersion` из `Current` используется.</span><span class="sxs-lookup"><span data-stu-id="77890-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="77890-141">`@OldCustomerID` Параметр используется для идентификации текущей строки в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="77890-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="77890-142">Так как в версии `Original` строки найдено значение, совпадающее со значением столбца, используется тот же `SourceColumn` (`CustomerID`) с `SourceVersion` для `Original`.</span><span class="sxs-lookup"><span data-stu-id="77890-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="77890-143">Работа с параметрами SqlClient</span><span class="sxs-lookup"><span data-stu-id="77890-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="77890-144">Следующий пример демонстрирует, как создать <xref:System.Data.SqlClient.SqlDataAdapter> и установить <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> в <xref:System.Data.MissingSchemaAction.AddWithKey>, чтобы получить из базы данных дополнительные сведения о схеме.</span><span class="sxs-lookup"><span data-stu-id="77890-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="77890-145">Устанавливаются свойства <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> и <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>, и соответствующие им объекты <xref:System.Data.SqlClient.SqlParameter> добавляются в коллекцию <xref:System.Data.SqlClient.SqlCommand.Parameters%2A>.</span><span class="sxs-lookup"><span data-stu-id="77890-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="77890-146">Метод возвращает объект `SqlDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="77890-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="77890-147">Местозаполнители параметров OleDb</span><span class="sxs-lookup"><span data-stu-id="77890-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="77890-148">Для объектов <xref:System.Data.OleDb.OleDbDataAdapter> и <xref:System.Data.Odbc.OdbcDataAdapter> для идентификации параметров необходимо использовать в качестве местозаполнителей вопросительные знаки (?).</span><span class="sxs-lookup"><span data-stu-id="77890-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 <span data-ttu-id="77890-149">Инструкции параметризованных запросов определяют, какие входные и выходные параметры должны создаваться.</span><span class="sxs-lookup"><span data-stu-id="77890-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="77890-150">Для создания параметра используйте метод `Parameters.Add` или конструктор `Parameter` для задания имени столбца, типа и размера данных.</span><span class="sxs-lookup"><span data-stu-id="77890-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="77890-151">Для внутренних типов данных, таких как `Integer`, нет необходимости включать размер, либо можно указать размер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77890-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="77890-152">В следующем примере кода создаются параметры для инструкции SQL, а затем заполняется `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="77890-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="77890-153">Пример OleDb</span><span class="sxs-lookup"><span data-stu-id="77890-153">OleDb Example</span></span>  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a><span data-ttu-id="77890-154">Параметры Odbc</span><span class="sxs-lookup"><span data-stu-id="77890-154">Odbc Parameters</span></span>  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="77890-155">Если для параметра не указано имя параметра, параметр присваивается предусмотренное по умолчанию имя параметра*N* *,* начиная с имени «Parameter1».</span><span class="sxs-lookup"><span data-stu-id="77890-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="77890-156">Рекомендуется избегать использования параметра*N* соглашение об именовании при указании имени параметра, поскольку такое имя может конфликтовать с именем существующего параметра по умолчанию в `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="77890-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="77890-157">Если указанное имя уже существует, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="77890-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77890-158">См. также</span><span class="sxs-lookup"><span data-stu-id="77890-158">See also</span></span>

- [<span data-ttu-id="77890-159">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="77890-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="77890-160">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="77890-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="77890-161">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="77890-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="77890-162">Изменение данных с помощью хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="77890-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="77890-163">Сопоставления типов данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="77890-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="77890-164">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="77890-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
