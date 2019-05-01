---
title: Практическое руководство. Создание составных элементов управления
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 8bb630d3fb7e064935440439f2f07816e87c77dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010960"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="e96a8-102">Практическое руководство. Создание составных элементов управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="e96a8-103">Составные элементы управления можно применять различным образом.</span><span class="sxs-lookup"><span data-stu-id="e96a8-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="e96a8-104">Их можно создать как часть проекта приложения рабочего стола Windows и использовать только в формах проекта.</span><span class="sxs-lookup"><span data-stu-id="e96a8-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="e96a8-105">Или их можно создать в проекте библиотеки элементов управления Windows, скомпилировать проект в сборку и использовать элементы управления в других проектах.</span><span class="sxs-lookup"><span data-stu-id="e96a8-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="e96a8-106">Можно даже от них наследовать и использовать визуальное наследование для их быстрой настройки.</span><span class="sxs-lookup"><span data-stu-id="e96a8-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e96a8-107">Если необходимо создать составной элемент управления для использования в Web Forms, см. раздел [Разработка пользовательских серверных элементов управления ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e96a8-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
>   
>  <span data-ttu-id="e96a8-108">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="e96a8-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e96a8-109">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="e96a8-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e96a8-110">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e96a8-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="e96a8-111">Создание составного элемента управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-111">To author a composite control</span></span>  
  
1. <span data-ttu-id="e96a8-112">Откройте новый проект **приложения Windows** с именем `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="e96a8-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2. <span data-ttu-id="e96a8-113">В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-113">On the **Project** menu, click **Add User Control**.</span></span>  
  
3. <span data-ttu-id="e96a8-114">В диалоговом окне **Добавить новый элемент** присвойте файлу класса (файлу VB или CS) имя, которое должен иметь составной элемент управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4. <span data-ttu-id="e96a8-115">Выберите **добавить** кнопку, чтобы создать файл класса для составного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-115">Select the **Add** button to create the class file for the composite control.</span></span>  
  
5. <span data-ttu-id="e96a8-116">Добавьте элементы управления с **панели элементов** на поверхность составного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6. <span data-ttu-id="e96a8-117">Поместите код в соответствующие процедуры для обработки событий, вызываемых составным элементом управления или входящими в его состав элементами управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7. <span data-ttu-id="e96a8-118">Закройте конструктор для составного элемента управления и сохраните файл по запросу.</span><span class="sxs-lookup"><span data-stu-id="e96a8-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8. <span data-ttu-id="e96a8-119">В меню **Сборка** выберите **Собрать решение**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="e96a8-120">Проект необходимо собрать, чтобы пользовательские элементы управления появились на **панели элементов**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="e96a8-121">Для добавления экземпляров элемента управления в `Form1` используйте вкладку **DemoControlHost** на **панели элементов**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="e96a8-122">Разработка библиотеки классов элементов управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-122">To author a control class library</span></span>  
  
1. <span data-ttu-id="e96a8-123">Откройте новый проект **библиотеки элементов управления Windows**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="e96a8-124">По умолчанию проект содержит составной элемент управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-124">By default, the project contains a composite control.</span></span>  
  
2. <span data-ttu-id="e96a8-125">Добавьте элементы управления и код, как описано в предыдущей процедуре.</span><span class="sxs-lookup"><span data-stu-id="e96a8-125">Add controls and code as described in the procedure above.</span></span>  
  
3. <span data-ttu-id="e96a8-126">Выберите элемент управления, который не должны изменять производные классы, и установите для свойства **Модификаторы** этого элемента управления значение **Закрытый**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4. <span data-ttu-id="e96a8-127">Построение библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="e96a8-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="e96a8-128">Наследование от составного элемента управления в библиотеке классов элементов управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-128">To inherit from a composite control in a control class library</span></span>  
  
1. <span data-ttu-id="e96a8-129">В меню **Файл** наведите указатель мыши на **Добавить** и выберите **Новый проект** для добавления нового проекта **приложения Windows** в решение.</span><span class="sxs-lookup"><span data-stu-id="e96a8-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2. <span data-ttu-id="e96a8-130">В **обозревателе решений** щелкните правой кнопкой мыши папку **Ссылки** для нового проекта и выберите **Добавить ссылку**, чтобы открыть диалоговое окно **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3. <span data-ttu-id="e96a8-131">Перейдите на вкладку **Проекты** и дважды щелкните проект библиотеки элементов управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4. <span data-ttu-id="e96a8-132">В меню **Сборка** выберите **Собрать решение**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="e96a8-133">В **обозревателе решений** щелкните правой кнопкой мыши проект библиотеки элементов управления и выберите пункт **Добавить новый элемент** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="e96a8-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6. <span data-ttu-id="e96a8-134">Выберите шаблон **Производный пользовательский элемент управления** в диалоговом окне **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7. <span data-ttu-id="e96a8-135">В диалоговом окне **Выбор компонентов для наследования** дважды щелкните элемент управления, от которого должно производиться наследование.</span><span class="sxs-lookup"><span data-stu-id="e96a8-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="e96a8-136">В ваш проект будет добавлен новый элемент управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-136">A new control is added to your project.</span></span>  
  
8. <span data-ttu-id="e96a8-137">Откройте визуальный конструктор для нового элемента управления и добавьте дополнительные вложенные элементы управления.</span><span class="sxs-lookup"><span data-stu-id="e96a8-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="e96a8-138">Вы увидите вложенные элементы управления, унаследованные от составного элемента управления в библиотеке DLL, и сможете изменить свойства элементов управления, для свойства **Модификаторы** которых установлено значение **Открытый**.</span><span class="sxs-lookup"><span data-stu-id="e96a8-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="e96a8-139">Свойства элемента управления, для свойства **Модификаторы** которого установлено значение **Закрытый**, менять нельзя.</span><span class="sxs-lookup"><span data-stu-id="e96a8-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96a8-140">См. также</span><span class="sxs-lookup"><span data-stu-id="e96a8-140">See also</span></span>

- [<span data-ttu-id="e96a8-141">Пошаговое руководство: Создание составного элемента управления с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e96a8-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="e96a8-142">Пошаговое руководство: Создание составного элемента управления с помощью VisualC#</span><span class="sxs-lookup"><span data-stu-id="e96a8-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="e96a8-143">Пошаговое руководство: Наследование элементов управления Windows Forms с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e96a8-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="e96a8-144">Пошаговое руководство: Наследование элементов управления Windows Forms с помощью VisualC#</span><span class="sxs-lookup"><span data-stu-id="e96a8-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="e96a8-145">Рекомендации относительно типов элементов управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-145">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="e96a8-146">Практическое руководство. Автор элементы управления для форм Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e96a8-146">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="e96a8-147">Разновидности пользовательских элементов управления</span><span class="sxs-lookup"><span data-stu-id="e96a8-147">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
