---
title: Действия доступа к базе данных
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 5a7c6fa6664acee8000c100513b2cc955ffa3392
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622457"
---
# <a name="database-access-activities"></a><span data-ttu-id="5be9a-102">Действия доступа к базе данных</span><span class="sxs-lookup"><span data-stu-id="5be9a-102">Database Access Activities</span></span>
<span data-ttu-id="5be9a-103">Действия доступа к базе данных позволяют обращаться к базе данных из рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="5be9a-104">Эти действия позволяют доступ к базам данных, чтобы вернуть или изменить сведения, а также использовать [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) для доступа к базе данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5be9a-105">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5be9a-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5be9a-106">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5be9a-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="5be9a-107">Если этот каталог не существует, перейдите к (загрузка страницы) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5be9a-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5be9a-108">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5be9a-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="5be9a-109">Действия базы данных</span><span class="sxs-lookup"><span data-stu-id="5be9a-109">Database Activities</span></span>
 <span data-ttu-id="5be9a-110">В следующих разделах приведен список действий, входящих в этот образец.</span><span class="sxs-lookup"><span data-stu-id="5be9a-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="5be9a-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="5be9a-111">DbUpdate</span></span>
 <span data-ttu-id="5be9a-112">Выполняет SQL-запрос, который реализует изменение в базе данных (вставку, обновление, удаление или иные изменения).</span><span class="sxs-lookup"><span data-stu-id="5be9a-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="5be9a-113">Этот класс выполняет работу асинхронно (он является производным от класса <xref:System.Activities.AsyncCodeActivity> и использует его возможности для асинхронной работы).</span><span class="sxs-lookup"><span data-stu-id="5be9a-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="5be9a-114">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="5be9a-115">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="5be9a-116">После выполнения `DbUpdate` количество измененных записей возвращается в свойстве `AffectedRecords`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="5be9a-117">Аргумент</span><span class="sxs-lookup"><span data-stu-id="5be9a-117">Argument</span></span>|<span data-ttu-id="5be9a-118">Описание</span><span class="sxs-lookup"><span data-stu-id="5be9a-118">Description</span></span>|
|-|-|
|<span data-ttu-id="5be9a-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5be9a-119">ProviderName</span></span>|<span data-ttu-id="5be9a-120">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5be9a-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="5be9a-121">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="5be9a-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="5be9a-122">ConnectionString</span></span>|<span data-ttu-id="5be9a-123">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-123">Connection string to connect to the database.</span></span> <span data-ttu-id="5be9a-124">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="5be9a-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="5be9a-125">ConfigName</span></span>|<span data-ttu-id="5be9a-126">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="5be9a-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="5be9a-127">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="5be9a-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="5be9a-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="5be9a-128">CommandType</span></span>|<span data-ttu-id="5be9a-129">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="5be9a-130">Sql</span><span class="sxs-lookup"><span data-stu-id="5be9a-130">Sql</span></span>|<span data-ttu-id="5be9a-131">Выполняемая команда SQL.</span><span class="sxs-lookup"><span data-stu-id="5be9a-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="5be9a-132">Параметры</span><span class="sxs-lookup"><span data-stu-id="5be9a-132">Parameters</span></span>|<span data-ttu-id="5be9a-133">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="5be9a-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="5be9a-134">AffectedRecords</span></span>|<span data-ttu-id="5be9a-135">Количество записей, на которые повлияла последняя операция.</span><span class="sxs-lookup"><span data-stu-id="5be9a-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="5be9a-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="5be9a-136">DbQueryScalar</span></span>
 <span data-ttu-id="5be9a-137">Выполняет запрос, возвращающий единичное значение данные из базы данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="5be9a-138">Этот класс выполняет работу асинхронно (он является производным от класса <xref:System.Activities.AsyncCodeActivity%601> и использует его возможности для асинхронной работы).</span><span class="sxs-lookup"><span data-stu-id="5be9a-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="5be9a-139">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="5be9a-140">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="5be9a-141">После `DbQueryScalar` является выполнении скалярное значение возвращается в `Result out` аргумент (типа `TResult`, который определен в базовом классе <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="5be9a-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="5be9a-142">Аргумент</span><span class="sxs-lookup"><span data-stu-id="5be9a-142">Argument</span></span>|<span data-ttu-id="5be9a-143">Описание</span><span class="sxs-lookup"><span data-stu-id="5be9a-143">Description</span></span>|
