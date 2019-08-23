---
title: Ограничения схемы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963176"
---
# <a name="schema-restrictions"></a><span data-ttu-id="78095-102">Ограничения схемы</span><span class="sxs-lookup"><span data-stu-id="78095-102">Schema Restrictions</span></span>
<span data-ttu-id="78095-103">Второй необязательный параметр метода **GetSchema** — это ограничения, которые используются для ограничения объема возвращаемых сведений о схеме и передаются в метод **GetSchema** в виде массива строк.</span><span class="sxs-lookup"><span data-stu-id="78095-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="78095-104">Позиция в массиве определяет значения, которые можно передать, и она эквивалентна номеру ограничения.</span><span class="sxs-lookup"><span data-stu-id="78095-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="78095-105">Например, в приведенной ниже таблице описываются ограничения, поддерживаемые коллекцией схемы Tables, использующей поставщик данных .NET Framework для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="78095-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="78095-106">Дополнительные ограничения для коллекций схем SQL Server перечислены в конце данного раздела.</span><span class="sxs-lookup"><span data-stu-id="78095-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="78095-107">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-107">Restriction Name</span></span>|<span data-ttu-id="78095-108">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-108">Parameter Name</span></span>|<span data-ttu-id="78095-109">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-109">Restriction Default</span></span>|<span data-ttu-id="78095-110">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-111">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-112">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-113">1</span><span class="sxs-lookup"><span data-stu-id="78095-113">1</span></span>|  
|<span data-ttu-id="78095-114">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-114">Owner</span></span>|@Owner|<span data-ttu-id="78095-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-116">2</span><span class="sxs-lookup"><span data-stu-id="78095-116">2</span></span>|  
|<span data-ttu-id="78095-117">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-117">Table</span></span>|@Name|<span data-ttu-id="78095-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-118">TABLE_NAME</span></span>|<span data-ttu-id="78095-119">3</span><span class="sxs-lookup"><span data-stu-id="78095-119">3</span></span>|  
|<span data-ttu-id="78095-120">TableType</span><span class="sxs-lookup"><span data-stu-id="78095-120">TableType</span></span>|@TableType|<span data-ttu-id="78095-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78095-121">TABLE_TYPE</span></span>|<span data-ttu-id="78095-122">4</span><span class="sxs-lookup"><span data-stu-id="78095-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="78095-123">Указание значений ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="78095-124">Чтобы использовать одно из ограничений коллекции схем Tables, необходимо создать массив строк с четырьмя элементами, затем поместить значение в элемент, совпадающий с номером ограничения.</span><span class="sxs-lookup"><span data-stu-id="78095-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="78095-125">Например, чтобы ограничить таблицы, возвращаемые методом GetSchema , только таблицами в схеме Sales, задайте для второго элемента массива значение Sales, прежде чем передать его в метод **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="78095-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78095-126">Коллекции ограничений для `SqlClient` и `OracleClient` имеют дополнительный столбец `ParameterName`.</span><span class="sxs-lookup"><span data-stu-id="78095-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="78095-127">Столбец ограничения по умолчанию оставлен для обратной совместимости, но не учитывается.</span><span class="sxs-lookup"><span data-stu-id="78095-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="78095-128">Чтобы свести к минимуму вероятности проведения атак путем внедрения кода SQL, при указании значений ограничений следует использовать параметризированные запросы, а не замену строк.</span><span class="sxs-lookup"><span data-stu-id="78095-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78095-129">Количество элементов в массиве должно быть меньше или равно количеству ограничений, поддерживаемых специальной коллекцией схем, в противном случае возникнет исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="78095-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="78095-130">Их может быть меньше максимального количества ограничений.</span><span class="sxs-lookup"><span data-stu-id="78095-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="78095-131">Предполагается, что отсутствующие ограничения имеют значение NULL (без ограничений).</span><span class="sxs-lookup"><span data-stu-id="78095-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="78095-132">Можно запросить управляемый поставщик .NET Framework, чтобы определить список поддерживаемых ограничений, вызвав метод **GetSchema** с именем коллекции схем ограничений, которая является "ограничениями".</span><span class="sxs-lookup"><span data-stu-id="78095-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="78095-133">Будет возвращен объект <xref:System.Data.DataTable> со списком имен коллекций и ограничений, значениями ограничений по умолчанию и номерами ограничений.</span><span class="sxs-lookup"><span data-stu-id="78095-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="78095-134">Пример</span><span class="sxs-lookup"><span data-stu-id="78095-134">Example</span></span>  
 <span data-ttu-id="78095-135">В следующих примерах показано, как использовать <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> метод поставщика данных .NET Framework для класса SQL Server <xref:System.Data.SqlClient.SqlConnection> , чтобы получить сведения о схеме всех таблиц, содержащихся в образце базы данных **AdventureWorks** . и для ограничения сведений, возвращаемых только таблицам в схеме Sales:</span><span class="sxs-lookup"><span data-stu-id="78095-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="78095-136">Ограничения схемы SQL Server</span><span class="sxs-lookup"><span data-stu-id="78095-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="78095-137">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server.</span><span class="sxs-lookup"><span data-stu-id="78095-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="78095-138">Users</span><span class="sxs-lookup"><span data-stu-id="78095-138">Users</span></span>  
  
