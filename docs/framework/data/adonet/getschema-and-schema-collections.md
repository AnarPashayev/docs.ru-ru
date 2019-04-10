---
title: Коллекции GetSchema и Schema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 11cfad81e40e76691db9f99efd1d60f5528600d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230178"
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="11281-102">Коллекции GetSchema и Schema</span><span class="sxs-lookup"><span data-stu-id="11281-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="11281-103">**Подключения** классы в каждом из управляемых поставщиков .NET Framework реализуют **GetSchema** метод, который используется для получения сведений схем обо базы данных, с которой установлено соединение, и сведения схемы, возвращенные из **GetSchema** метод поставляется в виде <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="11281-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="11281-104">**GetSchema** это перегруженный метод, содержащий необязательные параметры для указания возвращаемой коллекции схем и ограничения объема возвращаемых сведений.</span><span class="sxs-lookup"><span data-stu-id="11281-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="11281-105">Указание коллекций схем</span><span class="sxs-lookup"><span data-stu-id="11281-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="11281-106">Первым необязательным параметром метода **GetSchema** является имя коллекции, который указан как строка.</span><span class="sxs-lookup"><span data-stu-id="11281-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="11281-107">Существует два типа коллекций схем: стандартные (общие для всех поставщиков) и специальные (определенные для каждого поставщика).</span><span class="sxs-lookup"><span data-stu-id="11281-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="11281-108">Можно запросить управляемый поставщик .NET Framework для определения списка поддерживаемых коллекций схем, вызвав **GetSchema** метода без аргументов или с именем коллекции схем «MetaDataCollections».</span><span class="sxs-lookup"><span data-stu-id="11281-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="11281-109">При этом будет возвращена <xref:System.Data.DataTable> со списком поддерживаемых коллекций схем, число ограничений, которые каждая из них поддерживает, и число идентификационных частей, которые в них используются.</span><span class="sxs-lookup"><span data-stu-id="11281-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="11281-110">Получение примера коллекций схем</span><span class="sxs-lookup"><span data-stu-id="11281-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="11281-111">Следующие примеры демонстрируют, как использовать <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> метод поставщика данных .NET Framework для SQL Server <xref:System.Data.SqlClient.SqlConnection> класса для извлечения сведений схем обо всех таблицах, содержащихся в **AdventureWorks**образца базы данных:</span><span class="sxs-lookup"><span data-stu-id="11281-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
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
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
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
  
## <a name="see-also"></a><span data-ttu-id="11281-112">См. также</span><span class="sxs-lookup"><span data-stu-id="11281-112">See also</span></span>

- [<span data-ttu-id="11281-113">Извлечение сведений о схеме базы данных</span><span class="sxs-lookup"><span data-stu-id="11281-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="11281-114">Управляемые поставщики ADO.NET и центр разработчиков DataSet</span><span class="sxs-lookup"><span data-stu-id="11281-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
