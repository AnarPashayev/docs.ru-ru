---
title: Практическое руководство. Создание родительских MDI-форм
description: Сведения о создании родительской формы MDI программным путем и с помощью конструктор Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174709"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="5a1e4-103">Практическое руководство. Создание родительских MDI-форм</span><span class="sxs-lookup"><span data-stu-id="5a1e4-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a1e4-104">В этом разделе используется элемент управления <xref:System.Windows.Forms.MainMenu>, который был заменен на элемент управления <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="5a1e4-105">Элемент управления <xref:System.Windows.Forms.MainMenu> сохраняется для обеспечения обратной совместимости и использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5a1e4-106">Сведения о создании родительской MDI-формы с помощью см <xref:System.Windows.Forms.MenuStrip> . [в разделе как создать список окон MDI с помощью MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5a1e4-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="5a1e4-107">Базой для приложения многодокументного интерфейса (MDI) является родительская MDI-форма.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="5a1e4-108">Это форма, содержащая дочерние MDI-окна, которые являются вложенными окнами, когда пользователи взаимодействуют с MDI-приложением.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="5a1e4-109">Создание родительской MDI-формы представляет собой несложный процесс, как с помощью конструктора Windows Forms, так и на программном уровне.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="5a1e4-110">Создание родительской формы MDI во время разработки</span><span class="sxs-lookup"><span data-stu-id="5a1e4-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="5a1e4-111">Создайте проект приложения Windows в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="5a1e4-112">В окне **Свойства** присвойте <xref:System.Windows.Forms.Form.IsMdiContainer%2A> свойству значение **true**.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="5a1e4-113">При этом форма назначается в качестве MDI-контейнера для дочерних окон.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5a1e4-114">При необходимости, при настройке свойств в окне **Свойства** для свойства `WindowState` также можно задать значение **Maximized**, так как управлять дочерними MDI-окнами проще, когда родительская форма развернута.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="5a1e4-115">Кроме того, следует помнить, что граница родительской MDI-формы будет окрашена в системный цвет (заданный на панели управления Windows), а не в черный цвет, заданный с помощью свойства <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="5a1e4-116">Перетащите элемент управления **MenuStrip** из **панели элементов** в форму.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="5a1e4-117">Создайте пункт меню верхнего уровня — для свойства **Text** задайте значение **&File**, пункты меню должны называться **&New** и **&Close**.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="5a1e4-118">Также создайте пункт меню верхнего уровня **&Window**.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="5a1e4-119">Первое меню будет создавать и скрывать пункты меню во время выполнения, а второе меню будет отслеживать открытые дочерние MDI-окна.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="5a1e4-120">На этом этапе вы создали родительское MDI-окно.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="5a1e4-121">Нажмите клавишу **F5** для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="5a1e4-121">Press **F5** to run the application.</span></span> <span data-ttu-id="5a1e4-122">Подробнее о создании дочерних MDI-окон, работающих в родительской MDI-форме, см. в разделе [Практическое руководство. Создание дочерних MDI-форм](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5a1e4-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a1e4-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5a1e4-123">See also</span></span>

- [<span data-ttu-id="5a1e4-124">Приложения с интерфейсом MDI</span><span class="sxs-lookup"><span data-stu-id="5a1e4-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="5a1e4-125">Практическое руководство. Создание дочерних форм MDI</span><span class="sxs-lookup"><span data-stu-id="5a1e4-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="5a1e4-126">Практическое руководство. Определение активной дочерней MDI-формы</span><span class="sxs-lookup"><span data-stu-id="5a1e4-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="5a1e4-127">Практическое руководство. Отправка данных в активную дочернюю MDI-форму</span><span class="sxs-lookup"><span data-stu-id="5a1e4-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="5a1e4-128">Практическое руководство. Упорядочение дочерних MDI-форм</span><span class="sxs-lookup"><span data-stu-id="5a1e4-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
