---
title: Практическое руководство. Наследование класса Control
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 14f225f5587379b3efa7b6dc2475f1b697ebb281
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941145"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="9e428-102">Практическое руководство. Наследование класса Control</span><span class="sxs-lookup"><span data-stu-id="9e428-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="9e428-103">Если вы хотите создать полностью пользовательский элемент управления для использования в Windows Forms, следует наследовать <xref:System.Windows.Forms.Control> класса.</span><span class="sxs-lookup"><span data-stu-id="9e428-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="9e428-104">При наследовании <xref:System.Windows.Forms.Control> класса необходимо, чтобы выполнить более тщательного планирования и реализации также предоставляет широкий выбор вариантов.</span><span class="sxs-lookup"><span data-stu-id="9e428-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="9e428-105">При наследовании от <xref:System.Windows.Forms.Control>, наследуются простейшие функции, обеспечивающие работоспособность элементов управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="9e428-106">Стандартные функции <xref:System.Windows.Forms.Control> класс обрабатывает входные данные с клавиатуры и мыши, определяют границы и размер элемента управления, обрабатывают окна и обеспечивают обработку сообщений и безопасность.</span><span class="sxs-lookup"><span data-stu-id="9e428-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="9e428-107">Они не включают оформление (в данном случае отрисовку графического интерфейса элемента управления) или конкретные функции взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="9e428-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="9e428-108">Все эти аспекты необходимо прописывать в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="9e428-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e428-109">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="9e428-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9e428-110">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="9e428-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9e428-111">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9e428-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="9e428-112">Создание пользовательского элемента управления</span><span class="sxs-lookup"><span data-stu-id="9e428-112">To create a custom control</span></span>  
  
1. <span data-ttu-id="9e428-113">Создайте проект **приложения Windows** или **библиотеки элементов управления Windows**.</span><span class="sxs-lookup"><span data-stu-id="9e428-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2. <span data-ttu-id="9e428-114">В меню **Проект** выберите команду **Добавить класс**.</span><span class="sxs-lookup"><span data-stu-id="9e428-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3. <span data-ttu-id="9e428-115">В диалоговом окне **Добавление нового элемента** щелкните пункт **Пользовательский элемент управления**.</span><span class="sxs-lookup"><span data-stu-id="9e428-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="9e428-116">В ваш проект будет добавлен новый пользовательский элемент управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-116">A new custom control is added to your project.</span></span>  
  
4. <span data-ttu-id="9e428-117">Нажмите клавишу F7, чтобы открыть **редактор кода** для пользовательского элемента управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5. <span data-ttu-id="9e428-118">Найдите <xref:System.Windows.Forms.Control.OnPaint%2A> метод, который будет содержать только вызов <xref:System.Windows.Forms.Control.OnPaint%2A> метод базового класса.</span><span class="sxs-lookup"><span data-stu-id="9e428-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6. <span data-ttu-id="9e428-119">Измените код, добавив в него пользовательское оформление вашего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="9e428-120">Сведения о написании кода для отрисовки графического интерфейса элементов управления см. в разделе [Рисование и отрисовка пользовательского элемента управления](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="9e428-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
7. <span data-ttu-id="9e428-121">Реализуйте необходимые пользовательские методы, свойства или события, которые будут входить в ваш элемент управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8. <span data-ttu-id="9e428-122">Сохраните и проверьте элемент управления.</span><span class="sxs-lookup"><span data-stu-id="9e428-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e428-123">См. также</span><span class="sxs-lookup"><span data-stu-id="9e428-123">See also</span></span>

- [<span data-ttu-id="9e428-124">Разновидности пользовательских элементов управления</span><span class="sxs-lookup"><span data-stu-id="9e428-124">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="9e428-125">Практическое руководство. Наследование класса UserControl</span><span class="sxs-lookup"><span data-stu-id="9e428-125">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="9e428-126">Практическое руководство. Наследование Windows существующих элементов управления формы</span><span class="sxs-lookup"><span data-stu-id="9e428-126">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="9e428-127">Практическое руководство. Автор элементы управления для форм Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e428-127">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="9e428-128">Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e428-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="9e428-129">Создание элементов управления Windows Forms во время разработки</span><span class="sxs-lookup"><span data-stu-id="9e428-129">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
