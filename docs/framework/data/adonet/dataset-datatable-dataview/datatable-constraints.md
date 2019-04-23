---
title: Ограничения таблиц данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 254f486fa19d8af30759d9a9fd6642a1a40e82a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165182"
---
# <a name="datatable-constraints"></a><span data-ttu-id="4df94-102">Ограничения таблиц данных</span><span class="sxs-lookup"><span data-stu-id="4df94-102">DataTable Constraints</span></span>
<span data-ttu-id="4df94-103">Ограничения позволяют принудительно поддерживать целостность данных <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4df94-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="4df94-104">Ограничение представляет собой автоматическое правило, применяемое к столбцу или связанным столбцам и определяющее порядок действий при каком-либо изменении содержимого строки.</span><span class="sxs-lookup"><span data-stu-id="4df94-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="4df94-105">Ограничения применяются при `System.Data.DataSet.EnforceConstraints` свойство <xref:System.Data.DataSet> — **true**.</span><span class="sxs-lookup"><span data-stu-id="4df94-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="4df94-106">Пример кода, показывающий, как установить свойство `EnforceConstraints`, см. в разделе справки <xref:System.Data.DataSet.EnforceConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="4df94-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="4df94-107">В ADO.NET имеется два типа ограничений: <xref:System.Data.ForeignKeyConstraint> и <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="4df94-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="4df94-108">По умолчанию оба ограничения создаются автоматически при создании связи между двух или более таблиц, добавив <xref:System.Data.DataRelation> для **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="4df94-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="4df94-109">Тем не менее, это поведение можно отключить, указав **createConstraints** = **false** при создании связи.</span><span class="sxs-lookup"><span data-stu-id="4df94-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="4df94-110">Ограничение ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="4df94-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="4df94-111">Объект **ForeignKeyConstraint** определяет порядок распространения обновлений и удалений в связанных таблицах.</span><span class="sxs-lookup"><span data-stu-id="4df94-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="4df94-112">Например, если значение в строке одной таблицы обновляется или удаляется и то же самое значение также используется в одном или нескольких связанных таблицах **ForeignKeyConstraint** определяет, что произойдет в связанных таблицах.</span><span class="sxs-lookup"><span data-stu-id="4df94-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="4df94-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> И <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> свойства **ForeignKeyConstraint** определить действие, выполняемое, когда пользователь пытается удалить или обновить строку в связанной таблице.</span><span class="sxs-lookup"><span data-stu-id="4df94-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="4df94-114">В следующей таблице описаны различные доступные параметры для **DeleteRule** и **UpdateRule** свойства **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4df94-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="4df94-115">Установка правил</span><span class="sxs-lookup"><span data-stu-id="4df94-115">Rule setting</span></span>|<span data-ttu-id="4df94-116">Описание</span><span class="sxs-lookup"><span data-stu-id="4df94-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4df94-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="4df94-117">**Cascade**</span></span>|<span data-ttu-id="4df94-118">Удалить или обновить связанные строки.</span><span class="sxs-lookup"><span data-stu-id="4df94-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="4df94-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="4df94-119">**SetNull**</span></span>|<span data-ttu-id="4df94-120">Задайте значения в связанных строках **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="4df94-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="4df94-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="4df94-121">**SetDefault**</span></span>|<span data-ttu-id="4df94-122">Присвоить столбцам в связанных строках значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4df94-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="4df94-123">**None**</span><span class="sxs-lookup"><span data-stu-id="4df94-123">**None**</span></span>|<span data-ttu-id="4df94-124">Не выполнять никаких действий в связанных строках.</span><span class="sxs-lookup"><span data-stu-id="4df94-124">Take no action on related rows.</span></span> <span data-ttu-id="4df94-125">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4df94-125">This is the default.</span></span>|  
  
 <span data-ttu-id="4df94-126">Объект **ForeignKeyConstraint** может ограничивать или распространять, изменения на связанные столбцы.</span><span class="sxs-lookup"><span data-stu-id="4df94-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="4df94-127">В зависимости от свойств, заданных для **ForeignKeyConstraint** столбца, если **EnforceConstraints** свойство **набора данных** является **true**, определенные операции в родительскую строку приведет к исключению.</span><span class="sxs-lookup"><span data-stu-id="4df94-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="4df94-128">Например если **DeleteRule** свойство **ForeignKeyConstraint** — **None**, родительскую строку нельзя удалить, если он имеет дочерние строки.</span><span class="sxs-lookup"><span data-stu-id="4df94-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="4df94-129">Можно создать ограничение внешнего ключа между отдельными столбцами или массивом столбцов с помощью **ForeignKeyConstraint** конструктор.</span><span class="sxs-lookup"><span data-stu-id="4df94-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="4df94-130">Передайте объект **ForeignKeyConstraint** объект **добавить** метод таблицы **ограничения** свойство, являющееся **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="4df94-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4df94-131">Можно также передать аргументы конструктора из нескольких перегруженных **добавить** метод **ConstraintCollection** для создания **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4df94-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="4df94-132">При создании **ForeignKeyConstraint**, вы можете передать **DeleteRule** и **UpdateRule** значения в конструктор как аргументы, или задать их в виде свойств, как показано на Следующий пример (где **DeleteRule** присваивается значение **None**).</span><span class="sxs-lookup"><span data-stu-id="4df94-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="4df94-133">Свойство AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="4df94-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="4df94-134">Изменения в строках можно принять, используя **AcceptChanges** метода или отменить с помощью метода **RejectChanges** метод **набора данных**, **DataTable**, или **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="4df94-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="4df94-135">Когда **набора данных** содержит **ForeignKeyConstraints**, вызов **AcceptChanges** или **RejectChanges** методов обеспечивает  **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="4df94-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="4df94-136">**AcceptRejectRule** свойство **ForeignKeyConstraint** определяет действие, которое будет предпринять в дочерних строках, если **AcceptChanges** или  **RejectChanges** вызывается в родительской строке.</span><span class="sxs-lookup"><span data-stu-id="4df94-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="4df94-137">В следующей таблице перечислены доступные параметры для **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="4df94-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="4df94-138">Установка правил</span><span class="sxs-lookup"><span data-stu-id="4df94-138">Rule setting</span></span>|<span data-ttu-id="4df94-139">Описание</span><span class="sxs-lookup"><span data-stu-id="4df94-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4df94-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="4df94-140">**Cascade**</span></span>|<span data-ttu-id="4df94-141">Принять или отклонить изменения в дочерних строках.</span><span class="sxs-lookup"><span data-stu-id="4df94-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="4df94-142">**None**</span><span class="sxs-lookup"><span data-stu-id="4df94-142">**None**</span></span>|<span data-ttu-id="4df94-143">Не выполнять никаких действий в дочерних строках.</span><span class="sxs-lookup"><span data-stu-id="4df94-143">Take no action on child rows.</span></span> <span data-ttu-id="4df94-144">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4df94-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="4df94-145">Пример</span><span class="sxs-lookup"><span data-stu-id="4df94-145">Example</span></span>  
 <span data-ttu-id="4df94-146">В следующем примере создается ограничение <xref:System.Data.ForeignKeyConstraint>, устанавливаются некоторые из его свойств, в том числе <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, а само ограничение добавляется в коллекцию <xref:System.Data.ConstraintCollection> объекта <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4df94-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="4df94-147">Ограничение UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="4df94-147">UniqueConstraint</span></span>  
 <span data-ttu-id="4df94-148">**UniqueConstraint** объект, который можно назначить отдельным столбцом или массиву столбцов в **DataTable**, обеспечивает уникальность каждой строки все данные в указанном столбце или столбцах.</span><span class="sxs-lookup"><span data-stu-id="4df94-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="4df94-149">Можно создать ограничение уникальности для столбца или массива столбцов с помощью **UniqueConstraint** конструктор.</span><span class="sxs-lookup"><span data-stu-id="4df94-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="4df94-150">Передайте объект **UniqueConstraint** объект **добавить** метод таблицы **ограничения** свойство, являющееся **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="4df94-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4df94-151">Можно также передать аргументы конструктора из нескольких перегруженных **добавить** метод **ConstraintCollection** для создания **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4df94-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="4df94-152">При создании **UniqueConstraint** для столбца или столбцов, при необходимости можно указать, ли столбец или столбцы первичного ключа.</span><span class="sxs-lookup"><span data-stu-id="4df94-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="4df94-153">Можно также создать ограничение уникальности для столбца, задав **Unique** свойство столбца **true**.</span><span class="sxs-lookup"><span data-stu-id="4df94-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="4df94-154">Кроме того, параметр **Unique** свойство из одного столбца для **false** удаляет любые ограничения уникальности, могут существовать.</span><span class="sxs-lookup"><span data-stu-id="4df94-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="4df94-155">При определении столбца или группы столбцов в качестве первичного ключа таблицы автоматически создается ограничение уникальности для заданного столбца или группы столбцов.</span><span class="sxs-lookup"><span data-stu-id="4df94-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="4df94-156">Если удалить столбец из **PrimaryKey** свойство **DataTable**, **UniqueConstraint** удаляется.</span><span class="sxs-lookup"><span data-stu-id="4df94-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="4df94-157">В следующем примере создается **UniqueConstraint** для двух столбцов **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="4df94-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4df94-158">См. также</span><span class="sxs-lookup"><span data-stu-id="4df94-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="4df94-159">Определение схемы DataTable</span><span class="sxs-lookup"><span data-stu-id="4df94-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="4df94-160">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="4df94-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="4df94-161">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4df94-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