|<span data-ttu-id="78095-139">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-139">Restriction Name</span></span>|<span data-ttu-id="78095-140">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-140">Parameter Name</span></span>|<span data-ttu-id="78095-141">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-141">Restriction Default</span></span>|<span data-ttu-id="78095-142">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="78095-143">User_Name</span></span>|@Name|<span data-ttu-id="78095-144">имя</span><span class="sxs-lookup"><span data-stu-id="78095-144">name</span></span>|<span data-ttu-id="78095-145">1</span><span class="sxs-lookup"><span data-stu-id="78095-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="78095-146">Базы данных</span><span class="sxs-lookup"><span data-stu-id="78095-146">Databases</span></span>  
  
|<span data-ttu-id="78095-147">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-147">Restriction Name</span></span>|<span data-ttu-id="78095-148">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-148">Parameter Name</span></span>|<span data-ttu-id="78095-149">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-149">Restriction Default</span></span>|<span data-ttu-id="78095-150">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-151">name</span><span class="sxs-lookup"><span data-stu-id="78095-151">Name</span></span>|@Name|<span data-ttu-id="78095-152">name</span><span class="sxs-lookup"><span data-stu-id="78095-152">Name</span></span>|<span data-ttu-id="78095-153">1</span><span class="sxs-lookup"><span data-stu-id="78095-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="78095-154">Таблицы</span><span class="sxs-lookup"><span data-stu-id="78095-154">Tables</span></span>  
  
|<span data-ttu-id="78095-155">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-155">Restriction Name</span></span>|<span data-ttu-id="78095-156">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-156">Parameter Name</span></span>|<span data-ttu-id="78095-157">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-157">Restriction Default</span></span>|<span data-ttu-id="78095-158">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-159">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-160">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-161">1</span><span class="sxs-lookup"><span data-stu-id="78095-161">1</span></span>|  
|<span data-ttu-id="78095-162">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-162">Owner</span></span>|@Owner|<span data-ttu-id="78095-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-164">2</span><span class="sxs-lookup"><span data-stu-id="78095-164">2</span></span>|  
|<span data-ttu-id="78095-165">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-165">Table</span></span>|@Name|<span data-ttu-id="78095-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-166">TABLE_NAME</span></span>|<span data-ttu-id="78095-167">3</span><span class="sxs-lookup"><span data-stu-id="78095-167">3</span></span>|  
|<span data-ttu-id="78095-168">TableType</span><span class="sxs-lookup"><span data-stu-id="78095-168">TableType</span></span>|@TableType|<span data-ttu-id="78095-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78095-169">TABLE_TYPE</span></span>|<span data-ttu-id="78095-170">4</span><span class="sxs-lookup"><span data-stu-id="78095-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="78095-171">Столбцы</span><span class="sxs-lookup"><span data-stu-id="78095-171">Columns</span></span>  
  
