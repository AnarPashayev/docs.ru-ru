---
title: Практическое руководство. Удаление или скрытие столбцов элемента управления DataGrid в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: e6e8a4a5908d890d34ab6de952917cd97be2b433
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120150"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="90bab-102">Практическое руководство. Удаление или скрытие столбцов элемента управления DataGrid в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90bab-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="90bab-103">Элемент управления <xref:System.Windows.Forms.DataGridView> заменяет элемент управления <xref:System.Windows.Forms.DataGrid> и расширяет его функциональные возможности; однако при необходимости элемент управления <xref:System.Windows.Forms.DataGrid> можно сохранить для обратной совместимости и использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="90bab-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="90bab-104">Дополнительные сведения см. в разделе [Различия элементов управления DataGridView и DataGrid в Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="90bab-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="90bab-105">Можно программно удалить или скрыть столбцы в Windows Forms <xref:System.Windows.Forms.DataGrid> элемента управления с помощью свойств и методов <xref:System.Windows.Forms.GridColumnStylesCollection> и <xref:System.Windows.Forms.DataGridColumnStyle> объектов (которые являются членами <xref:System.Windows.Forms.DataGridTableStyle> класса).</span><span class="sxs-lookup"><span data-stu-id="90bab-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="90bab-106">Удаленные или скрытые столбцы по-прежнему существуют в источнике данных привязывается к сетке и по-прежнему может осуществляться программными средствами.</span><span class="sxs-lookup"><span data-stu-id="90bab-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="90bab-107">Они просто больше не отображается в элементе управления datagrid.</span><span class="sxs-lookup"><span data-stu-id="90bab-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90bab-108">Если приложение не осуществляет доступ к определенным столбцам данных, и нежелательно, чтобы они отображались в сетке данных, то это скорее всего, не обязательно включать их в источнике данных, в первую очередь.</span><span class="sxs-lookup"><span data-stu-id="90bab-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="90bab-109">Чтобы программно удалить столбец из элемента управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="90bab-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="90bab-110">В области объявлений формы объявить новый экземпляр класса <xref:System.Windows.Forms.DataGridTableStyle> класса.</span><span class="sxs-lookup"><span data-stu-id="90bab-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="90bab-111">Задайте <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> свойство к таблице в источнике данных, который вы хотите применить стиль.</span><span class="sxs-lookup"><span data-stu-id="90bab-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="90bab-112">В следующем примере используется <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> свойство, которое предполагается, что уже задан.</span><span class="sxs-lookup"><span data-stu-id="90bab-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="90bab-113">Добавьте новые <xref:System.Windows.Forms.DataGridTableStyle> объект в коллекцию стилей таблиц элемента управления datagrid.</span><span class="sxs-lookup"><span data-stu-id="90bab-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="90bab-114">Вызовите <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> метод <xref:System.Windows.Forms.DataGrid>в <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> коллекции, указав индекс столбца для удаления.</span><span class="sxs-lookup"><span data-stu-id="90bab-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="90bab-115">Чтобы скрыть столбец в сетке данных программными средствами</span><span class="sxs-lookup"><span data-stu-id="90bab-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="90bab-116">В области объявлений формы объявить новый экземпляр класса <xref:System.Windows.Forms.DataGridTableStyle> класса.</span><span class="sxs-lookup"><span data-stu-id="90bab-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="90bab-117">Задайте <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> свойство <xref:System.Windows.Forms.DataGridTableStyle> в таблицу в источнике данных, который вы хотите применить стиль.</span><span class="sxs-lookup"><span data-stu-id="90bab-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="90bab-118">В следующем примере кода используется <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> свойство, которое предполагается, что уже задан.</span><span class="sxs-lookup"><span data-stu-id="90bab-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="90bab-119">Добавьте новые <xref:System.Windows.Forms.DataGridTableStyle> объект в коллекцию стилей таблиц элемента управления datagrid.</span><span class="sxs-lookup"><span data-stu-id="90bab-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="90bab-120">Скрыть столбец, задав его `Width` значение 0, указывающее индекс столбца для столбца.</span><span class="sxs-lookup"><span data-stu-id="90bab-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="90bab-121">См. также</span><span class="sxs-lookup"><span data-stu-id="90bab-121">See also</span></span>

- [<span data-ttu-id="90bab-122">Практическое руководство. Изменение данных, отображаемых во время выполнения, в элементе управления DataGrid в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90bab-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="90bab-123">Практическое руководство. Добавление таблиц и столбцов в элемент управления DataGrid в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90bab-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
