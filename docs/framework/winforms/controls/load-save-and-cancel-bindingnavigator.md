---
title: Добавление кнопок загрузки, сохранения и отмены в элемент управления BindingNavigator
description: Узнайте, как добавлять кнопки загрузки, сохранения и отмены в Windows Forms элемент управления BindingNavigator.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173423"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="45c6a-103">Практическое руководство. Добавление кнопок загрузки, сохранения и отмены в элемент управления BindingNavigator в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45c6a-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="45c6a-104"><xref:System.Windows.Forms.BindingNavigator>Элемент управления — это специализированный <xref:System.Windows.Forms.ToolStrip> элемент управления, предназначенный для навигации по элементам управления формы, привязанным к данным, и манипулирования ими.</span><span class="sxs-lookup"><span data-stu-id="45c6a-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="45c6a-105">Поскольку это <xref:System.Windows.Forms.ToolStrip> элемент управления, <xref:System.Windows.Forms.BindingNavigator> компонент можно легко изменить, включив в него дополнительные или альтернативные команды для пользователя.</span><span class="sxs-lookup"><span data-stu-id="45c6a-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="45c6a-106">В следующей процедуре <xref:System.Windows.Forms.TextBox> элемент управления привязан к данным, а <xref:System.Windows.Forms.ToolStrip> элемент управления, добавляемый в форму, изменяется для включения кнопок загрузки, сохранения и отмены.</span><span class="sxs-lookup"><span data-stu-id="45c6a-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="45c6a-107">Добавление кнопок загрузки, сохранения и отмены в компонент BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="45c6a-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="45c6a-108">В Visual Studio добавьте в <xref:System.Windows.Forms.TextBox> форму элемент управления.</span><span class="sxs-lookup"><span data-stu-id="45c6a-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="45c6a-109">Привяжите его к <xref:System.Windows.Forms.BindingSource> , который привязан к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="45c6a-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="45c6a-110">В этом примере <xref:System.Windows.Forms.BindingSource> Привязка привязана к базе данных.</span><span class="sxs-lookup"><span data-stu-id="45c6a-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="45c6a-111">После создания набора данных и адаптера таблицы перетащите <xref:System.Windows.Forms.BindingNavigator> элемент управления в форму.</span><span class="sxs-lookup"><span data-stu-id="45c6a-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="45c6a-112">Присвойте <xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> свойству элемента управления значение в <xref:System.Windows.Forms.BindingSource> форме, привязанной к элементам управления.</span><span class="sxs-lookup"><span data-stu-id="45c6a-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="45c6a-113">Выберите элемент управления <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="45c6a-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="45c6a-114">Щелкните глиф действия конструктора ( ![ маленькая черная стрелка ](./media/designer-actions-glyph.gif) ), чтобы появилась диалоговое окно **Задачи BindingNavigator** , и выберите **изменить элементы**.</span><span class="sxs-lookup"><span data-stu-id="45c6a-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="45c6a-115">Откроется **Редактор коллекции элементов** .</span><span class="sxs-lookup"><span data-stu-id="45c6a-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="45c6a-116">В **редакторе коллекции элементов**выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="45c6a-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="45c6a-117">Добавьте <xref:System.Windows.Forms.ToolStripSeparator> и три <xref:System.Windows.Forms.ToolStripButton> элемента, выбрав соответствующий тип <xref:System.Windows.Forms.ToolStripItem> и нажав кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="45c6a-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="45c6a-118">Задайте <xref:System.Windows.Forms.ToolStripItem.Name%2A> для свойств кнопок значение **лоадбуттон**, **савебуттон**и **CancelButton**соответственно.</span><span class="sxs-lookup"><span data-stu-id="45c6a-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="45c6a-119">Задайте <xref:System.Windows.Forms.ToolStripItem.Text%2A> для свойства кнопки значение **Загрузка**, **Сохранение**и **Отмена**.</span><span class="sxs-lookup"><span data-stu-id="45c6a-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="45c6a-120">Присвойте <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> свойству каждой кнопки значение **Text**.</span><span class="sxs-lookup"><span data-stu-id="45c6a-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="45c6a-121">Кроме того, можно задать для этого свойства значение **Image** или **имажеандтекст**и задать отображение изображения в <xref:System.Windows.Forms.ToolStripItem.Image%2A> свойстве.</span><span class="sxs-lookup"><span data-stu-id="45c6a-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="45c6a-122">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="45c6a-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="45c6a-123">Кнопки добавляются в <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="45c6a-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="45c6a-124">Щелкните форму правой кнопкой мыши и выберите команду **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="45c6a-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="45c6a-125">В редакторе кода найдите строку кода, которая загружает данные в адаптер таблицы.</span><span class="sxs-lookup"><span data-stu-id="45c6a-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="45c6a-126">Этот код был создан при настройке привязки данных на шаге 2.</span><span class="sxs-lookup"><span data-stu-id="45c6a-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="45c6a-127">Код должен выглядеть следующим образом: `TableAdapterName.Fill(DataSetName.TableName)` .</span><span class="sxs-lookup"><span data-stu-id="45c6a-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="45c6a-128">Скорее всего, оно будет содержаться в <xref:System.Windows.Forms.Form.Load> событии формы.</span><span class="sxs-lookup"><span data-stu-id="45c6a-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="45c6a-129">Создайте обработчик событий для <xref:System.Windows.Forms.ToolStripItem.Click> события **Load** <xref:System.Windows.Forms.ToolStripButton> ранее созданной нагрузки и переместите в нее этот код загрузки данных.</span><span class="sxs-lookup"><span data-stu-id="45c6a-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="45c6a-130">Теперь ваш код должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="45c6a-130">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="45c6a-131">Создайте обработчик событий для <xref:System.Windows.Forms.ToolStripItem.Click> события **Save** <xref:System.Windows.Forms.ToolStripButton> ранее созданного сохранения и напишите код для обновления данных в таблице, к которой привязан элемент управления.</span><span class="sxs-lookup"><span data-stu-id="45c6a-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="45c6a-132">В некоторых случаях в <xref:System.Windows.Forms.BindingNavigator> компоненте уже есть кнопка **сохранить** , но конструктор Windows Forms не был создан код.</span><span class="sxs-lookup"><span data-stu-id="45c6a-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="45c6a-133">В этом случае можно поместить приведенный выше код в <xref:System.Windows.Forms.ToolStripItem.Click> обработчик событий для этой кнопки, а не создавать совершенно новую кнопку на <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="45c6a-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="45c6a-134">Однако кнопка по умолчанию отключена, поэтому необходимо задать для свойства кнопки значение, чтобы <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> `true` функция кнопки была правильной.</span><span class="sxs-lookup"><span data-stu-id="45c6a-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="45c6a-135">Создайте обработчик событий для <xref:System.Windows.Forms.ToolStripItem.Click> события **отмены** , <xref:System.Windows.Forms.ToolStripButton> созданного ранее, и напишите код, чтобы отменить все изменения, внесенные в отображаемую запись данных.</span><span class="sxs-lookup"><span data-stu-id="45c6a-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="45c6a-136">Метод ограничивается <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> строкой данных.</span><span class="sxs-lookup"><span data-stu-id="45c6a-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="45c6a-137">Сохраните все изменения, внесенные при просмотре отдельной записи, прежде чем переходить к следующей записи.</span><span class="sxs-lookup"><span data-stu-id="45c6a-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="45c6a-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="45c6a-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="45c6a-139">BindingNavigator — элемент управления</span><span class="sxs-lookup"><span data-stu-id="45c6a-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="45c6a-140">Общие сведения о компоненте BindingSource</span><span class="sxs-lookup"><span data-stu-id="45c6a-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
