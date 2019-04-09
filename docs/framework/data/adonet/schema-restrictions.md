---
title: Ограничения схемы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151207"
---
# <a name="schema-restrictions"></a><span data-ttu-id="8755d-102">Ограничения схемы</span><span class="sxs-lookup"><span data-stu-id="8755d-102">Schema Restrictions</span></span>
<span data-ttu-id="8755d-103">Вторым необязательным параметром метода **GetSchema** метод является возвращаемых ограничения, которые используются для ограничения объема данных схемы, и он передается **GetSchema** метод как массив строк .</span><span class="sxs-lookup"><span data-stu-id="8755d-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="8755d-104">Позиция в массиве определяет значения, которые можно передать, и она эквивалентна номеру ограничения.</span><span class="sxs-lookup"><span data-stu-id="8755d-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="8755d-105">Например, в приведенной ниже таблице описываются ограничения, поддерживаемые коллекцией схемы Tables, использующей поставщик данных .NET Framework для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8755d-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="8755d-106">Дополнительные ограничения для коллекций схем SQL Server перечислены в конце данного раздела.</span><span class="sxs-lookup"><span data-stu-id="8755d-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="8755d-107">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-107">Restriction Name</span></span>|<span data-ttu-id="8755d-108">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-108">Parameter Name</span></span>|<span data-ttu-id="8755d-109">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-109">Restriction Default</span></span>|<span data-ttu-id="8755d-110">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-111">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-112">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-113">1</span><span class="sxs-lookup"><span data-stu-id="8755d-113">1</span></span>|  
|<span data-ttu-id="8755d-114">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-114">Owner</span></span>|@Owner|<span data-ttu-id="8755d-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-116">2</span><span class="sxs-lookup"><span data-stu-id="8755d-116">2</span></span>|  
|<span data-ttu-id="8755d-117">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-117">Table</span></span>|@Name|<span data-ttu-id="8755d-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-118">TABLE_NAME</span></span>|<span data-ttu-id="8755d-119">3</span><span class="sxs-lookup"><span data-stu-id="8755d-119">3</span></span>|  
|<span data-ttu-id="8755d-120">TableType</span><span class="sxs-lookup"><span data-stu-id="8755d-120">TableType</span></span>|@TableType|<span data-ttu-id="8755d-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8755d-121">TABLE_TYPE</span></span>|<span data-ttu-id="8755d-122">4</span><span class="sxs-lookup"><span data-stu-id="8755d-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="8755d-123">Указание значений ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="8755d-124">Чтобы использовать одно из ограничений коллекции схем Tables, необходимо создать массив строк с четырьмя элементами, затем поместить значение в элемент, совпадающий с номером ограничения.</span><span class="sxs-lookup"><span data-stu-id="8755d-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="8755d-125">Например, чтобы ограничить таблицы, возвращаемые **GetSchema** метод только таблицами из схемы «Sales», присвойте второму элементу массива значение «Sales» перед передачей в **GetSchema** метод.</span><span class="sxs-lookup"><span data-stu-id="8755d-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8755d-126">Коллекции ограничений для `SqlClient` и `OracleClient` имеют дополнительный столбец `ParameterName`.</span><span class="sxs-lookup"><span data-stu-id="8755d-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="8755d-127">Столбец ограничения по умолчанию оставлен для обратной совместимости, но не учитывается.</span><span class="sxs-lookup"><span data-stu-id="8755d-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="8755d-128">Чтобы свести к минимуму вероятности проведения атак путем внедрения кода SQL, при указании значений ограничений следует использовать параметризированные запросы, а не замену строк.</span><span class="sxs-lookup"><span data-stu-id="8755d-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8755d-129">Количество элементов в массиве должно быть меньше или равно количеству ограничений, поддерживаемых специальной коллекцией схем, в противном случае возникнет исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="8755d-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="8755d-130">Их может быть меньше максимального количества ограничений.</span><span class="sxs-lookup"><span data-stu-id="8755d-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="8755d-131">Предполагается, что отсутствующие ограничения имеют значение NULL (без ограничений).</span><span class="sxs-lookup"><span data-stu-id="8755d-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="8755d-132">Можно запросить управляемый поставщик .NET Framework для определения списка поддерживаемых ограничений, вызвав **GetSchema** метод с именем коллекции схем ограничений, который является «Ограничения».</span><span class="sxs-lookup"><span data-stu-id="8755d-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="8755d-133">Будет возвращен объект <xref:System.Data.DataTable> со списком имен коллекций и ограничений, значениями ограничений по умолчанию и номерами ограничений.</span><span class="sxs-lookup"><span data-stu-id="8755d-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8755d-134">Пример</span><span class="sxs-lookup"><span data-stu-id="8755d-134">Example</span></span>  
 <span data-ttu-id="8755d-135">Следующие примеры демонстрируют, как использовать <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> метод поставщика данных .NET Framework для SQL Server <xref:System.Data.SqlClient.SqlConnection> класса для извлечения сведений схем обо всех таблицах, содержащихся в **AdventureWorks**образца базы данных, и для ограничения сведений, возвращается только таблицами из схемы «Sales»:</span><span class="sxs-lookup"><span data-stu-id="8755d-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="8755d-136">Ограничения схемы SQL Server</span><span class="sxs-lookup"><span data-stu-id="8755d-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="8755d-137">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8755d-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="8755d-138">Users</span><span class="sxs-lookup"><span data-stu-id="8755d-138">Users</span></span>  
  
