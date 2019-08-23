---
title: Практическое руководство. Определение клавиш доступа с помощью элементов управления Label в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950538"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="24a4f-102">Практическое руководство. Определение клавиш доступа с помощью элементов управления Label в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24a4f-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="24a4f-103">Элементы <xref:System.Windows.Forms.Label> управления Windows Forms могут использоваться для определения ключей доступа для других элементов управления.</span><span class="sxs-lookup"><span data-stu-id="24a4f-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="24a4f-104">При определении ключа доступа в элементе управления Label пользователь может нажать клавишу ALT плюс символ, который вы указываете, чтобы переместить фокус на элемент управления, следующий за ним в последовательности табуляции.</span><span class="sxs-lookup"><span data-stu-id="24a4f-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="24a4f-105">Поскольку метки не могут получать фокус, фокус автоматически перемещается к следующему элементу управления в последовательности табуляции.</span><span class="sxs-lookup"><span data-stu-id="24a4f-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="24a4f-106">Используйте этот метод, чтобы назначить ключи доступа для текстовых полей, полей со списками, списков и сеток данных.</span><span class="sxs-lookup"><span data-stu-id="24a4f-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="24a4f-107">Назначение клавиши доступа элементу управления с меткой</span><span class="sxs-lookup"><span data-stu-id="24a4f-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="24a4f-108">Сначала нарисуйте метку, а затем нарисуйте другой элемент управления.</span><span class="sxs-lookup"><span data-stu-id="24a4f-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="24a4f-109">-или-</span><span class="sxs-lookup"><span data-stu-id="24a4f-109">-or-</span></span>  
  
     <span data-ttu-id="24a4f-110">Нарисуйте элементы управления в любом порядке и присвойте <xref:System.Windows.Forms.Control.TabIndex%2A> свойству метки значение на единицу меньше другого элемента управления.</span><span class="sxs-lookup"><span data-stu-id="24a4f-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="24a4f-111"><xref:System.Windows.Forms.Label.UseMnemonic%2A> Присвойте`true`свойству метки значение.</span><span class="sxs-lookup"><span data-stu-id="24a4f-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="24a4f-112">Используйте амперсанд (&) в <xref:System.Windows.Forms.Label.Text%2A> свойстве метки, чтобы назначить ключ доступа для метки.</span><span class="sxs-lookup"><span data-stu-id="24a4f-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="24a4f-113">Дополнительные сведения см. в разделе [Создание ключей доступа для элементов управления Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="24a4f-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="24a4f-114">Можно отобразить амперсанды в элементе управления Label, а не использовать их для создания ключей доступа.</span><span class="sxs-lookup"><span data-stu-id="24a4f-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="24a4f-115">Это может произойти при привязке элемента управления Label к полю в наборе записей, где данные содержат амперсанды.</span><span class="sxs-lookup"><span data-stu-id="24a4f-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="24a4f-116">Чтобы отобразить амперсанды в элементе управления Label, задайте <xref:System.Windows.Forms.Label.UseMnemonic%2A> для `false`свойства значение.</span><span class="sxs-lookup"><span data-stu-id="24a4f-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="24a4f-117">Если вы хотите отображать амперсанды, а также ключ доступа, установите <xref:System.Windows.Forms.Label.UseMnemonic%2A> свойство в значение и укажите для `true` ключа доступа один амперсанд (&), а затем амперсанд для отображения с двумя амперсандами.</span><span class="sxs-lookup"><span data-stu-id="24a4f-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="24a4f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="24a4f-118">See also</span></span>

- [<span data-ttu-id="24a4f-119">Практическое руководство. Размер элемента управления метки Windows Forms в соответствии с его содержимым</span><span class="sxs-lookup"><span data-stu-id="24a4f-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="24a4f-120">Общие сведения об элементе управления Label</span><span class="sxs-lookup"><span data-stu-id="24a4f-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="24a4f-121">Элемент управления Label</span><span class="sxs-lookup"><span data-stu-id="24a4f-121">Label Control</span></span>](label-control-windows-forms.md)
