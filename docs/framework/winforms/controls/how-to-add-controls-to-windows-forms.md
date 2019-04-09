---
title: Практическое руководство. Добавление элементов управления в формы Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 72b5931a79284a93a4e0fdf3cb2cc3b03157f5f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106487"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="d8631-102">Практическое руководство. Добавление элементов управления в формы Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="d8631-103">Большинство форм разрабатываются путем добавления элементов управления в область формы для определения пользовательского интерфейса (UI).</span><span class="sxs-lookup"><span data-stu-id="d8631-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="d8631-104">Объект *управления* — это компонент на форме, использующийся для отображения сведений или принимают пользовательский ввод.</span><span class="sxs-lookup"><span data-stu-id="d8631-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="d8631-105">Дополнительные сведения об элементах управления см. в разделе [элементов управления Windows Forms](index.md).</span><span class="sxs-lookup"><span data-stu-id="d8631-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8631-106">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="d8631-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d8631-107">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="d8631-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d8631-108">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d8631-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="d8631-109">Для рисования элемента управления в форме</span><span class="sxs-lookup"><span data-stu-id="d8631-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="d8631-110">Откройте форму.</span><span class="sxs-lookup"><span data-stu-id="d8631-110">Open the form.</span></span> <span data-ttu-id="d8631-111">Дополнительные сведения см. в разделе [Как Отображение в конструкторе Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8631-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="d8631-112">В **элементов**, щелкните элемент управления, который вы хотите добавить в форму.</span><span class="sxs-lookup"><span data-stu-id="d8631-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="d8631-113">В области формы нажмите на место желаемого положения верхнего левого угла элемента и перетащите указатель к месту желаемого положения нижнего правого угла элемента.</span><span class="sxs-lookup"><span data-stu-id="d8631-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="d8631-114">Элемент управления добавляется в форму с указанным расположением и размером.</span><span class="sxs-lookup"><span data-stu-id="d8631-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8631-115">Каждый элемент управления имеет определенный размер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d8631-115">Each control has a default size defined.</span></span> <span data-ttu-id="d8631-116">Можно добавить элемент управления на форму с его размером по умолчанию, перетащив его из **панели элементов** на форму.</span><span class="sxs-lookup"><span data-stu-id="d8631-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="d8631-117">Чтобы перетащить элемент управления на форму</span><span class="sxs-lookup"><span data-stu-id="d8631-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="d8631-118">Откройте форму.</span><span class="sxs-lookup"><span data-stu-id="d8631-118">Open the form.</span></span> <span data-ttu-id="d8631-119">Дополнительные сведения см. в разделе [Как Отображение в конструкторе Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8631-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="d8631-120">В **элементов**, щелкните и перетащите его в форму элемент управления.</span><span class="sxs-lookup"><span data-stu-id="d8631-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="d8631-121">Элемент управления будет добавлен на форму в указанном месте с размером по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d8631-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8631-122">Можно дважды щелкнуть элемент управления на **нанели элементов**, чтобы добавить его в левом верхнем углу формы с размером по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d8631-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="d8631-123">Вы можете добавить элементы управления на форму динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d8631-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="d8631-124">В следующем примере кода элемент управления <xref:System.Windows.Forms.TextBox> будет добавлен на форму при нажатии элемента управления <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="d8631-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8631-125">Следующая процедура требует наличия формы с уже расположенным на ней элементом управления **button** — `Button1`.</span><span class="sxs-lookup"><span data-stu-id="d8631-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="d8631-126">Добавление элемента управления в форму программными средствами</span><span class="sxs-lookup"><span data-stu-id="d8631-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="d8631-127">В метод, обрабатывающий событие `Click` кнопки в классе формы, вставьте код, аналогичный приведенному ниже, чтобы создать ссылку на переменную элемента управления, установить его свойство `Location` и добавить элемент управления на форму.</span><span class="sxs-lookup"><span data-stu-id="d8631-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d8631-128">Кроме того, можно добавить код для инициализации других свойств элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d8631-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d8631-129">Создание ссылки на вредоносный элемент `UserControl` может поставить локальный компьютер под угрозу атаки по сети.</span><span class="sxs-lookup"><span data-stu-id="d8631-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="d8631-130">Это может произойти только в том случае, если злоумышленник создаст небезопасный пользовательский элемент управления, а затем вы по ошибке добавите его в проект.</span><span class="sxs-lookup"><span data-stu-id="d8631-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8631-131">См. также</span><span class="sxs-lookup"><span data-stu-id="d8631-131">See also</span></span>

- [<span data-ttu-id="d8631-132">Элементы управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d8631-133">Расположение элементов управления в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d8631-134">Практическое руководство. Изменение размера элементов управления в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="d8631-135">Практическое руководство. Определение текста, отображаемого элементом управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="d8631-136">Элементы управления для использования в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8631-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