|<span data-ttu-id="78095-172">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-172">Restriction Name</span></span>|<span data-ttu-id="78095-173">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-173">Parameter Name</span></span>|<span data-ttu-id="78095-174">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-174">Restriction Default</span></span>|<span data-ttu-id="78095-175">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-176">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-177">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-178">1</span><span class="sxs-lookup"><span data-stu-id="78095-178">1</span></span>|  
|<span data-ttu-id="78095-179">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-179">Owner</span></span>|@Owner|<span data-ttu-id="78095-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-181">2</span><span class="sxs-lookup"><span data-stu-id="78095-181">2</span></span>|  
|<span data-ttu-id="78095-182">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-182">Table</span></span>|@Table|<span data-ttu-id="78095-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-183">TABLE_NAME</span></span>|<span data-ttu-id="78095-184">3</span><span class="sxs-lookup"><span data-stu-id="78095-184">3</span></span>|  
|<span data-ttu-id="78095-185">Столбец</span><span class="sxs-lookup"><span data-stu-id="78095-185">Column</span></span>|@Column|<span data-ttu-id="78095-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-186">COLUMN_NAME</span></span>|<span data-ttu-id="78095-187">4</span><span class="sxs-lookup"><span data-stu-id="78095-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="78095-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="78095-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="78095-189">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-189">Restriction Name</span></span>|<span data-ttu-id="78095-190">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-190">Parameter Name</span></span>|<span data-ttu-id="78095-191">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-191">Restriction Default</span></span>|<span data-ttu-id="78095-192">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-193">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-194">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-195">1</span><span class="sxs-lookup"><span data-stu-id="78095-195">1</span></span>|  
|<span data-ttu-id="78095-196">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-196">Owner</span></span>|@Owner|<span data-ttu-id="78095-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-198">2</span><span class="sxs-lookup"><span data-stu-id="78095-198">2</span></span>|  
|<span data-ttu-id="78095-199">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-199">Table</span></span>|@Table|<span data-ttu-id="78095-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-200">TABLE_NAME</span></span>|<span data-ttu-id="78095-201">3</span><span class="sxs-lookup"><span data-stu-id="78095-201">3</span></span>|  
|<span data-ttu-id="78095-202">Столбец</span><span class="sxs-lookup"><span data-stu-id="78095-202">Column</span></span>|@Column|<span data-ttu-id="78095-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-203">COLUMN_NAME</span></span>|<span data-ttu-id="78095-204">4</span><span class="sxs-lookup"><span data-stu-id="78095-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="78095-205">Представления</span><span class="sxs-lookup"><span data-stu-id="78095-205">Views</span></span>  
  
|<span data-ttu-id="78095-206">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-206">Restriction Name</span></span>|<span data-ttu-id="78095-207">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-207">Parameter Name</span></span>|<span data-ttu-id="78095-208">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-208">Restriction Default</span></span>|<span data-ttu-id="78095-209">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-210">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-211">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-212">1</span><span class="sxs-lookup"><span data-stu-id="78095-212">1</span></span>|  
|<span data-ttu-id="78095-213">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-213">Owner</span></span>|@Owner|<span data-ttu-id="78095-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-215">2</span><span class="sxs-lookup"><span data-stu-id="78095-215">2</span></span>|  
|<span data-ttu-id="78095-216">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-216">Table</span></span>|@Table|<span data-ttu-id="78095-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-217">TABLE_NAME</span></span>|<span data-ttu-id="78095-218">3</span><span class="sxs-lookup"><span data-stu-id="78095-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="78095-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="78095-219">ViewColumns</span></span>  
  