|<span data-ttu-id="8755d-139">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-139">Restriction Name</span></span>|<span data-ttu-id="8755d-140">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-140">Parameter Name</span></span>|<span data-ttu-id="8755d-141">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-141">Restriction Default</span></span>|<span data-ttu-id="8755d-142">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="8755d-143">User_Name</span></span>|@Name|<span data-ttu-id="8755d-144">имя</span><span class="sxs-lookup"><span data-stu-id="8755d-144">name</span></span>|<span data-ttu-id="8755d-145">1</span><span class="sxs-lookup"><span data-stu-id="8755d-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="8755d-146">Базы данных</span><span class="sxs-lookup"><span data-stu-id="8755d-146">Databases</span></span>  
  
|<span data-ttu-id="8755d-147">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-147">Restriction Name</span></span>|<span data-ttu-id="8755d-148">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-148">Parameter Name</span></span>|<span data-ttu-id="8755d-149">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-149">Restriction Default</span></span>|<span data-ttu-id="8755d-150">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-151">name</span><span class="sxs-lookup"><span data-stu-id="8755d-151">Name</span></span>|@Name|<span data-ttu-id="8755d-152">name</span><span class="sxs-lookup"><span data-stu-id="8755d-152">Name</span></span>|<span data-ttu-id="8755d-153">1</span><span class="sxs-lookup"><span data-stu-id="8755d-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="8755d-154">Таблицы</span><span class="sxs-lookup"><span data-stu-id="8755d-154">Tables</span></span>  
  
|<span data-ttu-id="8755d-155">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-155">Restriction Name</span></span>|<span data-ttu-id="8755d-156">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-156">Parameter Name</span></span>|<span data-ttu-id="8755d-157">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-157">Restriction Default</span></span>|<span data-ttu-id="8755d-158">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-159">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-160">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-161">1</span><span class="sxs-lookup"><span data-stu-id="8755d-161">1</span></span>|  
|<span data-ttu-id="8755d-162">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-162">Owner</span></span>|@Owner|<span data-ttu-id="8755d-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-164">2</span><span class="sxs-lookup"><span data-stu-id="8755d-164">2</span></span>|  
|<span data-ttu-id="8755d-165">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-165">Table</span></span>|@Name|<span data-ttu-id="8755d-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-166">TABLE_NAME</span></span>|<span data-ttu-id="8755d-167">3</span><span class="sxs-lookup"><span data-stu-id="8755d-167">3</span></span>|  
|<span data-ttu-id="8755d-168">TableType</span><span class="sxs-lookup"><span data-stu-id="8755d-168">TableType</span></span>|@TableType|<span data-ttu-id="8755d-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8755d-169">TABLE_TYPE</span></span>|<span data-ttu-id="8755d-170">4</span><span class="sxs-lookup"><span data-stu-id="8755d-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8755d-171">Столбцы</span><span class="sxs-lookup"><span data-stu-id="8755d-171">Columns</span></span>  
  