|-|-|
|<span data-ttu-id="5be9a-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5be9a-144">ProviderName</span></span>|<span data-ttu-id="5be9a-145">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5be9a-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="5be9a-146">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="5be9a-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="5be9a-147">ConnectionString</span></span>|<span data-ttu-id="5be9a-148">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-148">Connection string to connect to the database.</span></span> <span data-ttu-id="5be9a-149">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="5be9a-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="5be9a-150">ConfigName</span></span>|<span data-ttu-id="5be9a-151">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="5be9a-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="5be9a-152">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="5be9a-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="5be9a-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="5be9a-153">CommandType</span></span>|<span data-ttu-id="5be9a-154">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="5be9a-155">Sql</span><span class="sxs-lookup"><span data-stu-id="5be9a-155">Sql</span></span>|<span data-ttu-id="5be9a-156">Выполняемая команда SQL.</span><span class="sxs-lookup"><span data-stu-id="5be9a-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="5be9a-157">Параметры</span><span class="sxs-lookup"><span data-stu-id="5be9a-157">Parameters</span></span>|<span data-ttu-id="5be9a-158">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="5be9a-159">Результат</span><span class="sxs-lookup"><span data-stu-id="5be9a-159">Result</span></span>|<span data-ttu-id="5be9a-160">Скаляр, полученный после выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="5be9a-161">Этот аргумент имеет тип `TResult`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="5be9a-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="5be9a-162">DbQuery</span></span>
 <span data-ttu-id="5be9a-163">Выполняет запрос, который возвращает список объектов.</span><span class="sxs-lookup"><span data-stu-id="5be9a-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="5be9a-164">После выполнения запроса выполняется функция сопоставления (это может быть <xref:System.Func%601> < `DbDataReader`, `TResult`> или <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="5be9a-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="5be9a-165">Эта функция сопоставления получает запись в `DbDataReader` и сопоставляет ее возвращаемому объекту.</span><span class="sxs-lookup"><span data-stu-id="5be9a-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="5be9a-166">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="5be9a-167">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="5be9a-168">Результаты SQL-запроса извлекаются с использованием `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="5be9a-169">Действие выполняет перебор по `DbDataReader` и сопоставляет строки в `DbDataReader` с экземпляром `TResult`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="5be9a-170">Пользователь `DbQuery` должен предоставить код сопоставления, что это можно сделать двумя способами: с помощью <xref:System.Func%601> < `DbDataReader`, `TResult`> или <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="5be9a-171">В первом случае сопоставление совершается на одном шаге выполнения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="5be9a-172">Поэтому этот способ быстрее, но сериализация в XAML невозможна.</span><span class="sxs-lookup"><span data-stu-id="5be9a-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="5be9a-173">Во втором случае сопоставление выполняется в несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="5be9a-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="5be9a-174">Поэтому может потребоваться больше времени, зато возможны сериализация в XAML и декларативное авторство (любое существующее действие может участвовать в сопоставлении).</span><span class="sxs-lookup"><span data-stu-id="5be9a-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="5be9a-175">Аргумент</span><span class="sxs-lookup"><span data-stu-id="5be9a-175">Argument</span></span>|<span data-ttu-id="5be9a-176">Описание</span><span class="sxs-lookup"><span data-stu-id="5be9a-176">Description</span></span>|
