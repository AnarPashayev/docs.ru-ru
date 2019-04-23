---
title: Практическое руководство. Запрос к базе данных с помощью LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: 3fa4434ed43e41959d6ebd3521bb1eecd041c9ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326116"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="75018-102">Практическое руководство. Запрос к базе данных с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75018-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="75018-103">Language-Integrated Query (LINQ) позволяет легко получить доступ к информации базы данных и выполнения запросов.</span><span class="sxs-lookup"><span data-stu-id="75018-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="75018-104">В следующем примере показано, как создать новое приложение, которое выполняет запросы к базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75018-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="75018-105">В примерах в этом разделе используется образец базы данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="75018-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="75018-106">Если у вас нет этой базы данных на компьютере разработчика, его можно загрузить из центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="75018-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="75018-107">Инструкции см. в разделе [Загрузка примеров баз данных](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="75018-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="75018-108">Чтобы создать подключение к базе данных</span><span class="sxs-lookup"><span data-stu-id="75018-108">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="75018-109">В Visual Studio откройте **обозревателя серверов**/**обозреватель баз данных** , щелкнув **обозревателя серверов**/**базы данных Обозреватель** на **представление** меню.</span><span class="sxs-lookup"><span data-stu-id="75018-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="75018-110">Щелкните правой кнопкой мыши **подключения к данным** в **обозревателя серверов**/**обозреватель баз данных** и нажмите кнопку **добавить подключение**.</span><span class="sxs-lookup"><span data-stu-id="75018-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="75018-111">Укажите допустимое соединение с образцом базы данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="75018-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="75018-112">Чтобы добавить в проект, содержащий файл классов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="75018-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="75018-113">В меню **Файл** окна Visual Studio наведите указатель мыши на пункт **Создать** и щелкните **Проект**.</span><span class="sxs-lookup"><span data-stu-id="75018-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="75018-114">Выберите Visual Basic **приложение Windows Forms** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="75018-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="75018-115">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="75018-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="75018-116">Выберите **LINQ to SQL Classes** шаблона элемента.</span><span class="sxs-lookup"><span data-stu-id="75018-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="75018-117">Назовите файл `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="75018-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="75018-118">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="75018-118">Click **Add**.</span></span> <span data-ttu-id="75018-119">Для файла northwind.dbml открывается реляционный конструктор объектов (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="75018-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="75018-120">Добавление таблицы к запросу в конструкторе O/R</span><span class="sxs-lookup"><span data-stu-id="75018-120">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="75018-121">В **обозревателя серверов**/**обозреватель баз данных**, разверните подключение к базе данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="75018-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="75018-122">Разверните **таблиц** папки.</span><span class="sxs-lookup"><span data-stu-id="75018-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="75018-123">Если вы уже закрыли конструктор O/R, его можно открыть, дважды щелкнув файл northwind.dbml, который был добавлен ранее.</span><span class="sxs-lookup"><span data-stu-id="75018-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="75018-124">Щелкните таблицу Customers и перетащите его в левую область конструктора.</span><span class="sxs-lookup"><span data-stu-id="75018-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="75018-125">Щелкните в таблице Orders и перетащите его в левую область конструктора.</span><span class="sxs-lookup"><span data-stu-id="75018-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="75018-126">Конструктор создает новый `Customer` и `Order` объектов для проекта.</span><span class="sxs-lookup"><span data-stu-id="75018-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="75018-127">Обратите внимание на то, что конструктор автоматически обнаруживает связи между таблицами и создает дочерние свойства для связанных объектов.</span><span class="sxs-lookup"><span data-stu-id="75018-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="75018-128">Например, IntelliSense покажет, что `Customer` объект имеет `Orders` свойство для всех заказов, связанных с клиентом.</span><span class="sxs-lookup"><span data-stu-id="75018-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="75018-129">Сохраните изменения и закройте конструктор.</span><span class="sxs-lookup"><span data-stu-id="75018-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="75018-130">Сохраните проект.</span><span class="sxs-lookup"><span data-stu-id="75018-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="75018-131">Добавление кода для запроса к базе данных и отображения результатов</span><span class="sxs-lookup"><span data-stu-id="75018-131">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="75018-132">Из **элементов**, перетащите <xref:System.Windows.Forms.DataGridView> элемента управления на форме Windows по умолчанию для проекта, Form1.</span><span class="sxs-lookup"><span data-stu-id="75018-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="75018-133">Дважды щелкните файл Form1, чтобы добавить код для `Load` событий формы.</span><span class="sxs-lookup"><span data-stu-id="75018-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="75018-134">При добавлении таблиц в конструктор O/R designer добавлены <xref:System.Data.Linq.DataContext> объект для проекта.</span><span class="sxs-lookup"><span data-stu-id="75018-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="75018-135">Этот объект содержит код, который должен иметь доступ к этим таблицам, в дополнение к отдельным объектам и коллекциям для каждой таблицы.</span><span class="sxs-lookup"><span data-stu-id="75018-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="75018-136"><xref:System.Data.Linq.DataContext> Объектов для проекта имя на основе имени файла .dbml.</span><span class="sxs-lookup"><span data-stu-id="75018-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="75018-137">Для этого проекта <xref:System.Data.Linq.DataContext> объект называется `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="75018-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="75018-138">Можно создать экземпляр <xref:System.Data.Linq.DataContext> в коде и запрос таблицы, указанные в конструкторе O/R.</span><span class="sxs-lookup"><span data-stu-id="75018-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="75018-139">Добавьте следующий код, чтобы `Load` событий для запроса к таблицам, которые представляются как свойства контекста данных.</span><span class="sxs-lookup"><span data-stu-id="75018-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#3)]  
  
4. <span data-ttu-id="75018-140">Нажмите клавишу F5, чтобы запустить проект и просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="75018-140">Press F5 to run your project and view the results.</span></span>  
  
5. <span data-ttu-id="75018-141">Ниже приведены некоторые дополнительные запросы, которые могут помочь.</span><span class="sxs-lookup"><span data-stu-id="75018-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="75018-142">См. также</span><span class="sxs-lookup"><span data-stu-id="75018-142">See also</span></span>

- [<span data-ttu-id="75018-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="75018-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="75018-144">Запросы</span><span class="sxs-lookup"><span data-stu-id="75018-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="75018-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="75018-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="75018-146">Методы DataContext (реляционный конструктор объектов)</span><span class="sxs-lookup"><span data-stu-id="75018-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