|<span data-ttu-id="8755d-172">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-172">Restriction Name</span></span>|<span data-ttu-id="8755d-173">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-173">Parameter Name</span></span>|<span data-ttu-id="8755d-174">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-174">Restriction Default</span></span>|<span data-ttu-id="8755d-175">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-176">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-177">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-178">1</span><span class="sxs-lookup"><span data-stu-id="8755d-178">1</span></span>|  
|<span data-ttu-id="8755d-179">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-179">Owner</span></span>|@Owner|<span data-ttu-id="8755d-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-181">2</span><span class="sxs-lookup"><span data-stu-id="8755d-181">2</span></span>|  
|<span data-ttu-id="8755d-182">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-182">Table</span></span>|@Table|<span data-ttu-id="8755d-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-183">TABLE_NAME</span></span>|<span data-ttu-id="8755d-184">3</span><span class="sxs-lookup"><span data-stu-id="8755d-184">3</span></span>|  
|<span data-ttu-id="8755d-185">Столбец</span><span class="sxs-lookup"><span data-stu-id="8755d-185">Column</span></span>|@Column|<span data-ttu-id="8755d-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-186">COLUMN_NAME</span></span>|<span data-ttu-id="8755d-187">4</span><span class="sxs-lookup"><span data-stu-id="8755d-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="8755d-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="8755d-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="8755d-189">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-189">Restriction Name</span></span>|<span data-ttu-id="8755d-190">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-190">Parameter Name</span></span>|<span data-ttu-id="8755d-191">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-191">Restriction Default</span></span>|<span data-ttu-id="8755d-192">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-193">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-194">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-195">1</span><span class="sxs-lookup"><span data-stu-id="8755d-195">1</span></span>|  
|<span data-ttu-id="8755d-196">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-196">Owner</span></span>|@Owner|<span data-ttu-id="8755d-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-198">2</span><span class="sxs-lookup"><span data-stu-id="8755d-198">2</span></span>|  
|<span data-ttu-id="8755d-199">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-199">Table</span></span>|@Table|<span data-ttu-id="8755d-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-200">TABLE_NAME</span></span>|<span data-ttu-id="8755d-201">3</span><span class="sxs-lookup"><span data-stu-id="8755d-201">3</span></span>|  
|<span data-ttu-id="8755d-202">Столбец</span><span class="sxs-lookup"><span data-stu-id="8755d-202">Column</span></span>|@Column|<span data-ttu-id="8755d-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-203">COLUMN_NAME</span></span>|<span data-ttu-id="8755d-204">4</span><span class="sxs-lookup"><span data-stu-id="8755d-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8755d-205">Представления</span><span class="sxs-lookup"><span data-stu-id="8755d-205">Views</span></span>  
  
|<span data-ttu-id="8755d-206">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-206">Restriction Name</span></span>|<span data-ttu-id="8755d-207">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-207">Parameter Name</span></span>|<span data-ttu-id="8755d-208">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-208">Restriction Default</span></span>|<span data-ttu-id="8755d-209">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-210">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-211">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-212">1</span><span class="sxs-lookup"><span data-stu-id="8755d-212">1</span></span>|  
|<span data-ttu-id="8755d-213">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-213">Owner</span></span>|@Owner|<span data-ttu-id="8755d-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-215">2</span><span class="sxs-lookup"><span data-stu-id="8755d-215">2</span></span>|  
|<span data-ttu-id="8755d-216">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-216">Table</span></span>|@Table|<span data-ttu-id="8755d-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-217">TABLE_NAME</span></span>|<span data-ttu-id="8755d-218">3</span><span class="sxs-lookup"><span data-stu-id="8755d-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="8755d-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="8755d-219">ViewColumns</span></span>  
  
