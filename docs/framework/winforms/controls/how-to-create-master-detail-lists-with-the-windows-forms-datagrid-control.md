---
title: Практическое руководство. Создание списков «основной/подробности» с помощью элемента управления Windows Forms DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914755"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="01e9c-102">Практическое руководство. Создание основных или подробных списков с помощью элемента управления DataGrid в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01e9c-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="01e9c-103">Элемент управления <xref:System.Windows.Forms.DataGridView> заменяет элемент управления <xref:System.Windows.Forms.DataGrid> и расширяет его функциональные возможности; однако при необходимости элемент управления <xref:System.Windows.Forms.DataGrid> можно сохранить для обратной совместимости и использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="01e9c-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="01e9c-104">Дополнительные сведения см. в разделе [Различия элементов управления DataGridView и DataGrid в Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="01e9c-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="01e9c-105">Если содержит ряд связанных таблиц, можно использовать два <xref:System.Windows.Forms.DataGrid> элемента управления для отображения данных в формате "основной/подробности". <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="01e9c-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="01e9c-106">Один <xref:System.Windows.Forms.DataGrid> из них обозначен как Главная сетка, а второй — сеткой сведений.</span><span class="sxs-lookup"><span data-stu-id="01e9c-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="01e9c-107">При выборе записи в главном списке все связанные дочерние записи отображаются в списке подробностей.</span><span class="sxs-lookup"><span data-stu-id="01e9c-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="01e9c-108">Например, если <xref:System.Data.DataSet> содержит таблицу Customers и связанную таблицу Orders, можно указать таблицу Customers, которая будет главной сеткой, а таблица Orders — сетку сведений.</span><span class="sxs-lookup"><span data-stu-id="01e9c-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="01e9c-109">При выборе клиента из главной сетки все заказы, связанные с этим клиентом в таблице Orders, будут отображаться в сетке сведений.</span><span class="sxs-lookup"><span data-stu-id="01e9c-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="01e9c-110">Настройка связи «основной/подробности» программным способом</span><span class="sxs-lookup"><span data-stu-id="01e9c-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="01e9c-111">Создайте два новых <xref:System.Windows.Forms.DataGrid> элемента управления и задайте их свойства.</span><span class="sxs-lookup"><span data-stu-id="01e9c-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="01e9c-112">Добавьте таблицы в набор данных.</span><span class="sxs-lookup"><span data-stu-id="01e9c-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="01e9c-113">Объявите переменную типа <xref:System.Data.DataRelation> для представления отношения, которое необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="01e9c-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="01e9c-114">Создайте экземпляр связи, указав имя связи и указав таблицу, столбец и элемент, которые будут связывать две таблицы.</span><span class="sxs-lookup"><span data-stu-id="01e9c-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="01e9c-115">Добавьте связь в <xref:System.Data.DataSet> <xref:System.Data.DataSet.Relations%2A> коллекцию объекта.</span><span class="sxs-lookup"><span data-stu-id="01e9c-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="01e9c-116">Используйте метод класса, <xref:System.Windows.Forms.DataGrid> чтобы привязать каждую сетку к <xref:System.Data.DataSet>. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A></span><span class="sxs-lookup"><span data-stu-id="01e9c-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="01e9c-117">В следующем примере показано, как задать связь «основной/подробности» между таблицами Customers и Orders в <xref:System.Data.DataSet> ранее`ds`созданной ().</span><span class="sxs-lookup"><span data-stu-id="01e9c-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="01e9c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="01e9c-118">See also</span></span>

- [<span data-ttu-id="01e9c-119">Элемент управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="01e9c-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="01e9c-120">Общие сведения об элементе управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="01e9c-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="01e9c-121">Практическое руководство. Привязка Windows Forms элемента управления DataGrid к источнику данных</span><span class="sxs-lookup"><span data-stu-id="01e9c-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
