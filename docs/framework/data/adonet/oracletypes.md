---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 3762fdaee1312a7cb008386bb1f6b7bf7cb4316e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212314"
---
# <a name="oracletypes"></a><span data-ttu-id="5e8ab-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="5e8ab-102">OracleTypes</span></span>
<span data-ttu-id="5e8ab-103">Поставщик данных .NET Framework для Oracle содержит несколько структур, которые можно использовать для работы с типами данных Oracle.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="5e8ab-104">В их числе <xref:System.Data.OracleClient.OracleNumber> и <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e8ab-105">Полное описание этих структур см. в разделе <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="5e8ab-106">Далее приведены примеры на языке C#.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-106">The following C# examples:</span></span>  
  
-   <span data-ttu-id="5e8ab-107">Создайте таблицу Oracle и заполните ее данными.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-107">Create an Oracle table and load it with data.</span></span>  
  
-   <span data-ttu-id="5e8ab-108">Воспользуйтесь объектом <xref:System.Data.OracleClient.OracleDataReader> для доступа к данным и несколькими структурами <xref:System.Data.OracleClient.OracleType> для отображения этих данных.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="5e8ab-109">Создание таблицы Oracle</span><span class="sxs-lookup"><span data-stu-id="5e8ab-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="5e8ab-110">В этом примере создается и загружается данными таблица Oracle.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="5e8ab-111">Пример следует выполнить до запуска следующего примера.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="5e8ab-112">Получение данных из таблицы Oracle</span><span class="sxs-lookup"><span data-stu-id="5e8ab-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="5e8ab-113">В этом примере используется **OracleDataReader** для доступа к данным и несколько **OracleType** структуры для отображения данных.</span><span class="sxs-lookup"><span data-stu-id="5e8ab-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =   
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =   
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =   
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =   
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =   
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e8ab-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5e8ab-114">See also</span></span>

- [<span data-ttu-id="5e8ab-115">Oracle и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e8ab-115">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="5e8ab-116">Управляемые поставщики ADO.NET и центр разработчиков DataSet</span><span class="sxs-lookup"><span data-stu-id="5e8ab-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