|<span data-ttu-id="78095-220">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-220">Restriction Name</span></span>|<span data-ttu-id="78095-221">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-221">Parameter Name</span></span>|<span data-ttu-id="78095-222">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-222">Restriction Default</span></span>|<span data-ttu-id="78095-223">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-224">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-225">VIEW_CATALOG</span></span>|<span data-ttu-id="78095-226">1</span><span class="sxs-lookup"><span data-stu-id="78095-226">1</span></span>|  
|<span data-ttu-id="78095-227">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-227">Owner</span></span>|@Owner|<span data-ttu-id="78095-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="78095-229">2</span><span class="sxs-lookup"><span data-stu-id="78095-229">2</span></span>|  
|<span data-ttu-id="78095-230">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-230">Table</span></span>|@Table|<span data-ttu-id="78095-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-231">VIEW_NAME</span></span>|<span data-ttu-id="78095-232">3</span><span class="sxs-lookup"><span data-stu-id="78095-232">3</span></span>|  
|<span data-ttu-id="78095-233">Столбец</span><span class="sxs-lookup"><span data-stu-id="78095-233">Column</span></span>|@Column|<span data-ttu-id="78095-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-234">COLUMN_NAME</span></span>|<span data-ttu-id="78095-235">4</span><span class="sxs-lookup"><span data-stu-id="78095-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="78095-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="78095-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="78095-237">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-237">Restriction Name</span></span>|<span data-ttu-id="78095-238">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-238">Parameter Name</span></span>|<span data-ttu-id="78095-239">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-239">Restriction Default</span></span>|<span data-ttu-id="78095-240">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-241">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="78095-243">1</span><span class="sxs-lookup"><span data-stu-id="78095-243">1</span></span>|  
|<span data-ttu-id="78095-244">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-244">Owner</span></span>|@Owner|<span data-ttu-id="78095-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="78095-246">2</span><span class="sxs-lookup"><span data-stu-id="78095-246">2</span></span>|  
|<span data-ttu-id="78095-247">name</span><span class="sxs-lookup"><span data-stu-id="78095-247">Name</span></span>|@Name|<span data-ttu-id="78095-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="78095-249">3</span><span class="sxs-lookup"><span data-stu-id="78095-249">3</span></span>|  
|<span data-ttu-id="78095-250">Параметр</span><span class="sxs-lookup"><span data-stu-id="78095-250">Parameter</span></span>|@Parameter|<span data-ttu-id="78095-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-251">PARAMETER_NAME</span></span>|<span data-ttu-id="78095-252">4</span><span class="sxs-lookup"><span data-stu-id="78095-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="78095-253">Процедуры</span><span class="sxs-lookup"><span data-stu-id="78095-253">Procedures</span></span>  
  
|<span data-ttu-id="78095-254">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-254">Restriction Name</span></span>|<span data-ttu-id="78095-255">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-255">Parameter Name</span></span>|<span data-ttu-id="78095-256">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-256">Restriction Default</span></span>|<span data-ttu-id="78095-257">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-258">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="78095-260">1</span><span class="sxs-lookup"><span data-stu-id="78095-260">1</span></span>|  
|<span data-ttu-id="78095-261">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-261">Owner</span></span>|@Owner|<span data-ttu-id="78095-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="78095-263">2</span><span class="sxs-lookup"><span data-stu-id="78095-263">2</span></span>|  
|<span data-ttu-id="78095-264">name</span><span class="sxs-lookup"><span data-stu-id="78095-264">Name</span></span>|@Name|<span data-ttu-id="78095-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="78095-266">3</span><span class="sxs-lookup"><span data-stu-id="78095-266">3</span></span>|  
|<span data-ttu-id="78095-267">Тип</span><span class="sxs-lookup"><span data-stu-id="78095-267">Type</span></span>|@Type|<span data-ttu-id="78095-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78095-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="78095-269">4</span><span class="sxs-lookup"><span data-stu-id="78095-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="78095-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="78095-270">IndexColumns</span></span>  
  
