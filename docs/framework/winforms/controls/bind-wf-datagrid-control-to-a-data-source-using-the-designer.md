---
title: Практическое руководство. Привязка элемента управления DataGrid в Windows Forms к источнику данных с помощью конструктора
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: fe54c650e1d19f36d681053c7da47e12527c5827
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320890"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="01561-102">Практическое руководство. Привязка элемента управления DataGrid в Windows Forms к источнику данных с помощью конструктора</span><span class="sxs-lookup"><span data-stu-id="01561-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="01561-103">Элемент управления <xref:System.Windows.Forms.DataGridView> заменяет элемент управления <xref:System.Windows.Forms.DataGrid> и расширяет его функциональные возможности; однако при необходимости элемент управления <xref:System.Windows.Forms.DataGrid> можно сохранить для обратной совместимости и использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="01561-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="01561-104">Дополнительные сведения см. в разделе [Различия элементов управления DataGridView и DataGrid в Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="01561-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="01561-105">Windows Forms <xref:System.Windows.Forms.DataGrid> управления разработан специально для отображения сведений из источника данных.</span><span class="sxs-lookup"><span data-stu-id="01561-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="01561-106">Привязка элемента управления во время разработки, установив <xref:System.Windows.Forms.DataGrid.DataSource%2A> и <xref:System.Windows.Forms.DataGrid.DataMember%2A> свойства, или во время выполнения путем вызова <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="01561-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="01561-107">Несмотря на то, что можно отобразить данные из различных источников данных, наиболее обычные параметры являются наборы данных и представления данных.</span><span class="sxs-lookup"><span data-stu-id="01561-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="01561-108">Если источник данных доступен во время разработки, например, если форма содержит экземпляр набора данных или представлении данных — сетки можно привязать к источнику данных во время разработки.</span><span class="sxs-lookup"><span data-stu-id="01561-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="01561-109">Затем можно просмотреть, как будет выглядеть данные в сетке.</span><span class="sxs-lookup"><span data-stu-id="01561-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="01561-110">Можно также программно, привязка сетки во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="01561-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="01561-111">Это полезно в том случае, если вы хотите указать источник данных, на основе сведений, получаемых во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="01561-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="01561-112">Например приложение может позволить пользователю указать имя таблицы для просмотра.</span><span class="sxs-lookup"><span data-stu-id="01561-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="01561-113">Это также в некоторых ситуациях, где источник данных не существует во время разработки.</span><span class="sxs-lookup"><span data-stu-id="01561-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="01561-114">Сюда входят источников данных, таких как массивы, коллекции, нетипизированные наборы данных и модули чтения данных.</span><span class="sxs-lookup"><span data-stu-id="01561-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="01561-115">Следующая процедура требуется **приложения Windows** проекта с формой, содержащей <xref:System.Windows.Forms.DataGrid> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="01561-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="01561-116">Сведения о настройке такого проекта см. в разделе [как: Создайте проект приложения Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) и [как: Добавление элементов управления в Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="01561-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="01561-117">В Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> элемент управления отсутствует в **элементов** по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="01561-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="01561-118">Сведения о его добавлении см. в разделе [как: Добавление элементов на панель инструментов](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="01561-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="01561-119">Кроме того в Visual Studio 2005, вы можете использовать **источников данных** окно для привязки данных во время разработки.</span><span class="sxs-lookup"><span data-stu-id="01561-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="01561-120">Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="01561-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01561-121">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="01561-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="01561-122">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="01561-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="01561-123">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="01561-123">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="01561-124">Чтобы выполнить привязку данных элемента управления DataGrid к одной таблице в конструкторе</span><span class="sxs-lookup"><span data-stu-id="01561-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1. <span data-ttu-id="01561-125">Задайте в качестве <xref:System.Windows.Forms.DataGrid.DataSource%2A> объект, содержащие элементы данных, необходимо выполнить привязку к свойству.</span><span class="sxs-lookup"><span data-stu-id="01561-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2. <span data-ttu-id="01561-126">Если источник данных представляет собой набор данных, задайте <xref:System.Windows.Forms.DataGrid.DataMember%2A> имя таблицы для привязки.</span><span class="sxs-lookup"><span data-stu-id="01561-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3. <span data-ttu-id="01561-127">Если источником данных является набор данных или представление данных, на основе таблицы набора данных, добавьте код в форму для заполнения набора данных.</span><span class="sxs-lookup"><span data-stu-id="01561-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="01561-128">Использовании программы зависит от того, где данные поступают в набор.</span><span class="sxs-lookup"><span data-stu-id="01561-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="01561-129">Если набор данных заполняется непосредственно из базы данных, обычно вызывается `Fill` метод адаптера данных, как показано в следующем примере кода, который заполняет набор данных с именем `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="01561-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4. <span data-ttu-id="01561-130">(Необязательно) Добавьте соответствующую таблицу стилей и столбцов в сетку.</span><span class="sxs-lookup"><span data-stu-id="01561-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="01561-131">Если стили таблиц отсутствуют, вы увидите таблицу с минимальным форматированием и со всеми столбцами видимым.</span><span class="sxs-lookup"><span data-stu-id="01561-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="01561-132">Чтобы выполнить привязку данных элемента управления DataGrid с несколькими таблицами в наборе данных в конструкторе</span><span class="sxs-lookup"><span data-stu-id="01561-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1. <span data-ttu-id="01561-133">Задайте в качестве <xref:System.Windows.Forms.DataGrid.DataSource%2A> объект, содержащие элементы данных, необходимо выполнить привязку к свойству.</span><span class="sxs-lookup"><span data-stu-id="01561-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2. <span data-ttu-id="01561-134">Если набор данных содержит связанные таблицы (то есть, если он содержит объект связи), задайте <xref:System.Windows.Forms.DataGrid.DataMember%2A> имя родительской таблицы.</span><span class="sxs-lookup"><span data-stu-id="01561-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3. <span data-ttu-id="01561-135">Напишите код для заполнения набора данных.</span><span class="sxs-lookup"><span data-stu-id="01561-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01561-136">См. также</span><span class="sxs-lookup"><span data-stu-id="01561-136">See also</span></span>

- [<span data-ttu-id="01561-137">Общие сведения об элементе управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="01561-137">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="01561-138">Практическое руководство. Добавление таблиц и столбцов в элемент управления DataGrid в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01561-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="01561-139">Элемент управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="01561-139">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="01561-140">Привязка данных Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01561-140">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="01561-141">Доступ к данным в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01561-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
