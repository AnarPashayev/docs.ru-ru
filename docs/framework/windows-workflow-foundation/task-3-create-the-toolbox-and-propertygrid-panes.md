---
title: Задача 3. Создание области элементов и сетки свойств
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 402a25c1cb82c245afa94f58cefc180515622ea9
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275859"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Задача 3. Создание области элементов и сетки свойств

В этой задаче вы создадите панели **элементов** и **PropertyGrid** и добавите их в переразмещенную [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].

Для справки код, который должен находиться в файле MainWindow.xaml.cs после выполнения трех задач в процессе повторного [размещения Конструктор рабочих процессов](rehosting-the-workflow-designer.md) ряд разделов, приведен в конце этого раздела.

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Создание области элементов и ее добавление к сетке.

1. Откройте полученный проект Хостингаппликатион, выполнив процедуру, описанную в разделе [Task 2. Разместите конструктор рабочих процессов @ no__t-0.

2. В области **Обозреватель решений** щелкните правой кнопкой мыши файл *MainWindow. XAML* и выберите **Просмотреть код**.

3. Добавьте метод `GetToolboxControl` в класс `MainWindow`, который создает <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, добавляет новую категорию **панели элементов** на **панель элементов**и назначает этой категории типы действий <xref:System.Activities.Statements.Assign> и <xref:System.Activities.Statements.Sequence>.

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. Добавьте закрытый метод `AddToolbox` в класс `MainWindow`, который помещает **область элементов** в левом столбце сетки.

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. Добавьте вызов метода `AddToolBox` в конструкторе класса `MainWindow()`, как показано в следующем коде:

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. Нажмите клавишу <kbd>F5</kbd> , чтобы создать и запустить решение. Должна отобразиться **панель элементов** , содержащая действия <xref:System.Activities.Statements.Assign> и <xref:System.Activities.Statements.Sequence>.

## <a name="to-create-the-propertygrid"></a>Создание области PropertyGrid

1. В области **Обозреватель решений** щелкните правой кнопкой мыши файл *MainWindow. XAML* и выберите **Просмотреть код**.

2. Добавьте метод `AddPropertyInspector` в класс `MainWindow`, чтобы разместить панель **PropertyGrid** в крайнем правом столбце сетки:

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. Добавьте вызов метода `AddPropertyInspector` в конструкторе класса `MainWindow()`, как показано в следующем коде:

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. Нажмите клавишу <kbd>F5</kbd> , чтобы создать и запустить решение. Все панели **элементов**, конструктор рабочего процесса и области **PropertyGrid** должны отображаться, а при перетаскивании действия <xref:System.Activities.Statements.Assign> или <xref:System.Activities.Statements.Sequence> на холст конструктора сетка свойств должна обновляться в зависимости от выделенного действия.

## <a name="example"></a>Пример

Файл *MainWindow.XAML.CS* теперь должен содержать следующий код:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a>См. также

- [Отдельное размещение конструктора рабочих процессов](rehosting-the-workflow-designer.md)
- @no__t 0Task 1: Создание нового Windows Presentation Foundation приложения @ no__t-0
- @no__t 0Task 2: Размещение конструктор рабочих процессов @ no__t-0