|<span data-ttu-id="8755d-220">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-220">Restriction Name</span></span>|<span data-ttu-id="8755d-221">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-221">Parameter Name</span></span>|<span data-ttu-id="8755d-222">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-222">Restriction Default</span></span>|<span data-ttu-id="8755d-223">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-224">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-225">VIEW_CATALOG</span></span>|<span data-ttu-id="8755d-226">1</span><span class="sxs-lookup"><span data-stu-id="8755d-226">1</span></span>|  
|<span data-ttu-id="8755d-227">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-227">Owner</span></span>|@Owner|<span data-ttu-id="8755d-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="8755d-229">2</span><span class="sxs-lookup"><span data-stu-id="8755d-229">2</span></span>|  
|<span data-ttu-id="8755d-230">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-230">Table</span></span>|@Table|<span data-ttu-id="8755d-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-231">VIEW_NAME</span></span>|<span data-ttu-id="8755d-232">3</span><span class="sxs-lookup"><span data-stu-id="8755d-232">3</span></span>|  
|<span data-ttu-id="8755d-233">Столбец</span><span class="sxs-lookup"><span data-stu-id="8755d-233">Column</span></span>|@Column|<span data-ttu-id="8755d-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-234">COLUMN_NAME</span></span>|<span data-ttu-id="8755d-235">4</span><span class="sxs-lookup"><span data-stu-id="8755d-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="8755d-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8755d-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="8755d-237">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-237">Restriction Name</span></span>|<span data-ttu-id="8755d-238">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-238">Parameter Name</span></span>|<span data-ttu-id="8755d-239">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-239">Restriction Default</span></span>|<span data-ttu-id="8755d-240">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-241">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="8755d-243">1</span><span class="sxs-lookup"><span data-stu-id="8755d-243">1</span></span>|  
|<span data-ttu-id="8755d-244">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-244">Owner</span></span>|@Owner|<span data-ttu-id="8755d-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="8755d-246">2</span><span class="sxs-lookup"><span data-stu-id="8755d-246">2</span></span>|  
|<span data-ttu-id="8755d-247">name</span><span class="sxs-lookup"><span data-stu-id="8755d-247">Name</span></span>|@Name|<span data-ttu-id="8755d-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="8755d-249">3</span><span class="sxs-lookup"><span data-stu-id="8755d-249">3</span></span>|  
|<span data-ttu-id="8755d-250">Параметр</span><span class="sxs-lookup"><span data-stu-id="8755d-250">Parameter</span></span>|@Parameter|<span data-ttu-id="8755d-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-251">PARAMETER_NAME</span></span>|<span data-ttu-id="8755d-252">4</span><span class="sxs-lookup"><span data-stu-id="8755d-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8755d-253">Процедуры</span><span class="sxs-lookup"><span data-stu-id="8755d-253">Procedures</span></span>  
  
|<span data-ttu-id="8755d-254">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-254">Restriction Name</span></span>|<span data-ttu-id="8755d-255">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-255">Parameter Name</span></span>|<span data-ttu-id="8755d-256">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-256">Restriction Default</span></span>|<span data-ttu-id="8755d-257">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-258">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="8755d-260">1</span><span class="sxs-lookup"><span data-stu-id="8755d-260">1</span></span>|  
|<span data-ttu-id="8755d-261">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-261">Owner</span></span>|@Owner|<span data-ttu-id="8755d-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="8755d-263">2</span><span class="sxs-lookup"><span data-stu-id="8755d-263">2</span></span>|  
|<span data-ttu-id="8755d-264">name</span><span class="sxs-lookup"><span data-stu-id="8755d-264">Name</span></span>|@Name|<span data-ttu-id="8755d-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="8755d-266">3</span><span class="sxs-lookup"><span data-stu-id="8755d-266">3</span></span>|  
|<span data-ttu-id="8755d-267">Тип</span><span class="sxs-lookup"><span data-stu-id="8755d-267">Type</span></span>|@Type|<span data-ttu-id="8755d-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8755d-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="8755d-269">4</span><span class="sxs-lookup"><span data-stu-id="8755d-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="8755d-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="8755d-270">IndexColumns</span></span>  
  
