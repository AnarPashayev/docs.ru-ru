---
title: Удаление DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196142"
---
# <a name="datarow-deletion"></a><span data-ttu-id="164bc-102">Удаление DataRow</span><span class="sxs-lookup"><span data-stu-id="164bc-102">DataRow Deletion</span></span>
<span data-ttu-id="164bc-103">Существует два способа, можно использовать для удаления <xref:System.Data.DataRow> объекта из <xref:System.Data.DataTable> объект: **удалить** метод <xref:System.Data.DataRowCollection> объекта и <xref:System.Data.DataRow.Delete%2A> метод **DataRow**объекта.</span><span class="sxs-lookup"><span data-stu-id="164bc-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="164bc-104">Тогда как <xref:System.Data.DataRowCollection.Remove%2A> метод удаления **DataRow** из **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> метод только помечает строку для удаления.</span><span class="sxs-lookup"><span data-stu-id="164bc-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="164bc-105">Фактическое удаление происходит, когда приложение вызывает **AcceptChanges** метод.</span><span class="sxs-lookup"><span data-stu-id="164bc-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="164bc-106">Использование метода <xref:System.Data.DataRow.Delete%2A> позволяет программно проверять, какие строки помечены для удаления, перед их фактическим удалением.</span><span class="sxs-lookup"><span data-stu-id="164bc-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="164bc-107">Когда строка отмечена для удаления, ее свойство <xref:System.Data.DataRow.RowState%2A> имеет значение <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="164bc-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="164bc-108">Ни <xref:System.Data.DataRow.Delete%2A>, ни <xref:System.Data.DataRowCollection.Remove%2A> не должны вызываться в цикле foreach во время итерации по объекту <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="164bc-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="164bc-109">Ни <xref:System.Data.DataRow.Delete%2A>, ни <xref:System.Data.DataRowCollection.Remove%2A> не изменяет состояние коллекции.</span><span class="sxs-lookup"><span data-stu-id="164bc-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="164bc-110">При использовании <xref:System.Data.DataSet> или **DataTable** в сочетании с **DataAdapter** и реляционного источника данных, используйте **удалить** метод  **DataRow** для удаления строки.</span><span class="sxs-lookup"><span data-stu-id="164bc-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="164bc-111">**Удалить** метод помечает строку как **Deleted** в **набора данных** или **DataTable** , но не удаляет ее.</span><span class="sxs-lookup"><span data-stu-id="164bc-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="164bc-112">Вместо этого, когда **DataAdapter** обнаруживает строку, помеченную как **Deleted**, он выполняет его **DeleteCommand** метод для удаления строки в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="164bc-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="164bc-113">Строки могут затем быть окончательно удалить с помощью **AcceptChanges** метод.</span><span class="sxs-lookup"><span data-stu-id="164bc-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="164bc-114">Если вы используете **удалить** для удаления строки, строка удаляется из таблицы, но **DataAdapter** не приведет к удалению строки в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="164bc-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="164bc-115">**Удалить** метод **DataRowCollection** принимает **DataRow** в качестве аргумента и удаляет его из коллекции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="164bc-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="164bc-116">Напротив, следующий пример демонстрирует вызов **удалить** метод **DataRow** для изменения его **RowState** для **Deleted** .</span><span class="sxs-lookup"><span data-stu-id="164bc-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="164bc-117">Если строка помечена для удаления и вызывается **AcceptChanges** метод **DataTable** объект, строка удаляется из **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="164bc-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="164bc-118">Напротив, при вызове метода **RejectChanges**, **RowState** строки возвращается к до помечается как **Deleted**.</span><span class="sxs-lookup"><span data-stu-id="164bc-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="164bc-119">Если **RowState** из **DataRow** — **Added**, означающее, что она недавно была добавлена в таблицу и затем она помечается как **Deleted**, это удаляется из таблицы.</span><span class="sxs-lookup"><span data-stu-id="164bc-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="164bc-120">См. также</span><span class="sxs-lookup"><span data-stu-id="164bc-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="164bc-121">Управление данными в DataTable</span><span class="sxs-lookup"><span data-stu-id="164bc-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="164bc-122">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="164bc-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
