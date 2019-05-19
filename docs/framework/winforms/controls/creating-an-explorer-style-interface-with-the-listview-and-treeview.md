---
title: Пошаговое руководство. Создание интерфейса в стиле проводника с использованием элементов управления ListView и TreeView с помощью конструктора
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 6484e6bfce885c28b943ad9844bfa6fc17889c2b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882235"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="f3a03-102">Пошаговое руководство. Создание интерфейса в стиле проводника с использованием элементов управления ListView и TreeView с помощью конструктора</span><span class="sxs-lookup"><span data-stu-id="f3a03-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="f3a03-103">Одним из преимуществ Visual Studio является возможность создания профессиональных приложений Windows Forms в короткие сроки.</span><span class="sxs-lookup"><span data-stu-id="f3a03-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="f3a03-104">Распространенным сценарием Создание пользовательского интерфейса (UI) с <xref:System.Windows.Forms.ListView> и <xref:System.Windows.Forms.TreeView> элементы управления похож на функцию Windows Explorer операционных систем Windows.</span><span class="sxs-lookup"><span data-stu-id="f3a03-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="f3a03-105">Windows Explorer отображает иерархическую структуру файлов и папок на компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="f3a03-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a03-106">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="f3a03-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f3a03-107">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="f3a03-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f3a03-108">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f3a03-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="f3a03-109">Чтобы создать форму, содержащую элемент управления ListView и TreeView</span><span class="sxs-lookup"><span data-stu-id="f3a03-109">To create the form containing a ListView and TreeView control</span></span>  
  
1. <span data-ttu-id="f3a03-110">В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.</span><span class="sxs-lookup"><span data-stu-id="f3a03-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="f3a03-111">В **новый проект** диалоговом окне сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="f3a03-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="f3a03-112">В категориях, выбрав **Visual Basic** или **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="f3a03-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2. <span data-ttu-id="f3a03-113">В списке шаблонов выберите **приложение Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="f3a03-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="f3a03-114">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f3a03-114">Click **OK**.</span></span> <span data-ttu-id="f3a03-115">Создается новый проект Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3a03-115">A new Windows Forms project is created.</span></span>  
  
4. <span data-ttu-id="f3a03-116">Добавить <xref:System.Windows.Forms.SplitContainer> управления в форму и задайте его <xref:System.Windows.Forms.SplitContainer.Dock%2A> свойства <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="f3a03-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5. <span data-ttu-id="f3a03-117">Добавить <xref:System.Windows.Forms.ImageList> с именем `imageList1` в форму и используйте окно свойств для добавления двух изображений: папки и документа, в указанном порядке.</span><span class="sxs-lookup"><span data-stu-id="f3a03-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6. <span data-ttu-id="f3a03-118">Добавить <xref:System.Windows.Forms.TreeView> управления с именем `treeview1` в форму и расположите его в левой части <xref:System.Windows.Forms.SplitContainer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="f3a03-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="f3a03-119">В окне «Свойства» для `treeView1` выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="f3a03-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1. <span data-ttu-id="f3a03-120">Задайте для свойства <xref:System.Windows.Forms.Control.Dock%2A> значение <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="f3a03-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2. <span data-ttu-id="f3a03-121">Задайте свойству <xref:System.Windows.Forms.TreeView.ImageList%2A> значение `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="f3a03-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>  
  