|<span data-ttu-id="8755d-271">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-271">Restriction Name</span></span>|<span data-ttu-id="8755d-272">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-272">Parameter Name</span></span>|<span data-ttu-id="8755d-273">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-273">Restriction Default</span></span>|<span data-ttu-id="8755d-274">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-275">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="8755d-276">db_name()</span></span>|<span data-ttu-id="8755d-277">1</span><span class="sxs-lookup"><span data-stu-id="8755d-277">1</span></span>|  
|<span data-ttu-id="8755d-278">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-278">Owner</span></span>|@Owner|<span data-ttu-id="8755d-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="8755d-279">user_name()</span></span>|<span data-ttu-id="8755d-280">2</span><span class="sxs-lookup"><span data-stu-id="8755d-280">2</span></span>|  
|<span data-ttu-id="8755d-281">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-281">Table</span></span>|@Table|<span data-ttu-id="8755d-282">o.name</span><span class="sxs-lookup"><span data-stu-id="8755d-282">o.name</span></span>|<span data-ttu-id="8755d-283">3</span><span class="sxs-lookup"><span data-stu-id="8755d-283">3</span></span>|  
|<span data-ttu-id="8755d-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="8755d-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="8755d-285">x.name</span><span class="sxs-lookup"><span data-stu-id="8755d-285">x.name</span></span>|<span data-ttu-id="8755d-286">4</span><span class="sxs-lookup"><span data-stu-id="8755d-286">4</span></span>|  
|<span data-ttu-id="8755d-287">Столбец</span><span class="sxs-lookup"><span data-stu-id="8755d-287">Column</span></span>|@Column|<span data-ttu-id="8755d-288">c.name</span><span class="sxs-lookup"><span data-stu-id="8755d-288">c.name</span></span>|<span data-ttu-id="8755d-289">5</span><span class="sxs-lookup"><span data-stu-id="8755d-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8755d-290">Индексы</span><span class="sxs-lookup"><span data-stu-id="8755d-290">Indexes</span></span>  
  
|<span data-ttu-id="8755d-291">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-291">Restriction Name</span></span>|<span data-ttu-id="8755d-292">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-292">Parameter Name</span></span>|<span data-ttu-id="8755d-293">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-293">Restriction Default</span></span>|<span data-ttu-id="8755d-294">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-295">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="8755d-296">db_name()</span></span>|<span data-ttu-id="8755d-297">1</span><span class="sxs-lookup"><span data-stu-id="8755d-297">1</span></span>|  
|<span data-ttu-id="8755d-298">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-298">Owner</span></span>|@Owner|<span data-ttu-id="8755d-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="8755d-299">user_name()</span></span>|<span data-ttu-id="8755d-300">2</span><span class="sxs-lookup"><span data-stu-id="8755d-300">2</span></span>|  
|<span data-ttu-id="8755d-301">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-301">Table</span></span>|@Table|<span data-ttu-id="8755d-302">o.name</span><span class="sxs-lookup"><span data-stu-id="8755d-302">o.name</span></span>|<span data-ttu-id="8755d-303">3</span><span class="sxs-lookup"><span data-stu-id="8755d-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="8755d-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="8755d-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="8755d-305">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-305">Restriction Name</span></span>|<span data-ttu-id="8755d-306">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-306">Parameter Name</span></span>|<span data-ttu-id="8755d-307">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-307">Restriction Default</span></span>|<span data-ttu-id="8755d-308">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="8755d-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="8755d-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="8755d-310">assemblies.name</span></span>|<span data-ttu-id="8755d-311">1</span><span class="sxs-lookup"><span data-stu-id="8755d-311">1</span></span>|  
|<span data-ttu-id="8755d-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="8755d-312">udt_name</span></span>|@UDTName|<span data-ttu-id="8755d-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="8755d-313">types.assembly_class</span></span>|<span data-ttu-id="8755d-314">2</span><span class="sxs-lookup"><span data-stu-id="8755d-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="8755d-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="8755d-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="8755d-316">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-316">Restriction Name</span></span>|<span data-ttu-id="8755d-317">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-317">Parameter Name</span></span>|<span data-ttu-id="8755d-318">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-318">Restriction Default</span></span>|<span data-ttu-id="8755d-319">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-320">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="8755d-322">1</span><span class="sxs-lookup"><span data-stu-id="8755d-322">1</span></span>|  
|<span data-ttu-id="8755d-323">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-323">Owner</span></span>|@Owner|<span data-ttu-id="8755d-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="8755d-325">2</span><span class="sxs-lookup"><span data-stu-id="8755d-325">2</span></span>|  
|<span data-ttu-id="8755d-326">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-326">Table</span></span>|@Table|<span data-ttu-id="8755d-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-327">TABLE_NAME</span></span>|<span data-ttu-id="8755d-328">3</span><span class="sxs-lookup"><span data-stu-id="8755d-328">3</span></span>|  
|<span data-ttu-id="8755d-329">name</span><span class="sxs-lookup"><span data-stu-id="8755d-329">Name</span></span>|@Name|<span data-ttu-id="8755d-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="8755d-331">4</span><span class="sxs-lookup"><span data-stu-id="8755d-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="8755d-332">Ограничения схемы SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="8755d-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="8755d-333">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8755d-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="8755d-334">Эти ограничения действуют, начиная с версии .NET Framework 3.5 с пакетом обновления 1 (SP1) и SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8755d-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="8755d-335">Они не поддерживаются в предыдущих версиях .NET Framework и SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8755d-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="8755d-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="8755d-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="8755d-337">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-337">Restriction Name</span></span>|<span data-ttu-id="8755d-338">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-338">Parameter Name</span></span>|<span data-ttu-id="8755d-339">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-339">Restriction Default</span></span>|<span data-ttu-id="8755d-340">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-341">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-342">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-343">1</span><span class="sxs-lookup"><span data-stu-id="8755d-343">1</span></span>|  
|<span data-ttu-id="8755d-344">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-344">Owner</span></span>|@Owner|<span data-ttu-id="8755d-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-346">2</span><span class="sxs-lookup"><span data-stu-id="8755d-346">2</span></span>|  
|<span data-ttu-id="8755d-347">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-347">Table</span></span>|@Table|<span data-ttu-id="8755d-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-348">TABLE_NAME</span></span>|<span data-ttu-id="8755d-349">3</span><span class="sxs-lookup"><span data-stu-id="8755d-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="8755d-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="8755d-350">AllColumns</span></span>  
  
