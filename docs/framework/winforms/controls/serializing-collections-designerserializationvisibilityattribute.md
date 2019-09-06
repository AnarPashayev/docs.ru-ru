---
title: Пошаговое руководство. Сериализация коллекций стандартных типов с использованием атрибута DesignerSerializationVisibilityAttribute
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4fd1f1dc0c2c0ad9ae2009ed592e48b8eeaa2783
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373684"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Пошаговое руководство. Сериализация коллекций стандартных типов

Иногда пользовательские элементы управления предоставляют коллекцию в качестве свойства. В этом пошаговом руководстве показано <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> , как использовать класс для управления сериализацией коллекции во время разработки. <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Применение значения к свойству коллекции гарантирует, что свойство будет сериализовано.

Чтобы скопировать код из этого раздела единым блоком, см. раздел [Практическое руководство. Сериализация коллекций стандартных типов с помощью Десигнерсериализатионвисибилитяттрибуте](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Предварительные требования

Для выполнения шагов, описанных в этом руководстве, вам понадобится Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Создание элемента управления с сериализуемой коллекцией

Первым шагом является создание элемента управления с сериализуемой коллекцией в качестве свойства. Содержимое этой коллекции можно изменить с помощью **редактора коллекции**, доступ к которому можно получить из окна **свойства** .

1. В Visual Studio создайте проект библиотеки элементов управления Windows и назовите его **сериализатиондемоконтроллиб**.

2. Переименовать `UserControl1` в `SerializationDemoControl`. Дополнительные сведения см. [в разделе Переименование символа кода с помощью рефакторинга](/visualstudio/ide/reference/rename).

3. В окне **Свойства** присвойте <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> свойству значение **10**.

4. Поместите элемент управления в `SerializationDemoControl`. <xref:System.Windows.Forms.TextBox>

5. Выберите элемент управления <xref:System.Windows.Forms.TextBox>. В окне **Свойства** задайте следующие свойства.

    |Свойство.|Измените на|
    |--------------|---------------|
    |**Multiline**|`true`|
    |**Закрепить**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. В **редакторе кода**объявите поле массива строк с именем `stringsValue` в. `SerializationDemoControl`

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. `Strings` Определите свойство`SerializationDemoControl`для.

   > [!NOTE]
   > <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Значение используется для включения сериализации коллекции.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Нажмите клавишу **F5** , чтобы выполнить сборку проекта и запустить элемент управления в **тестовом контейнере UserControl**.

9. Найдите свойство **Strings** в <xref:System.Windows.Forms.PropertyGrid> **контейнере тестов пользовательских элементов управления**. Выберите свойство **Strings** , а затем нажмите кнопку с многоточием![(...) в окно свойств в Visual Studio](./media/visual-studio-ellipsis-button.png)), чтобы открыть **Редактор коллекции строк**.

10. Введите несколько строк в **редакторе коллекции строк**. Разделите их, нажав клавишу **Ввод** в конце каждой строки. После завершения ввода строк нажмите кнопку **ОК** .

   > [!NOTE]
   > Введенные строки отображаются в <xref:System.Windows.Forms.TextBox>. `SerializationDemoControl`

## <a name="serialize-a-collection-property"></a>Сериализация свойства коллекции

Чтобы проверить поведение сериализации элемента управления, необходимо поместить его в форму и изменить содержимое коллекции с помощью **редактора коллекции**. Состояние сериализованной коллекции можно просмотреть, просмотрев специальный файл конструктора, в который **конструктор Windows Forms** выдает код.

1. Добавьте в решение проект приложения Windows. Задайте для проекта имя `SerializationDemoControlTest`.

2. На **панели элементов**найдите вкладку с именем **компоненты сериализатиондемоконтроллиб**. На этой вкладке можно найти `SerializationDemoControl`. Дополнительные сведения см. в разделе [Пошаговое руководство: Автоматическое заполнение панели элементов пользовательскими компонентами](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. `SerializationDemoControl` Разместите в форме.

4. Найдите свойство в окне **Свойства.** `Strings` Щелкните свойство, а затем нажмите кнопку с многоточием![(...) в окно свойств кнопки Visual Studio.](./media/visual-studio-ellipsis-button.png)), чтобы открыть **Редактор коллекции строк.** `Strings`

5. Введите несколько строк в **редакторе коллекции строк**. Разделите их, нажав клавишу **Ввод** в конце каждой строки. После завершения ввода строк нажмите кнопку **ОК** .

    > [!NOTE]
    > Введенные строки отображаются в <xref:System.Windows.Forms.TextBox>. `SerializationDemoControl`

6. В **обозревателе решений** нажмите кнопку **Показать все файлы**.

7. Откройте узел **Form1** . Под ним находится файл с именем **Form1.Designer.CS** или **Form1. Designer. vb**. Это файл, в который **конструктор Windows Forms** выдает код, представляющий состояние времени разработки формы и ее дочерних элементов управления. Откройте этот файл в **редакторе кода**.

8. Откройте область код, **созданный конструктором форм Windows Forms** , и найдите раздел с меткой **serializationDemoControl1**. Под этой меткой находится код, представляющий сериализованное состояние элемента управления. Строки, введенные на шаге 5, отображаются в назначении для `Strings` свойства. В следующих примерах кода C# в и Visual Basic показан код, аналогичный тому, что вы видите при вводе строк "Red", "оранжевый" и "желтый".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. В **редакторе кода**измените значение <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` свойства <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>на.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Перестройте решение и повторите шаги 3 и 4.

> [!NOTE]
> В этом случае **конструктор Windows Forms** не выдает никакого назначения `Strings` свойству.

## <a name="next-steps"></a>Следующие шаги

Когда вы узнаете, как сериализовать коллекцию стандартных типов, рассмотрите возможность интеграции пользовательских элементов управления более глубоко в среду времени разработки. В следующих разделах описывается, как улучшить интеграцию пользовательских элементов управления во время разработки:

- [Архитектура времени разработки](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Атрибуты в элементах управления Windows Forms](attributes-in-windows-forms-controls.md)

- [Общие сведения о сериализации конструктора](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Пошаговое руководство: Создание элемента управления Windows Forms, который использует преимущества функций времени разработки Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>См. также

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Пошаговое руководство: Автоматическое заполнение панели элементов пользовательскими компонентами](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
