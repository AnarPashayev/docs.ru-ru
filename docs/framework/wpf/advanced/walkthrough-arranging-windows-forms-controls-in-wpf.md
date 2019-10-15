---
title: Пошаговое руководство. Упорядочение элементов управления Windows Forms в WPF
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179438"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Пошаговое руководство. Упорядочение элементов управления Windows Forms в WPF

В этом пошаговом руководстве показано, как использовать функции макета [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] для упорядочения элементов управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] в гибридном приложении.

В данном пошаговом руководстве представлены следующие задачи.

- Создание проекта.
- Использование параметров макета по умолчанию.
- Изменение размеров в зависимости от содержимого.
- Использование абсолютного позиционирования.
- Задание размера явным образом.
- Установка свойств макета.
- Описание ограничений z-порядка.
- Закрепление.
- Задание видимости.
- Размещение нерастягиваемых элементов управления.
- Масштабирование.
- Поворот.
- Задание полей и внутренних полей.
- Использование динамических контейнеров макета.

Полный листинг кода задач, показанных в этом пошаговом руководстве, см. в разделе [Размещение элементов управления Windows Forms в WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).

По завершении вы получите представление о функциях макета [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] в @no__t приложениях на основе -1.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения шагов, описанных в этом руководстве, вам понадобится Visual Studio.

## <a name="creating-the-project"></a>Создание проекта

Чтобы создать и настроить проект, выполните следующие действия.

1. Создайте проект приложения WPF с именем `WpfLayoutHostingWf`.

2. В обозреватель решений добавьте ссылки на следующие сборки:

    - WindowsFormsIntegration
    - System.Windows.Forms.
    - System.Drawing;

3. Дважды щелкните файл *MainWindow. XAML* , чтобы открыть его в представлении XAML.

4. В элемент <xref:System.Windows.Window> добавьте следующее сопоставление пространства имен [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. В элементе <xref:System.Windows.Controls.Grid> задайте для свойства <xref:System.Windows.Controls.Grid.ShowGridLines%2A> значение `true` и определите пять строк и три столбца.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Использование параметров макета по умолчанию

По умолчанию элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> обрабатывает макет для размещенного элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Чтобы использовать параметры макета по умолчанию, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> отображается в <xref:System.Windows.Controls.Canvas>. Размер размещаемого элемента управления зависит от его содержимого, а размер элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost> изменяется в соответствии с размещаемым элементом управления.

## <a name="sizing-to-content"></a>Изменение размеров в зависимости от содержимого

Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> гарантирует, что размещаемый элемент управления будет иметь размер, чтобы правильно отобразить его содержимое.

Чтобы задать размер содержимого, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Два новых элемента управления "Кнопка" имеют размер, чтобы правильно отображать более длинную текстовую строку и больший размер шрифта, а размеры элементов <xref:System.Windows.Forms.Integration.WindowsFormsHost> изменяются в соответствии с размещаемыми элементами управления.

## <a name="using-absolute-positioning"></a>Использование абсолютного позиционирования

Можно использовать абсолютное позиционирование для размещения элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost> в любом месте пользовательского интерфейса.

Чтобы использовать абсолютное позиционирование, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> размещается на 20 пикселях с верхней стороны ячейки сетки и на 20 пикселях слева.

## <a name="specifying-size-explicitly"></a>Задание размера явным образом

Можно указать размер элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost> с помощью свойств <xref:System.Windows.FrameworkElement.Width%2A> и <xref:System.Windows.FrameworkElement.Height%2A>.

Чтобы указать размер явным образом, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> задается размером 50 пикселей в ширину на 70 пикселей высотой, что меньше, чем параметры макета по умолчанию. Содержимое элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] упорядочивается соответствующим образом.

## <a name="setting-layout-properties"></a>Установка свойств макета

Всегда устанавливайте свойства, связанные с макетом, в размещенном элементе управления с помощью свойств элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost>. При установке свойств макета непосредственно для размещаемого элемента управления результат не будет соответствовать ожидаемому.

 Установка свойств, связанных с макетом, для размещенного элемента управления в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] не оказывает никакого влияния.

Чтобы увидеть влияние установки свойств на размещенном элементе управления, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. В **Обозреватель решений**дважды щелкните файл *MainWindow. XAML. vb* или *MainWindow.XAML.CS* , чтобы открыть его в редакторе кода.

3. Скопируйте следующий код в определение класса `MainWindow`:

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его.

5. Нажмите кнопку " **щелкните мне** ". Обработчик событий `button1_Click` задает свойства <xref:System.Windows.Forms.Control.Top%2A> и <xref:System.Windows.Forms.Control.Left%2A> для размещаемого элемента управления. Это приводит к перемещению размещенного элемента управления в элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ведущий элемент занимает то же пространство на экране, но размещаемый элемент управления обрезается. Вместо этого размещаемый элемент управления всегда должен заполнить элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

## <a name="understanding-z-order-limitations"></a>Описание ограничений z-порядка