|<span data-ttu-id="8755d-351">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-351">Restriction Name</span></span>|<span data-ttu-id="8755d-352">имени параметра</span><span class="sxs-lookup"><span data-stu-id="8755d-352">Parameter Name</span></span>|<span data-ttu-id="8755d-353">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8755d-353">Restriction Default</span></span>|<span data-ttu-id="8755d-354">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="8755d-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8755d-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="8755d-355">Catalog</span></span>|@Catalog|<span data-ttu-id="8755d-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8755d-356">TABLE_CATALOG</span></span>|<span data-ttu-id="8755d-357">1</span><span class="sxs-lookup"><span data-stu-id="8755d-357">1</span></span>|  
|<span data-ttu-id="8755d-358">Владелец</span><span class="sxs-lookup"><span data-stu-id="8755d-358">Owner</span></span>|@Owner|<span data-ttu-id="8755d-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8755d-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="8755d-360">2</span><span class="sxs-lookup"><span data-stu-id="8755d-360">2</span></span>|  
|<span data-ttu-id="8755d-361">Таблица</span><span class="sxs-lookup"><span data-stu-id="8755d-361">Table</span></span>|@Table|<span data-ttu-id="8755d-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-362">TABLE_NAME</span></span>|<span data-ttu-id="8755d-363">3</span><span class="sxs-lookup"><span data-stu-id="8755d-363">3</span></span>|  
|<span data-ttu-id="8755d-364">Столбец</span><span class="sxs-lookup"><span data-stu-id="8755d-364">Column</span></span>|@Column|<span data-ttu-id="8755d-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8755d-365">COLUMN_NAME</span></span>|<span data-ttu-id="8755d-366">4</span><span class="sxs-lookup"><span data-stu-id="8755d-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8755d-367">См. также</span><span class="sxs-lookup"><span data-stu-id="8755d-367">See also</span></span>

- [<span data-ttu-id="8755d-368">Управляемые поставщики ADO.NET и центр разработчиков DataSet</span><span class="sxs-lookup"><span data-stu-id="8755d-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
