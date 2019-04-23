---
title: Пошаговое руководство. Выполнение типичных задач с помощью смарт-тегов в элементах управления Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a93402be30cb461ac6a0ed9daa4a684598a85da1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318251"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="72096-102">Пошаговое руководство. Выполнение типичных задач с помощью смарт-тегов в элементах управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72096-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="72096-103">При создании форм и элементов управления для приложения Windows Forms есть множество задач, которые выполняются несколько раз.</span><span class="sxs-lookup"><span data-stu-id="72096-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="72096-104">Ниже перечислены некоторые наиболее типичных задач, которыми вы столкнетесь:</span><span class="sxs-lookup"><span data-stu-id="72096-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="72096-105">Добавление или удаление вкладки в <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="72096-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="72096-106">Закрепление элемента управления своему родителю.</span><span class="sxs-lookup"><span data-stu-id="72096-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="72096-107">Изменение ориентации элемента <xref:System.Windows.Forms.SplitContainer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="72096-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="72096-108">Для ускорения разработки, многие элементы управления обеспечивают смарт-тегов, которые являются контекстные меню, позволяющие выполнять общие задачи, как они в одном жесте во время разработки.</span><span class="sxs-lookup"><span data-stu-id="72096-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="72096-109">Эти задачи называются *командами смарт тегов*.</span><span class="sxs-lookup"><span data-stu-id="72096-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="72096-110">Смарт-теги остаются прикрепленными к экземпляра элемента управления для существования в конструкторе и всегда доступны.</span><span class="sxs-lookup"><span data-stu-id="72096-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="72096-111">В данном пошаговом руководстве представлены следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="72096-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="72096-112">Создание проекта Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72096-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="72096-113">С помощью смарт-тегов</span><span class="sxs-lookup"><span data-stu-id="72096-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="72096-114">Включение и отключение смарт-тегов</span><span class="sxs-lookup"><span data-stu-id="72096-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="72096-115">После завершения вы будете понимать роль, которую играют эти важные функции макета.</span><span class="sxs-lookup"><span data-stu-id="72096-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72096-116">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="72096-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="72096-117">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="72096-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="72096-118">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="72096-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="72096-119">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="72096-119">Creating the Project</span></span>  
 <span data-ttu-id="72096-120">Первым шагом является создание проекта и настройка формы.</span><span class="sxs-lookup"><span data-stu-id="72096-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="72096-121">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="72096-121">To create the project</span></span>  
  
1. <span data-ttu-id="72096-122">Создайте проект приложения на основе Windows с именем «SmartTagsExample» (**файл** > **New** > **проекта**  >   **Visual C#** или **Visual Basic** > **классический рабочий стол** > **Windows Forms Application**).</span><span class="sxs-lookup"><span data-stu-id="72096-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="72096-123">Выберите форму в **конструктор Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="72096-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="72096-124">С помощью смарт-тегов</span><span class="sxs-lookup"><span data-stu-id="72096-124">Using Smart Tags</span></span>  
 <span data-ttu-id="72096-125">Смарт-тегов постоянную доступность во время разработки для элементов управления, которые содержат их.</span><span class="sxs-lookup"><span data-stu-id="72096-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="72096-126">Использование смарт-тегов</span><span class="sxs-lookup"><span data-stu-id="72096-126">To use smart tags</span></span>  
  
1. <span data-ttu-id="72096-127">Перетащите <xref:System.Windows.Forms.TabControl> из **элементов** на форму.</span><span class="sxs-lookup"><span data-stu-id="72096-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="72096-128">Обратите внимание, глиф смарт тега (![глиф смарт-тега](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), отображаемый на краю <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="72096-128">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2. <span data-ttu-id="72096-129">Щелкните глиф смарт тега.</span><span class="sxs-lookup"><span data-stu-id="72096-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="72096-130">Выберите в контекстном меню, отображаемый рядом с глифом, **добавить вкладку** элемента.</span><span class="sxs-lookup"><span data-stu-id="72096-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="72096-131">Обратите внимание, что новую страницу вкладки добавляется <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="72096-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3. <span data-ttu-id="72096-132">Перетащите элемент управления <xref:System.Windows.Forms.TableLayoutPanel> из **панели элементов** в свою форму.</span><span class="sxs-lookup"><span data-stu-id="72096-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4. <span data-ttu-id="72096-133">Щелкните глиф смарт тега.</span><span class="sxs-lookup"><span data-stu-id="72096-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="72096-134">Выберите в контекстном меню, отображаемый рядом с глифом, **добавить столбец** элемента.</span><span class="sxs-lookup"><span data-stu-id="72096-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="72096-135">Обратите внимание, что новый столбец будет добавлен <xref:System.Windows.Forms.TableLayoutPanel> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="72096-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5. <span data-ttu-id="72096-136">Перетащите элемент управления <xref:System.Windows.Forms.SplitContainer> из **панели элементов** в свою форму.</span><span class="sxs-lookup"><span data-stu-id="72096-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6. <span data-ttu-id="72096-137">Щелкните глиф смарт тега.</span><span class="sxs-lookup"><span data-stu-id="72096-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="72096-138">Выберите в контекстном меню, отображаемый рядом с глифом, **Ориентация горизонтального разделителя** элемента.</span><span class="sxs-lookup"><span data-stu-id="72096-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="72096-139">Обратите внимание, что <xref:System.Windows.Forms.SplitContainer> разделителя элемента управления — теперь горизонтальную ориентацию.</span><span class="sxs-lookup"><span data-stu-id="72096-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72096-140">См. также</span><span class="sxs-lookup"><span data-stu-id="72096-140">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="72096-141">[Пошаговое руководство: Добавление смарт-тегов в компонент Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="72096-141">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