Видимые элементы <xref:System.Windows.Forms.Integration.WindowsFormsHost> всегда рисуются поверх других элементов WPF, и они не зависят от z-порядка. Чтобы увидеть это поведение z-порядка, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> рисуется над элементом Label.

## <a name="docking"></a>Закрепление

элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> поддерживает закрепление [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Задайте присоединенное свойство <xref:System.Windows.Controls.DockPanel.Dock%2A> для закрепления размещаемого элемента управления в элементе <xref:System.Windows.Controls.DockPanel>.

Чтобы закрепить размещенный элемент управления, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> закреплен на правой стороне элемента <xref:System.Windows.Controls.DockPanel>.

## <a name="setting-visibility"></a>Задание видимости

Можно сделать элемент управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] невидимым или свернуть его, задав свойство <xref:System.Windows.UIElement.Visibility%2A> для элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Если элемент управления невидим, он не отображается, но при этом занимает пространство разметки. Если элемент управления свернут, он не отображается и не занимает пространство разметки.

Чтобы задать видимость размещенного элемента управления, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. В файле *MainWindow. XAML. vb* или *MainWindow.XAML.CS*скопируйте следующий код в определение класса:

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его.

4. Нажмите кнопку, **чтобы сделать невидимую** кнопку, чтобы сделать элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> невидимым.

5. Нажмите кнопку " **щелкните, чтобы свернуть** ", чтобы полностью скрыть элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> из макета. При сворачивании элемента управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] окружающие элементы переупорядочиваются, чтобы занять свое пространство.

## <a name="hosting-a-control-that-does-not-stretch"></a>Размещение нерастягиваемых элементов управления

Некоторые элементы управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] имеют фиксированный размер и не растягиваются для заполнения доступного пространства в макете. Например, элемент управления <xref:System.Windows.Forms.MonthCalendar> отображает месяц в фиксированном пространстве.

Для размещения элемента управления, который не растягивается, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> центрируется в строке сетки, но не растягивается для заполнения доступного пространства. Если окно достаточно велико, можно увидеть два или больше месяцев, отображаемых размещаемым элементом управления <xref:System.Windows.Forms.MonthCalendar>, но они центрируются по строке. Подсистема разметки [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] выравнивает элементы по центру, размер которых не может быть заполнен для заполнения доступного пространства.

## <a name="scaling"></a>Масштабирование

В отличие от элементов WPF, большинство элементов управления Windows Forms не постоянно масштабируемыми. Чтобы обеспечить пользовательское масштабирование, переопределите метод <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.

Чтобы масштабировать размещенный элемент управления с использованием поведения по умолчанию, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Размещаемый элемент управления и его окружающие элементы масштабируются с коэффициентом 0,5. Но шрифт размещаемого элемента управления не масштабируется.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Поворот

В отличие от элементов WPF, Windows Forms элементы управления не поддерживают вращение. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> не поворачивается вместе с другими элементами WPF при применении преобразования поворота. Любое значение вращения, отличное от 180 градусов, вызывает событие <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.

Чтобы увидеть результат вращения в гибридном приложении, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Размещаемый элемент управления не повернут, но его соседние элементы повернуты на угол в 180 градусов. Для отображения элементов может потребоваться изменить размер окна.

## <a name="setting-padding-and-margins"></a>Задание отбивки и внутренних полей

Заполнение и поля в макете [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] похожи на заполнение и поля в [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Просто задайте свойства <xref:System.Windows.Controls.Control.Padding%2A> и <xref:System.Windows.FrameworkElement.Margin%2A> для элемента <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

Чтобы задать заполнение и поля для размещенного элемента управления, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Параметры заполнения и поля применяются к размещаемым элементам управления [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] так же, как и в [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="using-dynamic-layout-containers"></a>Использование динамических контейнеров макета

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] предоставляет два динамических контейнера макета: <xref:System.Windows.Forms.FlowLayoutPanel> и <xref:System.Windows.Forms.TableLayoutPanel>. Эти контейнеры также можно использовать в макетах [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Чтобы использовать динамический контейнер макета, выполните следующие действия.

1. Скопируйте следующий код XAML в элемент <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. В файле *MainWindow. XAML. vb* или *MainWindow.XAML.CS*скопируйте следующий код в определение класса:

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Добавьте вызов метода `InitializeFlowLayoutPanel` в конструкторе:

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Нажмите клавишу <kbd>F5</kbd>, чтобы выполнить сборку приложения и запустить его. Элемент <xref:System.Windows.Forms.Integration.WindowsFormsHost> заполняет <xref:System.Windows.Controls.DockPanel>, а <xref:System.Windows.Forms.FlowLayoutPanel> упорядочивает свои дочерние элементы управления по умолчанию <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Проектирование XAML в Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Вопросы, связанные с макетом элемента WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Пример упорядочивания элементов управления Windows Forms в WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Пошаговое руководство: Размещение Windows Forms составного элемента управления в WPF @ no__t-0
- [Пошаговое руководство: Размещение составного элемента управления WPF в Windows Forms @ no__t-0
