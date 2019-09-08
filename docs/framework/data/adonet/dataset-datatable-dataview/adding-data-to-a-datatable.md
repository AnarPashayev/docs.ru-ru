---
title: Добавление данных в таблицу данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 2a001ac8b3d4b8cd9618b3ced7bdf578ebae2e22
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786594"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="656a6-102">Добавление данных в таблицу данных</span><span class="sxs-lookup"><span data-stu-id="656a6-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="656a6-103">После создания объекта <xref:System.Data.DataTable> и определения его структуры с использованием столбцов и ограничений к созданной таблице можно добавлять новые строки данных.</span><span class="sxs-lookup"><span data-stu-id="656a6-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="656a6-104">Чтобы добавить новую строку, объявите новую переменную типа <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="656a6-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="656a6-105">При вызове <xref:System.Data.DataTable.NewRow%2A> метода возвращается новый объект **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="656a6-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="656a6-106">Затем **Таблица** данных создает объект **DataRow** на основе структуры таблицы, как определено в <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="656a6-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="656a6-107">В следующем примере показано, как создать новую строку, вызвав метод **невров** .</span><span class="sxs-lookup"><span data-stu-id="656a6-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="656a6-108">После этого можно манипулировать вновь добавленной строкой с помощью индекса или имени столбца, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="656a6-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="656a6-109">После вставки данных в новую строку метод **Add** используется для добавления строки <xref:System.Data.DataRowCollection>в, показанной в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="656a6-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="656a6-110">Можно также вызвать метод **Add** , чтобы добавить новую строку, передав массив значений, типизированный как <xref:System.Object>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="656a6-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="656a6-111">Передача массива значений, типизированных как **Object**, в метод **Add** создает новую строку внутри таблицы и устанавливает для ее значений столбцов значения в массиве объектов.</span><span class="sxs-lookup"><span data-stu-id="656a6-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="656a6-112">Обратите внимание, что значения в массиве сопоставляются со столбцами последовательно, с учетом порядка этих столбцов в таблице.</span><span class="sxs-lookup"><span data-stu-id="656a6-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="656a6-113">В следующем примере в созданную таблицу **Customers** добавляется 10 строк.</span><span class="sxs-lookup"><span data-stu-id="656a6-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="656a6-114">См. также</span><span class="sxs-lookup"><span data-stu-id="656a6-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="656a6-115">Управление данными в DataTable</span><span class="sxs-lookup"><span data-stu-id="656a6-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="656a6-116">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="656a6-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