|-|-|
|<span data-ttu-id="5be9a-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5be9a-177">ProviderName</span></span>|<span data-ttu-id="5be9a-178">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5be9a-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="5be9a-179">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="5be9a-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="5be9a-180">ConnectionString</span></span>|<span data-ttu-id="5be9a-181">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-181">Connection string to connect to the database.</span></span> <span data-ttu-id="5be9a-182">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="5be9a-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="5be9a-183">ConfigName</span></span>|<span data-ttu-id="5be9a-184">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="5be9a-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="5be9a-185">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="5be9a-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="5be9a-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="5be9a-186">CommandType</span></span>|<span data-ttu-id="5be9a-187">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="5be9a-188">Sql</span><span class="sxs-lookup"><span data-stu-id="5be9a-188">Sql</span></span>|<span data-ttu-id="5be9a-189">Выполняемая команда SQL.</span><span class="sxs-lookup"><span data-stu-id="5be9a-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="5be9a-190">Параметры</span><span class="sxs-lookup"><span data-stu-id="5be9a-190">Parameters</span></span>|<span data-ttu-id="5be9a-191">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="5be9a-192">Сопоставитель</span><span class="sxs-lookup"><span data-stu-id="5be9a-192">Mapper</span></span>|<span data-ttu-id="5be9a-193">Функция сопоставления (<xref:System.Func%601><`DbDataReader`, `TResult`>), принимает запись в `DataReader` полученном в результате выполнения запроса и возвращает экземпляр объекта типа `TResult` добавляемый `Result` коллекции.</span><span class="sxs-lookup"><span data-stu-id="5be9a-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="5be9a-194">В этом случае сопоставление совершается на одном шаге выполнения, но декларативное авторство с использованием конструктора невозможно.</span><span class="sxs-lookup"><span data-stu-id="5be9a-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="5be9a-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="5be9a-195">MapperFunc</span></span>|<span data-ttu-id="5be9a-196">Функция сопоставления (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), принимает запись в `DataReader` полученном в результате выполнения запроса и возвращает экземпляр объекта типа `TResult` добавляемый `Result` коллекции.</span><span class="sxs-lookup"><span data-stu-id="5be9a-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="5be9a-197">В этом случае сопоставление совершается в несколько шагов выполнения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="5be9a-198">Для этой функции возможны сериализация в XAML и декларативное авторство (любое существующее действие может участвовать в сопоставлении).</span><span class="sxs-lookup"><span data-stu-id="5be9a-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="5be9a-199">Результат</span><span class="sxs-lookup"><span data-stu-id="5be9a-199">Result</span></span>|<span data-ttu-id="5be9a-200">Список объектов, полученный в результате выполнения запроса и выполнения функции сопоставления для каждой записи в `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="5be9a-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="5be9a-201">DbQueryDataSet</span></span>
 <span data-ttu-id="5be9a-202">Выполняет запрос, который возвращает <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5be9a-203">Этот класс выполняет работу асинхронно.</span><span class="sxs-lookup"><span data-stu-id="5be9a-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="5be9a-204">Он является производным от <xref:System.Activities.AsyncCodeActivity> < `TResult`> и использует его асинхронные возможности.</span><span class="sxs-lookup"><span data-stu-id="5be9a-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="5be9a-205">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="5be9a-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="5be9a-206">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="5be9a-207">После `DbQueryDataSet` выполняется `DataSet` возвращается в `Result out` аргумент (типа `TResult`, который определен в базовом классе <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="5be9a-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="5be9a-208">Аргумент</span><span class="sxs-lookup"><span data-stu-id="5be9a-208">Argument</span></span>|<span data-ttu-id="5be9a-209">Описание</span><span class="sxs-lookup"><span data-stu-id="5be9a-209">Description</span></span>|
|-|-|
|<span data-ttu-id="5be9a-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5be9a-210">ProviderName</span></span>|<span data-ttu-id="5be9a-211">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5be9a-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="5be9a-212">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="5be9a-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="5be9a-213">ConnectionString</span></span>|<span data-ttu-id="5be9a-214">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-214">Connection string to connect to the database.</span></span> <span data-ttu-id="5be9a-215">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="5be9a-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="5be9a-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="5be9a-216">ConfigName</span></span>|<span data-ttu-id="5be9a-217">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="5be9a-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="5be9a-218">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="5be9a-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="5be9a-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="5be9a-219">CommandType</span></span>|<span data-ttu-id="5be9a-220">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="5be9a-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="5be9a-221">Sql</span><span class="sxs-lookup"><span data-stu-id="5be9a-221">Sql</span></span>|<span data-ttu-id="5be9a-222">Выполняемая команда SQL.</span><span class="sxs-lookup"><span data-stu-id="5be9a-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="5be9a-223">Параметры</span><span class="sxs-lookup"><span data-stu-id="5be9a-223">Parameters</span></span>|<span data-ttu-id="5be9a-224">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="5be9a-225">Результат</span><span class="sxs-lookup"><span data-stu-id="5be9a-225">Result</span></span>|<span data-ttu-id="5be9a-226"><xref:System.Data.DataSet>, полученный после выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="5be9a-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="5be9a-227">Настройка сведений о соединении</span><span class="sxs-lookup"><span data-stu-id="5be9a-227">Configuring Connection Information</span></span>
 <span data-ttu-id="5be9a-228">Все DbActivities используют одни и те же параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5be9a-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="5be9a-229">Их можно настроить двумя способами.</span><span class="sxs-lookup"><span data-stu-id="5be9a-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="5be9a-230">`ConnectionString + InvariantName`: Задайте неизменяемое имя и строку подключения для поставщика данных ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5be9a-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

- <span data-ttu-id="5be9a-231">`ConfigName`: Задайте имя раздела конфигурации, содержащий сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="5be9a-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

- <span data-ttu-id="5be9a-232">В действии:</span><span class="sxs-lookup"><span data-stu-id="5be9a-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="5be9a-233">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="5be9a-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="5be9a-234">Инструкции по установке</span><span class="sxs-lookup"><span data-stu-id="5be9a-234">Setup instructions</span></span>
 <span data-ttu-id="5be9a-235">Этот образец использует базу данных.</span><span class="sxs-lookup"><span data-stu-id="5be9a-235">This sample uses a database.</span></span> <span data-ttu-id="5be9a-236">Вместе с образцом предоставляется скрипт установки и загрузки (Setup.cmd).</span><span class="sxs-lookup"><span data-stu-id="5be9a-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="5be9a-237">Этот файл необходимо выполнить из командной строки.</span><span class="sxs-lookup"><span data-stu-id="5be9a-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="5be9a-238">Скрипт Setup.cmd вызывает файл скрипта CreateDb.sql, который содержит команды SQL и выполняет следующие операции.</span><span class="sxs-lookup"><span data-stu-id="5be9a-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="5be9a-239">Создает базу данных под именем DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="5be9a-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="5be9a-240">Создает таблицу Roles.</span><span class="sxs-lookup"><span data-stu-id="5be9a-240">Creates the Roles table.</span></span>

- <span data-ttu-id="5be9a-241">Создает таблицу Employees.</span><span class="sxs-lookup"><span data-stu-id="5be9a-241">Creates Employees table.</span></span>

- <span data-ttu-id="5be9a-242">Вставляет 3 записи в таблицу Roles.</span><span class="sxs-lookup"><span data-stu-id="5be9a-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="5be9a-243">Вставляет двенадцать записей в таблицу Employees.</span><span class="sxs-lookup"><span data-stu-id="5be9a-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="5be9a-244">Запуск команды Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="5be9a-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="5be9a-245">Откройте окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="5be9a-245">Open a command prompt.</span></span>

2. <span data-ttu-id="5be9a-246">Перейдите в папку образца DbActivities.</span><span class="sxs-lookup"><span data-stu-id="5be9a-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="5be9a-247">Введите «setup.cmd» и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="5be9a-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5be9a-248">Скрипт Setup.cmd пытается установить образец базы данных на экземпляр SQLExpress на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="5be9a-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="5be9a-249">Если образец необходимо установить на другом экземпляре сервера SQL, измените Setup.cmd, указав другое имя экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5be9a-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="5be9a-250">Удаление образца базы данных</span><span class="sxs-lookup"><span data-stu-id="5be9a-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="5be9a-251">Выполните в командной строке файл Cleanup.cmd из папки образца.</span><span class="sxs-lookup"><span data-stu-id="5be9a-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="5be9a-252">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="5be9a-252">To run the sample</span></span>

1. <span data-ttu-id="5be9a-253">Откройте решение в Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="5be9a-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="5be9a-254">Для компиляции решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="5be9a-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="5be9a-255">Чтобы запустить образец без отладки, нажмите сочетание клавиш CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="5be9a-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5be9a-256">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5be9a-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5be9a-257">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5be9a-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5be9a-258">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5be9a-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5be9a-259">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5be9a-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
