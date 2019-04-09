---
title: Практическое руководство. Доступ к объектам в раскрывающемся списке элемента управления DataGridViewComboBoxCell в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 221774895fa5867ad6ec870f7e293c9366e442f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080791"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="32a37-102">Практическое руководство. Доступ к объектам в раскрывающемся списке элемента управления DataGridViewComboBoxCell в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32a37-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="32a37-103">Как и <xref:System.Windows.Forms.ComboBox> управления <xref:System.Windows.Forms.DataGridViewComboBoxColumn> и <xref:System.Windows.Forms.DataGridViewComboBoxCell> типов позволяют добавлять произвольные объекты в свой список раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="32a37-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="32a37-104">С помощью этой функции может представлять сложных состояний в раскрывающемся списке без необходимости хранения соответствующих объектов в отдельной коллекции.</span><span class="sxs-lookup"><span data-stu-id="32a37-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="32a37-105">В отличие от <xref:System.Windows.Forms.ComboBox> управления <xref:System.Windows.Forms.DataGridView> типы не имеют <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> свойство для извлечения текущего выбранного объекта.</span><span class="sxs-lookup"><span data-stu-id="32a37-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="32a37-106">Вместо этого необходимо задать <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> или <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> присваивается имя свойства бизнес-объекта.</span><span class="sxs-lookup"><span data-stu-id="32a37-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="32a37-107">Когда пользователь делает выбор, указанное свойство бизнес-объект задает ячейку <xref:System.Windows.Forms.DataGridViewCell.Value%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="32a37-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="32a37-108">Для получения бизнес-объекта до значения ячейки, `ValueMember` свойство необходимо указать свойство, возвращающее ссылку на сам бизнес-объект.</span><span class="sxs-lookup"><span data-stu-id="32a37-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="32a37-109">Таким образом Если тип бизнес-объекта не под вашим управлением, необходимо добавить такое свойство, расширив тип путем наследования.</span><span class="sxs-lookup"><span data-stu-id="32a37-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="32a37-110">Следующие процедуры демонстрируют, как для заполнения раскрывающегося списка с бизнес-объектов и извлечение объектов с помощью ячейки <xref:System.Windows.Forms.DataGridViewCell.Value%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="32a37-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="32a37-111">Чтобы добавить бизнес-объектов в раскрывающемся списке</span><span class="sxs-lookup"><span data-stu-id="32a37-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="32a37-112">Создайте новый <xref:System.Windows.Forms.DataGridViewComboBoxColumn> и заполнить его <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> коллекции.</span><span class="sxs-lookup"><span data-stu-id="32a37-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="32a37-113">Кроме того, можно задать столбец <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> свойство в коллекцию бизнес-объектов.</span><span class="sxs-lookup"><span data-stu-id="32a37-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="32a37-114">В этом случае Однако нельзя добавляемый «неназначенные» стрелку раскрывающегося списка без создания соответствующего бизнес-объект в коллекции.</span><span class="sxs-lookup"><span data-stu-id="32a37-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="32a37-115">Задайте свойства <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> и <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="32a37-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> <span data-ttu-id="32a37-116">Указывает свойство бизнес-объекта для отображения в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="32a37-116">indicates the property of the business object to display in the drop-down list.</span></span> <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> <span data-ttu-id="32a37-117">Указывает свойство, которое возвращает ссылку на бизнес-объект.</span><span class="sxs-lookup"><span data-stu-id="32a37-117">indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="32a37-118">Убедитесь, что ваши бизнес-тип объекта содержит свойство, возвращающее ссылку на текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="32a37-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="32a37-119">Это свойство должно присваиваться с помощью значение, присваиваемое <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="32a37-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="32a37-120">Для извлечения выбранной бизнес-объекта</span><span class="sxs-lookup"><span data-stu-id="32a37-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="32a37-121">Получить ячейку <xref:System.Windows.Forms.DataGridViewCell.Value%2A> свойство и приведите его к типу объекта бизнеса.</span><span class="sxs-lookup"><span data-stu-id="32a37-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="32a37-122">Пример</span><span class="sxs-lookup"><span data-stu-id="32a37-122">Example</span></span>  
 <span data-ttu-id="32a37-123">Полный пример демонстрирует использование бизнес-объектов в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="32a37-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="32a37-124">В примере <xref:System.Windows.Forms.DataGridView> управления привязан к коллекции `Task` объектов.</span><span class="sxs-lookup"><span data-stu-id="32a37-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="32a37-125">Каждый `Task` объект имеет `AssignedTo` свойство, указывающее `Employee` объект, назначенных этой задачи.</span><span class="sxs-lookup"><span data-stu-id="32a37-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="32a37-126">`Assigned To` Столбце отображаются `Name` назначить значение свойства для каждого сотрудника или «неназначенные», если `Task.AssignedTo` свойство имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="32a37-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="32a37-127">Чтобы просмотреть поведение в этом примере, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="32a37-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="32a37-128">Изменение назначений в `Assigned To` столбец, выбрав разные значения из раскрывающихся списков или нажав сочетание клавиш CTRL + 0 в ячейке с раскрывающимся списком.</span><span class="sxs-lookup"><span data-stu-id="32a37-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="32a37-129">Щелкните `Generate Report` для отображения текущих назначений.</span><span class="sxs-lookup"><span data-stu-id="32a37-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="32a37-130">Это показывает, что изменение в `Assigned To` столбца автоматически обновляет `tasks` коллекции.</span><span class="sxs-lookup"><span data-stu-id="32a37-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="32a37-131">Нажмите кнопку `Request Status` кнопку, чтобы вызвать `RequestStatus` метод текущего класса `Employee` объекта для этой строки.</span><span class="sxs-lookup"><span data-stu-id="32a37-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="32a37-132">Это показывает, что выбранный объект был успешно получен.</span><span class="sxs-lookup"><span data-stu-id="32a37-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32a37-133">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="32a37-133">Compiling the Code</span></span>  
 <span data-ttu-id="32a37-134">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="32a37-134">This example requires:</span></span>  
  
-   <span data-ttu-id="32a37-135">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="32a37-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a37-136">См. также</span><span class="sxs-lookup"><span data-stu-id="32a37-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="32a37-137">Отображение данных с помощью элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32a37-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
