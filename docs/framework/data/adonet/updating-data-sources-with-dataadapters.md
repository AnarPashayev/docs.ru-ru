---
title: Обновление источников данных с объектами DataAdapter
description: Узнайте, как метод Update объекта DataAdapter разрешает изменения из набора данных обратно в источник данных в ADO.NET приложениях.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286188"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="f27b8-103">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="f27b8-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="f27b8-104">Метод `Update` объекта <xref:System.Data.Common.DataAdapter> вызывается для решения задачи по передаче изменений из <xref:System.Data.DataSet> обратно в источник данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="f27b8-105">Метод `Update`, как и метод `Fill`, принимает в качестве аргументов экземпляр `DataSet`, а также (необязательно) объект <xref:System.Data.DataTable> или имя `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="f27b8-106">Экземпляр `DataSet` представляет собой объект `DataSet`, который содержит выполненные изменения, а `DataTable` указывает на таблицу, из которой должны быть получены эти изменения.</span><span class="sxs-lookup"><span data-stu-id="f27b8-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="f27b8-107">Если ни один объект `DataTable` не задан, используется первый объект `DataTable` в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="f27b8-108">При вызове метода `Update` в `DataAdapter` анализируются внесенные изменения и выполняется соответствующая команда (INSERT, UPDATE или DELETE).</span><span class="sxs-lookup"><span data-stu-id="f27b8-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="f27b8-109">Если в `DataAdapter` обнаруживается изменение в <xref:System.Data.DataRow>, то в этом объекте используется команда <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> или <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> для обработки этого изменения.</span><span class="sxs-lookup"><span data-stu-id="f27b8-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="f27b8-110">Это позволяет максимально повысить производительность приложения ADO.NET путем задания синтаксиса команды во время разработки, а также, по возможности, за счет применения хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="f27b8-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="f27b8-111">Необходимо явно задавать команды перед вызовом `Update`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="f27b8-112">Если вызывается `Update`, и не существует подходящая команда для конкретного обновления (например, отсутствует `DeleteCommand` для удаленных строк), то активизируется исключение.</span><span class="sxs-lookup"><span data-stu-id="f27b8-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="f27b8-113">При использовании хранимых процедур SQL Server для изменения или удаления данных с помощью `DataAdapter` убедитесь, что в определении хранимой процедуры не указана инструкция SET NOCOUNT ON.</span><span class="sxs-lookup"><span data-stu-id="f27b8-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="f27b8-114">В таком случае возвращается число затронутых строк, равное нулю, что `DataAdapter` интерпретирует как конфликт параллелизма.</span><span class="sxs-lookup"><span data-stu-id="f27b8-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="f27b8-115">Это событие вызовет исключение <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="f27b8-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="f27b8-116">Параметры команды могут использоваться в целях указания входных и выходных значений для инструкции SQL или хранимой процедуры применительно к каждой модифицированной строке в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="f27b8-117">Дополнительные сведения см. в разделе [Параметры DataAdapter](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f27b8-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f27b8-118">Важно учитывать различие между обозначением строки как удаленной в <xref:System.Data.DataTable> и удалением этой строки.</span><span class="sxs-lookup"><span data-stu-id="f27b8-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="f27b8-119">Если вызывается метод `Remove` или `RemoveAt`, строка немедленно удаляется.</span><span class="sxs-lookup"><span data-stu-id="f27b8-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="f27b8-120">Любые соответствующие строки в серверном источнике данных остаются не затронутыми, если после этого будет передано значение `DataTable` или `DataSet` в `DataAdapter` и вызван метод `Update`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="f27b8-121">Если же используется метод `Delete`, то строка остается в `DataTable` и отмечается как предназначенная для удаления.</span><span class="sxs-lookup"><span data-stu-id="f27b8-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="f27b8-122">Если после этого будет передано значение `DataTable` или `DataSet` в `DataAdapter` и вызван метод `Update`, то соответствующая строка в серверном источнике данных становится удаленной.</span><span class="sxs-lookup"><span data-stu-id="f27b8-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="f27b8-123">Если значение `DataTable` сопоставляется или создается на основе одной таблицы базы данных, то можно воспользоваться тем, что объект <xref:System.Data.Common.DbCommandBuilder> автоматически создает объекты `DeleteCommand`, `InsertCommand` и `UpdateCommand` для `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="f27b8-124">Дополнительные сведения см. в разделе [Создание команд с помощью коммандбуилдерс](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="f27b8-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="f27b8-125">Использование объекта UpdatedRowSource для сопоставления значений с набором данных</span><span class="sxs-lookup"><span data-stu-id="f27b8-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="f27b8-126">Можно управлять тем, как значения, возвращенные из источника данных, сопоставляются в обратном направлении с `DataTable` вслед за вызовом метода Update объекта `DataAdapter` с использованием свойства <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> объекта <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="f27b8-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="f27b8-127">Задавая значение свойства `UpdatedRowSource` равным одному из значений перечисления <xref:System.Data.UpdateRowSource>, можно управлять тем, должны ли пропускаться выходные параметры, возвращаемые командами `DataAdapter`, или применяться к изменившейся строке в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="f27b8-128">Можно также указать, применяется ли первая возвращенная строка (если она существует) к изменившейся строке в `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="f27b8-129">В следующей таблице приведено описание различных значений перечисления `UpdateRowSource` и показано, как они влияют на поведение команды, используемой в сочетании с `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="f27b8-130">Перечисление UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="f27b8-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="f27b8-131">Описание</span><span class="sxs-lookup"><span data-stu-id="f27b8-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="f27b8-132">И выходные параметры, и первая строка возвращенного результирующего набора могут быть сопоставлены с модифицированной строкой в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="f27b8-133">Только данные из первой строки возвращенного результирующего набора могут быть сопоставлены с модифицированной строкой в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="f27b8-134">Любые выходные параметры или строки возвращенного результирующего набора пропускаются.</span><span class="sxs-lookup"><span data-stu-id="f27b8-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="f27b8-135">Только выходные параметры могут быть сопоставлены с модифицированной строкой в `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="f27b8-136">Метод `Update` позволяет решить задачу по передаче внесенных изменений обратно в источник данных; но может оказаться так, что другие клиенты уже внесли изменения в данные источника данных с того момента, как последний раз было осуществлено заполнение `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="f27b8-137">Чтобы обновить применяемый объект `DataSet` с использованием текущих данных, воспользуйтесь `DataAdapter` и методом `Fill`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="f27b8-138">Произойдет добавление новых строк к таблице, а обновленная информация будет включена в существующие строки.</span><span class="sxs-lookup"><span data-stu-id="f27b8-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="f27b8-139">Метод `Fill` определяет, должна ли быть добавлена новая строка или обновлена существующая строка, путем проверки значений первичного ключа в строках объекта `DataSet` и в строках, возвращенных `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="f27b8-140">Если в методе `Fill` обнаруживается значение первичного ключа какой-то строки в `DataSet`, которое совпадает со значением первичного ключа строки в результатах, возвращенных `SelectCommand`, то метод обновляет существующую строку на основании данных из строки, возвращенной `SelectCommand`, и задает значение <xref:System.Data.DataRow.RowState%2A> существующей строки, равное `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="f27b8-141">Если строка, возвращенная `SelectCommand`, имеет значение первичного ключа, не совпадающее ни с одним из значений первичного ключа в строках в `DataSet`, то метод `Fill` добавляет новую строку со значением `RowState`, равным `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="f27b8-142">Если метод `SelectCommand` возвращает результаты инструкции OUTER JOIN, то `DataAdapter` не задает значение `PrimaryKey` для результирующего набора `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="f27b8-143">Необходимо непосредственно определить значение `PrimaryKey` для обеспечения того, чтобы решение по обработке повторяющихся строк было принято правильно.</span><span class="sxs-lookup"><span data-stu-id="f27b8-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="f27b8-144">Дополнительные сведения см. в разделе [Определение первичных ключей](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="f27b8-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="f27b8-145">Для обработки исключений, которые могут возникнуть при вызове `Update` метода, можно использовать `RowUpdated` событие для реагирования на ошибки обновления строк по мере их возникновения (см. раздел [Обработка событий DataAdapter](handling-dataadapter-events.md)) или установить `DataAdapter.ContinueUpdateOnError` значение `true` до вызова `Update` и ответить на сведения об ошибке, хранящиеся в `RowError` свойстве определенной строки после завершения обновления (см. [сведения об ошибке строки](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="f27b8-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="f27b8-146">Вызов метода `AcceptChanges` для `DataSet` , `DataTable` или `DataRow` приведет к тому, что все `Original` значения для `DataRow` будут перезаписаны `Current` значениями для `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="f27b8-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="f27b8-147">Если были изменены значения полей, уникальным образом идентифицирующих строку, то после вызова метода `AcceptChanges` значения `Original` больше не будут соответствовать этим значениям в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="f27b8-148">Метод `AcceptChanges` вызывается автоматически для каждой строки во время вызова метода Update объекта `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="f27b8-149">Можно сохранить первоначальные значения во время вызова метода Update, для чего вначале следует задать значение свойства `AcceptChangesDuringUpdate` объекта `DataAdapter` равным false, или создать обработчик событий для события `RowUpdated` и задать значение <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A>, равное <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="f27b8-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="f27b8-150">Дополнительные сведения см. в разделе [Объединение содержимого набора данных](./dataset-datatable-dataview/merging-dataset-contents.md) и [Обработка событий DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="f27b8-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="f27b8-151">Пример</span><span class="sxs-lookup"><span data-stu-id="f27b8-151">Example</span></span>

<span data-ttu-id="f27b8-152">В следующих примерах показано, как выполнять обновления измененных строк путем явного задания значения свойства `UpdateCommand` `DataAdapter` и вызова его `Update` метода.</span><span class="sxs-lookup"><span data-stu-id="f27b8-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="f27b8-153">Обратите внимание на то, что задан параметр, указанный в предложении WHERE инструкции UPDATE, чтобы использовалось значение `Original` объекта `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="f27b8-154">Это важно, поскольку значение `Current` могло быть изменено, поэтому может не соответствовать этому значению в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="f27b8-155">Значение `Original` представляет собой значение, которое использовалось для заполнения `DataTable` из источника данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="f27b8-156">Столбцы AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="f27b8-156">AutoIncrement Columns</span></span>

<span data-ttu-id="f27b8-157">Если в таблицах из применяемого источника данных имеются столбцы с автоматическим увеличением значений, то можно обеспечить заполнение столбцов в применяемом `DataSet` путем возврата автоматически увеличивающегося значения как выходного параметра хранимой процедуры и сопоставления его со столбцом таблицы; возврата автоматически увеличивающегося значения в первой строке результирующего набора, возвращенного хранимой процедурой или инструкцией SQL; а также использование события `RowUpdated` объекта `DataAdapter` для выполнения дополнительной инструкции SELECT.</span><span class="sxs-lookup"><span data-stu-id="f27b8-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="f27b8-158">Дополнительные сведения и пример см. в разделе [Получение значений Identity или автонумерации](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="f27b8-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="f27b8-159">Упорядочение вставок, обновлений и удалений</span><span class="sxs-lookup"><span data-stu-id="f27b8-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="f27b8-160">Во многих обстоятельствах имеет значение последовательность передачи изменений, внесенных с помощью `DataSet`, в источник данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="f27b8-161">Например, если происходит обновление значения первичного ключа для существующей строки и добавляется новая строка с новым значением первичного ключа в качестве внешнего ключа, то важно вначале осуществить обновление, а затем вставку.</span><span class="sxs-lookup"><span data-stu-id="f27b8-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="f27b8-162">Можно использовать метод `Select` объекта `DataTable` для возврата массива `DataRow`, который ссылается только на строки с конкретным значением `RowState`.</span><span class="sxs-lookup"><span data-stu-id="f27b8-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="f27b8-163">После этого можно передать возвращенный массив `DataRow` в метод `Update` объекта `DataAdapter` для обработки измененных строк.</span><span class="sxs-lookup"><span data-stu-id="f27b8-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="f27b8-164">Задавая подмножество строк, подлежащих обновлению, можно управлять тем, в какой последовательности обрабатываются вставки, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="f27b8-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="f27b8-165">Пример</span><span class="sxs-lookup"><span data-stu-id="f27b8-165">Example</span></span>

<span data-ttu-id="f27b8-166">Например, в следующем коде обеспечивается то, что удаленные строки таблицы обрабатываются в первую очередь, затем происходит обработка обновленных строк, после чего обрабатываются вставленные строки.</span><span class="sxs-lookup"><span data-stu-id="f27b8-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="f27b8-167">Используйте DataAdapter для извлечения и обновления данных</span><span class="sxs-lookup"><span data-stu-id="f27b8-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="f27b8-168">DataAdapter можно использовать для извлечения и обновления данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="f27b8-169">В этом примере DataAdapter.AcceptChangesDuringFill используется для клонирования данных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="f27b8-170">Если свойство имеет значение false, AcceptChanges при заполнении таблицы не вызывается и позднее добавленные строки рассматриваются как вставленные строки.</span><span class="sxs-lookup"><span data-stu-id="f27b8-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="f27b8-171">Таким образом, в примере эти строки используются для вставки новых строк в базу данных.</span><span class="sxs-lookup"><span data-stu-id="f27b8-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="f27b8-172">В этом примере DataAdapter.TableMappings используется для определения сопоставления между исходной таблицей и DataTable.</span><span class="sxs-lookup"><span data-stu-id="f27b8-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="f27b8-173">В этом примере DataAdapter.FillLoadOption используется для определения того, как адаптер заполняет DataTable из DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="f27b8-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="f27b8-174">При создании объекта DataTable можно выполнять запись данных из базы данных только в текущую или исходную версию путем установки свойства в LoadOption.Upsert или LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="f27b8-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="f27b8-175">В примере также обновляется таблица путем использования DbDataAdapter.UpdateBatchSize для выполнения пакетных операций.</span><span class="sxs-lookup"><span data-stu-id="f27b8-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="f27b8-176">Перед компиляцией и выполнением примера необходимо создать образец базы данных:</span><span class="sxs-lookup"><span data-stu-id="f27b8-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="f27b8-177">Проекты C# и Visual Basic с этим примером кода можно найти в [примерах кода для разработчиков](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="f27b8-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="f27b8-178">См. также</span><span class="sxs-lookup"><span data-stu-id="f27b8-178">See also</span></span>

- [<span data-ttu-id="f27b8-179">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="f27b8-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="f27b8-180">Состояния и версии строк</span><span class="sxs-lookup"><span data-stu-id="f27b8-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="f27b8-181">AcceptChanges и RejectChanges</span><span class="sxs-lookup"><span data-stu-id="f27b8-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="f27b8-182">Слияние содержимого набора данных</span><span class="sxs-lookup"><span data-stu-id="f27b8-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="f27b8-183">Извлечение идентификации или значений автонумерации</span><span class="sxs-lookup"><span data-stu-id="f27b8-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="f27b8-184">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f27b8-184">ADO.NET Overview</span></span>](ado-net-overview.md)