|<span data-ttu-id="78095-271">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-271">Restriction Name</span></span>|<span data-ttu-id="78095-272">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-272">Parameter Name</span></span>|<span data-ttu-id="78095-273">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-273">Restriction Default</span></span>|<span data-ttu-id="78095-274">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-275">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="78095-276">db_name()</span></span>|<span data-ttu-id="78095-277">1</span><span class="sxs-lookup"><span data-stu-id="78095-277">1</span></span>|  
|<span data-ttu-id="78095-278">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-278">Owner</span></span>|@Owner|<span data-ttu-id="78095-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="78095-279">user_name()</span></span>|<span data-ttu-id="78095-280">2</span><span class="sxs-lookup"><span data-stu-id="78095-280">2</span></span>|  
|<span data-ttu-id="78095-281">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-281">Table</span></span>|@Table|<span data-ttu-id="78095-282">o.name</span><span class="sxs-lookup"><span data-stu-id="78095-282">o.name</span></span>|<span data-ttu-id="78095-283">3</span><span class="sxs-lookup"><span data-stu-id="78095-283">3</span></span>|  
|<span data-ttu-id="78095-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="78095-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="78095-285">x.name</span><span class="sxs-lookup"><span data-stu-id="78095-285">x.name</span></span>|<span data-ttu-id="78095-286">4</span><span class="sxs-lookup"><span data-stu-id="78095-286">4</span></span>|  
|<span data-ttu-id="78095-287">Столбец</span><span class="sxs-lookup"><span data-stu-id="78095-287">Column</span></span>|@Column|<span data-ttu-id="78095-288">c.name</span><span class="sxs-lookup"><span data-stu-id="78095-288">c.name</span></span>|<span data-ttu-id="78095-289">5</span><span class="sxs-lookup"><span data-stu-id="78095-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="78095-290">Индексы</span><span class="sxs-lookup"><span data-stu-id="78095-290">Indexes</span></span>  
  
|<span data-ttu-id="78095-291">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-291">Restriction Name</span></span>|<span data-ttu-id="78095-292">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-292">Parameter Name</span></span>|<span data-ttu-id="78095-293">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-293">Restriction Default</span></span>|<span data-ttu-id="78095-294">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-295">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="78095-296">db_name()</span></span>|<span data-ttu-id="78095-297">1</span><span class="sxs-lookup"><span data-stu-id="78095-297">1</span></span>|  
|<span data-ttu-id="78095-298">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-298">Owner</span></span>|@Owner|<span data-ttu-id="78095-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="78095-299">user_name()</span></span>|<span data-ttu-id="78095-300">2</span><span class="sxs-lookup"><span data-stu-id="78095-300">2</span></span>|  
|<span data-ttu-id="78095-301">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-301">Table</span></span>|@Table|<span data-ttu-id="78095-302">o.name</span><span class="sxs-lookup"><span data-stu-id="78095-302">o.name</span></span>|<span data-ttu-id="78095-303">3</span><span class="sxs-lookup"><span data-stu-id="78095-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="78095-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="78095-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="78095-305">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-305">Restriction Name</span></span>|<span data-ttu-id="78095-306">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-306">Parameter Name</span></span>|<span data-ttu-id="78095-307">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-307">Restriction Default</span></span>|<span data-ttu-id="78095-308">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="78095-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="78095-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="78095-310">assemblies.name</span></span>|<span data-ttu-id="78095-311">1</span><span class="sxs-lookup"><span data-stu-id="78095-311">1</span></span>|  
|<span data-ttu-id="78095-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="78095-312">udt_name</span></span>|@UDTName|<span data-ttu-id="78095-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="78095-313">types.assembly_class</span></span>|<span data-ttu-id="78095-314">2</span><span class="sxs-lookup"><span data-stu-id="78095-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="78095-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="78095-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="78095-316">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-316">Restriction Name</span></span>|<span data-ttu-id="78095-317">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-317">Parameter Name</span></span>|<span data-ttu-id="78095-318">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-318">Restriction Default</span></span>|<span data-ttu-id="78095-319">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-320">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="78095-322">1</span><span class="sxs-lookup"><span data-stu-id="78095-322">1</span></span>|  
|<span data-ttu-id="78095-323">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-323">Owner</span></span>|@Owner|<span data-ttu-id="78095-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="78095-325">2</span><span class="sxs-lookup"><span data-stu-id="78095-325">2</span></span>|  
|<span data-ttu-id="78095-326">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-326">Table</span></span>|@Table|<span data-ttu-id="78095-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-327">TABLE_NAME</span></span>|<span data-ttu-id="78095-328">3</span><span class="sxs-lookup"><span data-stu-id="78095-328">3</span></span>|  
|<span data-ttu-id="78095-329">name</span><span class="sxs-lookup"><span data-stu-id="78095-329">Name</span></span>|@Name|<span data-ttu-id="78095-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="78095-331">4</span><span class="sxs-lookup"><span data-stu-id="78095-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="78095-332">Ограничения схемы SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="78095-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="78095-333">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="78095-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="78095-334">Эти ограничения действуют, начиная с версии .NET Framework 3.5 с пакетом обновления 1 (SP1) и SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="78095-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="78095-335">Они не поддерживаются в предыдущих версиях .NET Framework и SQL Server.</span><span class="sxs-lookup"><span data-stu-id="78095-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="78095-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="78095-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="78095-337">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-337">Restriction Name</span></span>|<span data-ttu-id="78095-338">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-338">Parameter Name</span></span>|<span data-ttu-id="78095-339">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-339">Restriction Default</span></span>|<span data-ttu-id="78095-340">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-341">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-342">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-343">1</span><span class="sxs-lookup"><span data-stu-id="78095-343">1</span></span>|  
|<span data-ttu-id="78095-344">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-344">Owner</span></span>|@Owner|<span data-ttu-id="78095-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-346">2</span><span class="sxs-lookup"><span data-stu-id="78095-346">2</span></span>|  
|<span data-ttu-id="78095-347">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-347">Table</span></span>|@Table|<span data-ttu-id="78095-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-348">TABLE_NAME</span></span>|<span data-ttu-id="78095-349">3</span><span class="sxs-lookup"><span data-stu-id="78095-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="78095-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="78095-350">AllColumns</span></span>  
  