7. <span data-ttu-id="f3a03-122">Добавить <xref:System.Windows.Forms.ListView> управления с именем `listView1` в форму и разместите его справа от <xref:System.Windows.Forms.SplitContainer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="f3a03-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="f3a03-123">В окне «Свойства» для `listview1` выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="f3a03-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1. <span data-ttu-id="f3a03-124">Задайте для свойства <xref:System.Windows.Forms.Control.Dock%2A> значение <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="f3a03-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2. <span data-ttu-id="f3a03-125">Задайте для свойства <xref:System.Windows.Forms.ListView.View%2A> значение <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="f3a03-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="f3a03-126">Откройте редактор коллекции заголовков столбцов, нажав кнопку с многоточием (![кнопку с многоточием (...) в окне свойств Visual Studio.](./media/visual-studio-ellipsis-button.png)) в <xref:System.Windows.Forms.ListView.Columns%2A> свойство **.**</span><span class="sxs-lookup"><span data-stu-id="f3a03-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="f3a03-127">Добавьте три столбца и задайте их <xref:System.Windows.Forms.ColumnHeader.Text%2A> свойства `Name`, `Type`, и `Last Modified`, соответственно.</span><span class="sxs-lookup"><span data-stu-id="f3a03-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="f3a03-128">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="f3a03-128">Click **OK** to close the dialog box.</span></span>  
  
    4. <span data-ttu-id="f3a03-129">Задайте свойству <xref:System.Windows.Forms.ListView.SmallImageList%2A> значение `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="f3a03-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>  
  
8. <span data-ttu-id="f3a03-130">Реализуйте код для заполнения <xref:System.Windows.Forms.TreeView> с узлов и подузлов.</span><span class="sxs-lookup"><span data-stu-id="f3a03-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="f3a03-131">Добавьте следующий код в `Form1` класса.</span><span class="sxs-lookup"><span data-stu-id="f3a03-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="f3a03-132">Так как предыдущий код использует пространство имен System.IO, добавьте соответствующий или импортировать инструкцию в верхней части формы.</span><span class="sxs-lookup"><span data-stu-id="f3a03-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="f3a03-133">Вызовите метод настройки из предыдущего шага в конструкторе формы или <xref:System.Windows.Forms.Form.Load> метод обработки событий.</span><span class="sxs-lookup"><span data-stu-id="f3a03-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="f3a03-134">Добавьте следующий код в конструктор формы.</span><span class="sxs-lookup"><span data-stu-id="f3a03-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="f3a03-135">Обрабатывать <xref:System.Windows.Forms.TreeView.NodeMouseClick> событие для `treeview1` **,** и реализации кода для заполнения `listview1` содержимое узла, при щелчке узла.</span><span class="sxs-lookup"><span data-stu-id="f3a03-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="f3a03-136">Добавьте следующий код в `Form1` класса.</span><span class="sxs-lookup"><span data-stu-id="f3a03-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="f3a03-137">Если вы используете C#, убедитесь, что у вас есть <xref:System.Windows.Forms.TreeView.NodeMouseClick> событие, связанное со своим методом обработки событий.</span><span class="sxs-lookup"><span data-stu-id="f3a03-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="f3a03-138">Добавьте следующий код в конструктор формы.</span><span class="sxs-lookup"><span data-stu-id="f3a03-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="f3a03-139">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="f3a03-139">Testing the Application</span></span>  
 <span data-ttu-id="f3a03-140">Теперь можно проверить форму, чтобы убедиться, что она правильно работает.</span><span class="sxs-lookup"><span data-stu-id="f3a03-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="f3a03-141">Чтобы проверить форму</span><span class="sxs-lookup"><span data-stu-id="f3a03-141">To test the form</span></span>  
  
- <span data-ttu-id="f3a03-142">Нажмите клавишу F5 для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="f3a03-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="f3a03-143">Вы увидите разбиения форму, содержащую <xref:System.Windows.Forms.TreeView> элемент управления, отображающий каталог проекта на левой стороне, и <xref:System.Windows.Forms.ListView> управления справа от оператора с тремя столбцами.</span><span class="sxs-lookup"><span data-stu-id="f3a03-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="f3a03-144">Вы сможете просматривать <xref:System.Windows.Forms.TreeView> , выбрав узлы каталога и <xref:System.Windows.Forms.ListView> заполняется содержимое выбранного каталога.</span><span class="sxs-lookup"><span data-stu-id="f3a03-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f3a03-145">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="f3a03-145">Next Steps</span></span>  
 <span data-ttu-id="f3a03-146">Это приложение служит примером способом, можно использовать <xref:System.Windows.Forms.TreeView> и <xref:System.Windows.Forms.ListView> вместе элементы управления.</span><span class="sxs-lookup"><span data-stu-id="f3a03-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="f3a03-147">Дополнительные сведения об этих элементах управления см. в разделах:</span><span class="sxs-lookup"><span data-stu-id="f3a03-147">For more information on these controls, see the following topics:</span></span>  
  
- [<span data-ttu-id="f3a03-148">Практическое руководство. Добавление пользовательских данных в элемент управления TreeView или элемент управления ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f3a03-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
- [<span data-ttu-id="f3a03-149">Практическое руководство. Добавление возможностей поиска в элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="f3a03-149">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)  
  
- [<span data-ttu-id="f3a03-150">Практическое руководство. Подключение контекстного меню к узлу элемента управления TreeView</span><span class="sxs-lookup"><span data-stu-id="f3a03-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="f3a03-151">См. также</span><span class="sxs-lookup"><span data-stu-id="f3a03-151">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="f3a03-152">Элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="f3a03-152">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="f3a03-153">Практическое руководство. Добавление и удаление узлов с помощью элемента управления TreeView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a03-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="f3a03-154">Практическое руководство. Добавление и удаление элементов с помощью элемента управления ListView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a03-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f3a03-155">Практическое руководство. Добавить столбцы для элемента управления ListView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a03-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
