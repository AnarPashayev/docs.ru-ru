---
title: Пошаговое руководство. Применение только хранимых процедур (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 270b0f2123a20787a8e75d40f56a675c55824243
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742566"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="1e210-102">Пошаговое руководство. Применение только хранимых процедур (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e210-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="1e210-103">В данном пошаговом руководстве представлен основной полный сценарий [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для получения доступа к данным с использованием только хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="1e210-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="1e210-104">Этот метод часто используется администраторами баз данных для ограничения способов получения доступа к хранилищам данных.</span><span class="sxs-lookup"><span data-stu-id="1e210-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e210-105">Хранимые процедуры можно также использовать в приложениях [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для переопределения поведения по умолчанию, особенно для процессов `Create`, `Update` и `Delete`.</span><span class="sxs-lookup"><span data-stu-id="1e210-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="1e210-106">Дополнительные сведения см. в разделе [Настройка операций вставки, обновления и удалить](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1e210-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="1e210-107">Для целей данного пошагового руководства будут использованы два метода, которые были сопоставлены с хранимыми процедурами в образце базы данных Northwind: CustOrdersDetail и CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="1e210-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="1e210-108">Сопоставление осуществляется при запуске средства командной строки SqlMetal для создания файла Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e210-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="1e210-109">Дополнительные сведения см. в разделе "Предварительные требования" далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="1e210-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="1e210-110">В этом пошаговом руководстве не зависит от реляционного конструктора объектов.</span><span class="sxs-lookup"><span data-stu-id="1e210-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="1e210-111">Разработчики, использующие Visual Studio также можно использовать конструктор O/R для реализации функций хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="1e210-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="1e210-112">См. в разделе [средства LINQ to SQL в Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="1e210-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1e210-113">Это пошаговое руководство было написано с помощью параметров разработки Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e210-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e210-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="1e210-114">Prerequisites</span></span>  
 <span data-ttu-id="1e210-115">Необходимо выполнить следующие требования.</span><span class="sxs-lookup"><span data-stu-id="1e210-115">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="1e210-116">Для хранения файлов используется выделенная папка ("c:\linqtest3").</span><span class="sxs-lookup"><span data-stu-id="1e210-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="1e210-117">Прежде чем приступить к выполнению задач, создайте такую папку.</span><span class="sxs-lookup"><span data-stu-id="1e210-117">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="1e210-118">Наличие учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="1e210-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="1e210-119">Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1e210-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="1e210-120">Инструкции см. в разделе [Загрузка примеров баз данных](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1e210-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="1e210-121">После загрузки базы данных скопируйте файл northwnd.mdf в папку c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="1e210-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="1e210-122">Наличие файла кода Visual Basic, созданного из базы данных "Борей".</span><span class="sxs-lookup"><span data-stu-id="1e210-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="1e210-123">Данное пошаговое руководство было написано с использованием средства SqlMetal со следующей командной строкой:</span><span class="sxs-lookup"><span data-stu-id="1e210-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="1e210-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="1e210-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="1e210-125">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="1e210-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1e210-126">Обзор</span><span class="sxs-lookup"><span data-stu-id="1e210-126">Overview</span></span>  
 <span data-ttu-id="1e210-127">Данное пошаговое руководство состоит из шести основных задач.</span><span class="sxs-lookup"><span data-stu-id="1e210-127">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="1e210-128">Настройка [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e210-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="1e210-129">Добавление сборки System.Data.Linq в проект.</span><span class="sxs-lookup"><span data-stu-id="1e210-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="1e210-130">Добавление файла кода базы данных в проект.</span><span class="sxs-lookup"><span data-stu-id="1e210-130">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="1e210-131">Создание подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1e210-131">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="1e210-132">Настройка пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1e210-132">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="1e210-133">Запуск и тестирование приложения.</span><span class="sxs-lookup"><span data-stu-id="1e210-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="1e210-134">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e210-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="1e210-135">В первой задаче создается решение Visual Studio, содержащее ссылки, необходимые для построения и запуска [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта.</span><span class="sxs-lookup"><span data-stu-id="1e210-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="1e210-136">Создание решения LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e210-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="1e210-137">В меню **Файл** Visual Studio выберите команду **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="1e210-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="1e210-138">В области **Типы проектов** диалогового окна **Создать проект** разверните узел **Visual Basic**, а затем щелкните **Windows**.</span><span class="sxs-lookup"><span data-stu-id="1e210-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="1e210-139">Выберите **Приложение Windows Forms** в области **Шаблоны**.</span><span class="sxs-lookup"><span data-stu-id="1e210-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="1e210-140">В **имя** введите **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="1e210-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="1e210-141">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="1e210-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="1e210-142">Откроется конструктор Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1e210-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="1e210-143">Добавление ссылки на сборку LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e210-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="1e210-144">Сборка [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не включается в стандартный шаблон приложения Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1e210-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="1e210-145">Сборку необходимо добавить самостоятельно, выполнив приведенные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="1e210-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="1e210-146">Добавление сборки System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="1e210-146">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="1e210-147">В **обозревателе решений**, нажмите кнопку **Показать все файлы**.</span><span class="sxs-lookup"><span data-stu-id="1e210-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="1e210-148">В **обозревателе решений**, щелкните правой кнопкой мыши **ссылки**, а затем нажмите кнопку **добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="1e210-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="1e210-149">В **добавить ссылку** диалоговом окне щелкните **.NET**, выберите сборку System.Data.Linq, затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="1e210-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1e210-150">Сборка будет добавлена в проект.</span><span class="sxs-lookup"><span data-stu-id="1e210-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="1e210-151">Добавление файла кода Northwind в проект</span><span class="sxs-lookup"><span data-stu-id="1e210-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="1e210-152">При выполнении действий этого шага предполагается, что для создания файла кода из учебной базы данных Northwind использовалась программа SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="1e210-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="1e210-153">Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="1e210-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="1e210-154">Добавление файла кода northwind в проект</span><span class="sxs-lookup"><span data-stu-id="1e210-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="1e210-155">На **проекта** меню, щелкните **добавить существующий элемент**.</span><span class="sxs-lookup"><span data-stu-id="1e210-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="1e210-156">В **добавить существующий элемент** переместить c:\linqtest3\northwind.vb диалоговом окне и нажмите кнопку **добавить**.</span><span class="sxs-lookup"><span data-stu-id="1e210-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="1e210-157">Файл northwind.vb будет добавлен в проект.</span><span class="sxs-lookup"><span data-stu-id="1e210-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="1e210-158">Создание подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="1e210-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="1e210-159">На этом этапе определяется подключение к учебной базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="1e210-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="1e210-160">В качестве пути используется "c:\linqtest3\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="1e210-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
### <a name="to-create-the-database-connection"></a><span data-ttu-id="1e210-161">Создание подключения к базе данных</span><span class="sxs-lookup"><span data-stu-id="1e210-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="1e210-162">В **обозревателе решений**, щелкните правой кнопкой мыши **Form1.vb**, а затем нажмите кнопку **Просмотр кода**.</span><span class="sxs-lookup"><span data-stu-id="1e210-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="1e210-163">В редакторе кода откроется `Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="1e210-163">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="1e210-164">В блок кода `Form1` введите следующий код.</span><span class="sxs-lookup"><span data-stu-id="1e210-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="1e210-165">Настройка пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="1e210-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="1e210-166">В этой задаче создается интерфейс, с помощью которого пользователи могут выполнять хранимые процедуры для получения доступа к данным в базе данных.</span><span class="sxs-lookup"><span data-stu-id="1e210-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="1e210-167">В приложении, разрабатываемом с помощью настоящего пошагового руководства, пользователи могут получать доступ к данным в базе данных только с помощью хранимых процедур, внедренных в приложение.</span><span class="sxs-lookup"><span data-stu-id="1e210-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="1e210-168">Настройка пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="1e210-168">To set up the user interface</span></span>  
  
1. <span data-ttu-id="1e210-169">Конструктор вернуться в Windows Forms (**Form1.vb[Design]** ).</span><span class="sxs-lookup"><span data-stu-id="1e210-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="1e210-170">В меню **Вид** выберите пункт **Панель элементов**.</span><span class="sxs-lookup"><span data-stu-id="1e210-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="1e210-171">Откроется панель элементов.</span><span class="sxs-lookup"><span data-stu-id="1e210-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e210-172">Нажмите кнопку **Автоскрытие** вешку, чтобы не закрывайте панели элементов при выполнении оставшихся действий данного раздела.</span><span class="sxs-lookup"><span data-stu-id="1e210-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="1e210-173">Перетащите две кнопки, два текстовых поля и две метки из панели элементов на **Form1**.</span><span class="sxs-lookup"><span data-stu-id="1e210-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="1e210-174">Расположите элементы управления в соответствии с показанным здесь рисунком.</span><span class="sxs-lookup"><span data-stu-id="1e210-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="1e210-175">Разверните **Form1** , чтобы разместить все элементы управления.</span><span class="sxs-lookup"><span data-stu-id="1e210-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="1e210-176">Щелкните правой кнопкой мыши **Label1**, а затем нажмите кнопку **свойства**.</span><span class="sxs-lookup"><span data-stu-id="1e210-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="1e210-177">Изменение **текст** свойства из **Label1** для **введите код заказа:** .</span><span class="sxs-lookup"><span data-stu-id="1e210-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="1e210-178">Таким же образом для **Label2**, изменить **текст** свойства из **Label2** для **введите код клиента:** .</span><span class="sxs-lookup"><span data-stu-id="1e210-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="1e210-179">Таким же образом, изменить **текст** свойство для **Button1** для **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="1e210-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="1e210-180">Изменение **текст** свойство для **Button2** для **История заказа**.</span><span class="sxs-lookup"><span data-stu-id="1e210-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="1e210-181">Расширьте элементы управления "Кнопка", чтобы отображался весь текст.</span><span class="sxs-lookup"><span data-stu-id="1e210-181">Widen the button controls so that all the text is visible.</span></span>  
  
### <a name="to-handle-button-clicks"></a><span data-ttu-id="1e210-182">Обработка нажатий кнопки</span><span class="sxs-lookup"><span data-stu-id="1e210-182">To handle button clicks</span></span>  
  
1. <span data-ttu-id="1e210-183">Дважды щелкните **Order Details** на **Form1** для создания `Button1` обработчик событий и открыть редактор кода.</span><span class="sxs-lookup"><span data-stu-id="1e210-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="1e210-184">Введите в обработчик кнопки `Button1` следующий код:</span><span class="sxs-lookup"><span data-stu-id="1e210-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="1e210-185">Теперь дважды щелкните **Button2** на форме Form1, чтобы создать `Button2` обработчик событий и открыть редактор кода.</span><span class="sxs-lookup"><span data-stu-id="1e210-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="1e210-186">Введите в обработчик кнопки `Button2` следующий код:</span><span class="sxs-lookup"><span data-stu-id="1e210-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="1e210-187">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="1e210-187">Testing the Application</span></span>  
 <span data-ttu-id="1e210-188">Теперь необходимо протестировать приложение.</span><span class="sxs-lookup"><span data-stu-id="1e210-188">Now it is time to test your application.</span></span> <span data-ttu-id="1e210-189">Обратите внимание, что все обращения к хранилищу данных ограничены теми действиями, которые могут выполняться двумя хранимыми процедурами.</span><span class="sxs-lookup"><span data-stu-id="1e210-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="1e210-190">Эти действия заключаются в возвращении продуктов, включенных в заказ с введенным кодом, или истории продуктов, заказанных клиентом с введенным кодом.</span><span class="sxs-lookup"><span data-stu-id="1e210-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="1e210-191">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="1e210-191">To test the application</span></span>  
  
1. <span data-ttu-id="1e210-192">Нажмите клавишу F5, чтобы начать отладку.</span><span class="sxs-lookup"><span data-stu-id="1e210-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="1e210-193">Откроется форма "Form1".</span><span class="sxs-lookup"><span data-stu-id="1e210-193">Form1 appears.</span></span>  
  
2. <span data-ttu-id="1e210-194">В **введите код заказа** введите **10249** и нажмите кнопку **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="1e210-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="1e210-195">В окне сообщения будет отображен список продуктов, включенных в заказ 10249.</span><span class="sxs-lookup"><span data-stu-id="1e210-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="1e210-196">Нажмите кнопку **ОК** чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e210-196">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="1e210-197">В **введите код клиента** введите `ALFKI`, а затем нажмите кнопку **История заказа**.</span><span class="sxs-lookup"><span data-stu-id="1e210-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="1e210-198">Откроется окно сообщения, в котором отображается история заказа для клиента ALFKI.</span><span class="sxs-lookup"><span data-stu-id="1e210-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="1e210-199">Нажмите кнопку **ОК** чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e210-199">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="1e210-200">В **введите код заказа** введите `123`, а затем нажмите кнопку **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="1e210-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="1e210-201">Откроется окно сообщения, в котором отображается текст "Нет результатов".</span><span class="sxs-lookup"><span data-stu-id="1e210-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="1e210-202">Нажмите кнопку **ОК** чтобы закрыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e210-202">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="1e210-203">На **Отладка** меню, щелкните **остановить отладку**.</span><span class="sxs-lookup"><span data-stu-id="1e210-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="1e210-204">Сеанс отладки закрывается.</span><span class="sxs-lookup"><span data-stu-id="1e210-204">The debug session closes.</span></span>  
  
6. <span data-ttu-id="1e210-205">Если проверка завершена, вы можете щелкнуть **закрыть проект** на **файл** меню и сохранить проект при появлении запроса.</span><span class="sxs-lookup"><span data-stu-id="1e210-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1e210-206">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="1e210-206">Next Steps</span></span>  
 <span data-ttu-id="1e210-207">Этот проект можно улучшить, выполнив некоторые изменения.</span><span class="sxs-lookup"><span data-stu-id="1e210-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="1e210-208">Например, можно создать поле со списком доступных хранимых процедур и разрешить пользователю выбирать процедуру для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1e210-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="1e210-209">Можно также записывать выходные данных отчетов в текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="1e210-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e210-210">См. также</span><span class="sxs-lookup"><span data-stu-id="1e210-210">See also</span></span>

- [<span data-ttu-id="1e210-211">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="1e210-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="1e210-212">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="1e210-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