|<span data-ttu-id="78095-351">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-351">Restriction Name</span></span>|<span data-ttu-id="78095-352">имени параметра</span><span class="sxs-lookup"><span data-stu-id="78095-352">Parameter Name</span></span>|<span data-ttu-id="78095-353">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="78095-353">Restriction Default</span></span>|<span data-ttu-id="78095-354">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="78095-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="78095-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="78095-355">Catalog</span></span>|@Catalog|<span data-ttu-id="78095-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78095-356">TABLE_CATALOG</span></span>|<span data-ttu-id="78095-357">1</span><span class="sxs-lookup"><span data-stu-id="78095-357">1</span></span>|  
|<span data-ttu-id="78095-358">Владелец</span><span class="sxs-lookup"><span data-stu-id="78095-358">Owner</span></span>|@Owner|<span data-ttu-id="78095-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="78095-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="78095-360">2</span><span class="sxs-lookup"><span data-stu-id="78095-360">2</span></span>|  
|<span data-ttu-id="78095-361">Таблица</span><span class="sxs-lookup"><span data-stu-id="78095-361">Table</span></span>|@Table|<span data-ttu-id="78095-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-362">TABLE_NAME</span></span>|<span data-ttu-id="78095-363">3</span><span class="sxs-lookup"><span data-stu-id="78095-363">3</span></span>|  
|<span data-ttu-id="78095-364">Столбец</span><span class="sxs-lookup"><span data-stu-id="78095-364">Column</span></span>|@Column|<span data-ttu-id="78095-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="78095-365">COLUMN_NAME</span></span>|<span data-ttu-id="78095-366">4</span><span class="sxs-lookup"><span data-stu-id="78095-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78095-367">См. также</span><span class="sxs-lookup"><span data-stu-id="78095-367">See also</span></span>

- [<span data-ttu-id="78095-368">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="78095-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
