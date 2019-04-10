---
title: Пошаговое руководство. Простая модель объектов и простой запрос (C#)
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: dc56f1e7886a1a1391d94b512ba5c91ca8c9092a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309463"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="45ff5-102">Пошаговое руководство. Простая модель объектов и простой запрос (C#)</span><span class="sxs-lookup"><span data-stu-id="45ff5-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="45ff5-103">В данном пошаговом руководстве представлен основной и полный сценарий [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] с подробным объяснением выполняемых действий.</span><span class="sxs-lookup"><span data-stu-id="45ff5-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="45ff5-104">В нем создается класс сущностей, который моделирует таблицу Customers в учебной базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="45ff5-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="45ff5-105">После этого создается простой запрос на получение списка клиентов, находящихся в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="45ff5-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="45ff5-106">Данное руководство ориентировано на создание кода, чтобы продемонстрировать основные понятия технологии [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45ff5-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="45ff5-107">Как правило, создание собственной модели объектов выполняется с помощью [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45ff5-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="45ff5-108">Это пошаговое руководство было написано с использованием параметров разработки Visual C#.</span><span class="sxs-lookup"><span data-stu-id="45ff5-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="45ff5-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="45ff5-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="45ff5-110">Для хранения файлов используется выделенная папка ("c:\linqtest5").</span><span class="sxs-lookup"><span data-stu-id="45ff5-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="45ff5-111">Прежде чем приступить к выполнению задач, создайте такую папку.</span><span class="sxs-lookup"><span data-stu-id="45ff5-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="45ff5-112">В данном пошаговом руководстве требуется доступ к учебной базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="45ff5-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="45ff5-113">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="45ff5-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="45ff5-114">Инструкции см. в разделе [Загрузка примеров баз данных](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="45ff5-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="45ff5-115">После загрузки базы данных скопируйте файл в папку c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="45ff5-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="45ff5-116">Обзор</span><span class="sxs-lookup"><span data-stu-id="45ff5-116">Overview</span></span>  
 <span data-ttu-id="45ff5-117">Данное пошаговое руководство состоит из шести основных задач.</span><span class="sxs-lookup"><span data-stu-id="45ff5-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="45ff5-118">Создание [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ff5-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="45ff5-119">Сопоставление класса с таблицей базы данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="45ff5-120">Назначение свойств классу для представления столбцов базы данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="45ff5-121">Указание подключения к базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="45ff5-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="45ff5-122">Создание простого запроса к базе данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="45ff5-123">Выполнение запроса и просмотр результатов.</span><span class="sxs-lookup"><span data-stu-id="45ff5-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="45ff5-124">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="45ff5-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="45ff5-125">В первой задаче создается решение Visual Studio, содержащее ссылки, необходимые для построения и запуска [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта.</span><span class="sxs-lookup"><span data-stu-id="45ff5-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="45ff5-126">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="45ff5-126">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="45ff5-127">В Visual Studio **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **проекта**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="45ff5-128">В **типы проектов** области **новый проект** диалоговом окне щелкните **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="45ff5-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="45ff5-129">В области **Шаблоны** щелкните **Консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="45ff5-130">В **имя** введите **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5. <span data-ttu-id="45ff5-131">В **расположение** убедитесь в том, где будут храниться файлы проекта.</span><span class="sxs-lookup"><span data-stu-id="45ff5-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="45ff5-132">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="45ff5-133">Добавление ссылок и директив LINQ</span><span class="sxs-lookup"><span data-stu-id="45ff5-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="45ff5-134">В этом пошаговом руководстве используются сборки, которые могут быть не установлены по умолчанию в проект.</span><span class="sxs-lookup"><span data-stu-id="45ff5-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="45ff5-135">Если System.Data.Linq не входит в проект в качестве ссылки (разверните **ссылки** узел в **обозревателе решений**), добавьте ее, как описано в следующих шагах.</span><span class="sxs-lookup"><span data-stu-id="45ff5-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="45ff5-136">Добавление сборки System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="45ff5-136">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="45ff5-137">В **обозревателе решений**, щелкните правой кнопкой мыши **ссылки**, а затем нажмите кнопку **добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="45ff5-138">В **добавить ссылку** диалоговом окне щелкните **.NET**, выберите сборку System.Data.Linq, затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="45ff5-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45ff5-139">Сборка будет добавлена в проект.</span><span class="sxs-lookup"><span data-stu-id="45ff5-139">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="45ff5-140">Добавьте следующие директивы в верхней части **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="45ff5-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="45ff5-141">Сопоставление класса с таблицей базы данных</span><span class="sxs-lookup"><span data-stu-id="45ff5-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="45ff5-142">На этом этапе создается класс, который сопоставляется с таблицей базы данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="45ff5-143">Такой класс называется *класс сущностей*.</span><span class="sxs-lookup"><span data-stu-id="45ff5-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="45ff5-144">Обратите внимание, что сопоставление осуществляется простым добавлением атрибута <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="45ff5-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="45ff5-145">Свойство <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> задает имя таблицы в базе данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="45ff5-146">Создание класса сущностей и его сопоставление с таблицей базы данных</span><span class="sxs-lookup"><span data-stu-id="45ff5-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="45ff5-147">Введите или вставьте следующий код в Program.cs непосредственно перед объявлением класса `Program`.</span><span class="sxs-lookup"><span data-stu-id="45ff5-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="45ff5-148">Назначение свойств классу для представления столбцов базы данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="45ff5-149">На этом этапе выполняется несколько задач.</span><span class="sxs-lookup"><span data-stu-id="45ff5-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="45ff5-150">Используется атрибут <xref:System.Data.Linq.Mapping.ColumnAttribute> для назначения классу сущностей свойств `CustomerID` и `City`, представляющих столбцы в таблице базы данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="45ff5-151">Назначается свойство `CustomerID`, представляющее столбец первичного ключа в базе данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="45ff5-152">Назначаются поля `_CustomerID` и `_City` для закрытого хранения.</span><span class="sxs-lookup"><span data-stu-id="45ff5-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="45ff5-153">можно сохранять и извлекать значения напрямую, вместо использования открытых методов доступа, которые могут содержать бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="45ff5-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="45ff5-154">Представление характеристик двух столбцов базы данных</span><span class="sxs-lookup"><span data-stu-id="45ff5-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="45ff5-155">Для класса `Customer` введите или вставьте следующий код в Program.cs в фигурных скобках.</span><span class="sxs-lookup"><span data-stu-id="45ff5-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="45ff5-156">Указание подключения к базе данных Northwind</span><span class="sxs-lookup"><span data-stu-id="45ff5-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="45ff5-157">На этом этапе для установки подключения между основанными на коде структурами данных и самой базой данных используется объект <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="45ff5-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="45ff5-158">Основным каналом, через который извлекаются объекты из базы данных и отправляются изменения, является класс <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="45ff5-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="45ff5-159">Также объявляется объект `Table<Customer>`, который действует как логическая типизированная таблица для запросов к таблице Customers в базе данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="45ff5-160">Эти запросы создаются и выполняются в последующих действиях.</span><span class="sxs-lookup"><span data-stu-id="45ff5-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="45ff5-161">Указание подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="45ff5-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="45ff5-162">Введите или вставьте следующий код в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="45ff5-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="45ff5-163">Обратите внимание, что файл `northwnd.mdf` находится в папке "linqtest5".</span><span class="sxs-lookup"><span data-stu-id="45ff5-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="45ff5-164">Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="45ff5-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="45ff5-165">Создание простого запроса</span><span class="sxs-lookup"><span data-stu-id="45ff5-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="45ff5-166">На этом этапе создается запрос для поиска клиентов из таблицы Customers базы данных, находящихся в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="45ff5-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="45ff5-167">Код запроса, создаваемый на этом шаге, только описывает запрос.</span><span class="sxs-lookup"><span data-stu-id="45ff5-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="45ff5-168">но не выполняет его.</span><span class="sxs-lookup"><span data-stu-id="45ff5-168">It does not execute it.</span></span> <span data-ttu-id="45ff5-169">Этот подход известен как *отложенного выполнения*.</span><span class="sxs-lookup"><span data-stu-id="45ff5-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="45ff5-170">Дополнительные сведения см. в разделе [Введение в запросы LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="45ff5-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="45ff5-171">Можно также записать выходные данные в журнал, чтобы продемонстрировать команды SQL, создаваемые технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45ff5-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="45ff5-172">Возможность ведения журнала (которая использует метод <xref:System.Data.Linq.DataContext.Log%2A>) очень полезна при отладке, а также при проверке того, что команды, отправляемые в базу данных, точно соответствуют запросу.</span><span class="sxs-lookup"><span data-stu-id="45ff5-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="45ff5-173">Создание простого запроса</span><span class="sxs-lookup"><span data-stu-id="45ff5-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="45ff5-174">Введите или вставьте следующий код в метод `Main` после объявления `Table<Customer>`.</span><span class="sxs-lookup"><span data-stu-id="45ff5-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="45ff5-175">Выполнение запроса</span><span class="sxs-lookup"><span data-stu-id="45ff5-175">Executing the Query</span></span>  
 <span data-ttu-id="45ff5-176">На этом шаге производится фактическое выполнение запроса.</span><span class="sxs-lookup"><span data-stu-id="45ff5-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="45ff5-177">Выражения запроса, созданные на предыдущем этапе, не оцениваются до тех пор, пока не понадобятся результаты.</span><span class="sxs-lookup"><span data-stu-id="45ff5-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="45ff5-178">После начала итерации `foreach` выполняется команда SQL для базы данных и материализуются объекты.</span><span class="sxs-lookup"><span data-stu-id="45ff5-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="45ff5-179">Порядок выполнения запроса</span><span class="sxs-lookup"><span data-stu-id="45ff5-179">To execute the query</span></span>  
  
1. <span data-ttu-id="45ff5-180">Введите или вставьте следующий код в конце метода `Main` (после описания запроса).</span><span class="sxs-lookup"><span data-stu-id="45ff5-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="45ff5-181">Нажмите клавишу F5, чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="45ff5-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="45ff5-182">Если приложение создает ошибку времени выполнения, см. в разделе Устранение неполадок [обучения с использованием пошаговых руководств](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="45ff5-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="45ff5-183">В окне консоли отображаются следующие результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="45ff5-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3. <span data-ttu-id="45ff5-184">Чтобы закрыть приложение, в окне консоли нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="45ff5-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="45ff5-185">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="45ff5-185">Next Steps</span></span>  
 <span data-ttu-id="45ff5-186">[Пошаговое руководство: Запросов в связях (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) раздел продолжается, которой заканчивается в этом пошаговом руководстве.</span><span class="sxs-lookup"><span data-stu-id="45ff5-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="45ff5-187">Запросов в связях пошаговом руководстве показано, как [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] выполнять запросы в таблицах, аналогичные *соединения* в реляционной базе данных.</span><span class="sxs-lookup"><span data-stu-id="45ff5-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="45ff5-188">Если требуется выполнить пошаговое руководство "Выполнение запросов в связях", необходимо сохранить решение, созданное в процессе только что завершенного пошагового руководства. Это условие является обязательным.</span><span class="sxs-lookup"><span data-stu-id="45ff5-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ff5-189">См. также</span><span class="sxs-lookup"><span data-stu-id="45ff5-189">See also</span></span>

- [<span data-ttu-id="45ff5-190">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="45ff5-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
