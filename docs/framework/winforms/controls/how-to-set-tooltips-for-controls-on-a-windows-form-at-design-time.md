---
title: Практическое руководство. Определение всплывающих подсказок для элементов управления в Windows Forms во время разработки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: d2bca517e98a8258d4f510c64593de2ad9646e13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157609"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="e8600-102">Практическое руководство. Определение всплывающих подсказок для элементов управления в Windows Forms во время разработки</span><span class="sxs-lookup"><span data-stu-id="e8600-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="e8600-103">Можно задать <xref:System.Windows.Forms.ToolTip> строку в коде или в конструкторе Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e8600-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="e8600-104">Дополнительные сведения о <xref:System.Windows.Forms.ToolTip> компонента, см. в разделе [Общие сведения о компоненте ToolTip](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e8600-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8600-105">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="e8600-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e8600-106">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="e8600-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e8600-107">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e8600-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="e8600-108">Чтобы задать подсказку программным способом</span><span class="sxs-lookup"><span data-stu-id="e8600-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="e8600-109">Добавьте элемент управления, который будет отображаться объект ToolTip.</span><span class="sxs-lookup"><span data-stu-id="e8600-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="e8600-110">Используйте <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> метод <xref:System.Windows.Forms.ToolTip> компонента.</span><span class="sxs-lookup"><span data-stu-id="e8600-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="e8600-111">Для задания подсказки в конструкторе</span><span class="sxs-lookup"><span data-stu-id="e8600-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="e8600-112">Добавьте в форму компонент <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="e8600-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="e8600-113">Выберите элемент управления, который будет отображаться объект ToolTip, или добавьте его в форму.</span><span class="sxs-lookup"><span data-stu-id="e8600-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="e8600-114">В **свойства** окне **во всплывающей подсказке над ToolTip1** значение соответствующую строку текста.</span><span class="sxs-lookup"><span data-stu-id="e8600-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="e8600-115">Чтобы удалить подсказки программными средствами</span><span class="sxs-lookup"><span data-stu-id="e8600-115">To remove a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="e8600-116">Используйте <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> метод <xref:System.Windows.Forms.ToolTip> компонента.</span><span class="sxs-lookup"><span data-stu-id="e8600-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="e8600-117">Чтобы удалить всплывающей подсказки в конструкторе</span><span class="sxs-lookup"><span data-stu-id="e8600-117">To remove a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="e8600-118">Выберите элемент управления, который отображает подсказку.</span><span class="sxs-lookup"><span data-stu-id="e8600-118">Select the control that is displaying the ToolTip.</span></span>  
  
2.  <span data-ttu-id="e8600-119">В **свойства** окно, удалите текст в **во всплывающей подсказке над ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="e8600-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e8600-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e8600-120">See also</span></span>

- [<span data-ttu-id="e8600-121">Общие сведения об элементе управления ToolTip</span><span class="sxs-lookup"><span data-stu-id="e8600-121">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="e8600-122">Практическое руководство. Изменение значения задержки для компонента ToolTip в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8600-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="e8600-123">Компонент ToolTip</span><span class="sxs-lookup"><span data-stu-id="e8600-123">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
