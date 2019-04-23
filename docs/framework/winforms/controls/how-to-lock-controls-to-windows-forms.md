---
title: Практическое руководство. Прикрепление элементов управления в формах Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac5fbf33564ed2dd1a030132a35b36164f777519
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301702"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="a06ad-102">Практическое руководство. Прикрепление элементов управления в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="a06ad-103">При разработке пользовательского интерфейса (UI) приложения Windows, можно блокировать элементы управления, если они размещены правильно, чтобы случайно не перемещать или изменять их размер, при задании других свойств.</span><span class="sxs-lookup"><span data-stu-id="a06ad-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="a06ad-104">Кроме того можно блокировать и разблокировать все элементы управления в форме, что полезно для форм с большим количеством элементов управления, или вы можете разблокировать отдельные элементы управления.</span><span class="sxs-lookup"><span data-stu-id="a06ad-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="a06ad-105">После размещения всех элементов управления нужное место на форме, закрепить их все во избежание случайного перемещения.</span><span class="sxs-lookup"><span data-stu-id="a06ad-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a06ad-106">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="a06ad-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a06ad-107">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="a06ad-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a06ad-108">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a06ad-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="a06ad-109">Чтобы заблокировать элемент управления</span><span class="sxs-lookup"><span data-stu-id="a06ad-109">To lock a control</span></span>  
  
1. <span data-ttu-id="a06ad-110">В **свойства** окно, нажмите кнопку **Locked** свойство и выберите `true`.</span><span class="sxs-lookup"><span data-stu-id="a06ad-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="a06ad-111">(Дважды щелкните имя переключает значения этого свойства.)</span><span class="sxs-lookup"><span data-stu-id="a06ad-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="a06ad-112">Кроме того, щелкните правой кнопкой мыши элемент управления и выберите **блокировать элементы управления**.</span><span class="sxs-lookup"><span data-stu-id="a06ad-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a06ad-113">Блокировка элементов управления не позволяет их перетащить новый размер или расположение в рабочей области конструирования.</span><span class="sxs-lookup"><span data-stu-id="a06ad-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="a06ad-114">Тем не менее, можно по-прежнему изменить размер или расположение элементов управления с помощью параметра **свойства** окно или в коде.</span><span class="sxs-lookup"><span data-stu-id="a06ad-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="a06ad-115">Чтобы заблокировать все элементы управления в форме</span><span class="sxs-lookup"><span data-stu-id="a06ad-115">To lock all the controls on a form</span></span>  
  
1. <span data-ttu-id="a06ad-116">Из **формат** меню, выберите **блокировать элементы управления**.</span><span class="sxs-lookup"><span data-stu-id="a06ad-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a06ad-117">Эта команда запирает размер формы, так как элемент управления формы.</span><span class="sxs-lookup"><span data-stu-id="a06ad-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="a06ad-118">Чтобы разблокировать все заблокированные элементы управления в форме</span><span class="sxs-lookup"><span data-stu-id="a06ad-118">To unlock all locked controls on a form</span></span>  
  
1. <span data-ttu-id="a06ad-119">Из **формат** меню, выберите **блокировать элементы управления**.</span><span class="sxs-lookup"><span data-stu-id="a06ad-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="a06ad-120">Все ранее заблокированные элементы управления в форме стали разблокирован.</span><span class="sxs-lookup"><span data-stu-id="a06ad-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="a06ad-121">Чтобы разблокировать заблокированные элементы управления по отдельности</span><span class="sxs-lookup"><span data-stu-id="a06ad-121">To unlock locked controls individually</span></span>  
  
1. <span data-ttu-id="a06ad-122">В **свойства** окно, нажмите кнопку **Locked** свойство и выберите `false`.</span><span class="sxs-lookup"><span data-stu-id="a06ad-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="a06ad-123">(Дважды щелкните имя переключает значения этого свойства.)</span><span class="sxs-lookup"><span data-stu-id="a06ad-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06ad-124">См. также</span><span class="sxs-lookup"><span data-stu-id="a06ad-124">See also</span></span>

- [<span data-ttu-id="a06ad-125">Элементы управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-125">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a06ad-126">Упорядочение элементов управления в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-126">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="a06ad-127">Создание меток и назначение сочетаний клавиш для элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="a06ad-128">Элементы управления для использования в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="a06ad-129">Функциональная классификация элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a06ad-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
