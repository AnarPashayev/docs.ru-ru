---
title: Практическое руководство. Привязка данных к элементу управления DataGridView в форме Windows Forms с помощью конструктора
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 51e18555a322e32f0877167d42cd30776068c746
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040039"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Практическое руководство. Привязка данных к элементу управления DataGridView в форме Windows Forms с помощью конструктора
Конструктор можно использовать для подключения <xref:System.Windows.Forms.DataGridView> элемента управления к источникам данных различных видов, включая базы данных, бизнес-объекты или веб-службы. При привязке элемента управления к источнику данных с помощью конструктора элемент управления автоматически привязывается к <xref:System.Windows.Forms.BindingSource> компоненту, который представляет источник данных. Кроме того, в элементе управления автоматически создаются столбцы для сопоставления данных о схеме, предоставляемых источником данных.

 После этого созданные столбцы можно будет изменить с учетом ваших потребностей. Например, можно удалить или скрыть столбцы, которые вас не интересуют, изменить порядок или типы столбцов. Дополнительные сведения об изменении столбцов см. в разделах, перечисленных в разделе "См. также".

 Можно также привязать несколько <xref:System.Windows.Forms.DataGridView> элементов управления к связанным таблицам для создания связей "основной/подробности". В данной конфигурации один элемент управления отображает родительскую таблицу, а другой — только те строки из дочерней таблицы, которые связаны с текущей строкой в родительской таблице. Дополнительные сведения см. в разделе [Практическое руководство. Отображение связанных данных в приложении](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))Windows Forms.

 Для следующей процедуры требуется проект **приложения Windows** с формой, содержащей <xref:System.Windows.Forms.DataGridView> элемент управления или два элемента управления для связи «основной/подробности». Сведения о запуске такого проекта см. в разделе [как Создайте проект](/visualstudio/ide/step-1-create-a-windows-forms-application-project) приложения Windows Forms и [выполните следующие действия. Добавьте элементы управления в](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-bind-the-control-to-a-data-source"></a>Привязка элемента управления к источнику данных

1. Щелкните глиф смарт-тега (![глиф смарт-тега](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) в правом верхнем <xref:System.Windows.Forms.DataGridView> углу элемента управления.

2. Щелкните стрелку раскрывающегося списка рядом с параметром **Выбор источника данных**.

3. Если у проекта еще нет источника данных, нажмите **Добавить источник данных проекта** и следуйте указаниям мастера.

     Дополнительные сведения см. в разделе [Мастер настройки источника данных](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Новый источник данных появится в раскрывающемся окне **Выбор источника данных**. Если источник данных содержит только один элемент, например только одну таблицу баз данных, элемент управления будет автоматически привязан к этому элементу. В противном случае перейдите к следующему этапу.

4. Разверните узлы **Другие источники данных** и **Источники данных проекта**, если они еще не развернуты, и выберите источник данных, к которому нужно привязать элемент управления.

5. Если источник данных содержит более одного элемента, например, если создан объект <xref:System.Data.DataSet?displayProperty=nameWithType> , содержащий несколько таблиц, разверните источник данных, а затем выберите конкретный элемент для привязки.

6. Чтобы создать отношение "основной/подробности", в раскрывающемся окне **Выбор источника данных** для второго <xref:System.Windows.Forms.DataGridView> элемента управления разверните объект <xref:System.Windows.Forms.BindingSource> , созданный для родительской таблицы, а затем выберите связанную дочернюю таблицу из отображаемого списка.

    > [!NOTE]
    >  Если в вашем проекте уже есть источник данных, форму данных можно также создать в окне **Источники данных**. Дополнительные сведения см. в разделе [Окно источников данных](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Практическое руководство. Подключение к данным в базе данных](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Практическое руководство. Добавление и удаление столбцов в элементе управления Windows Forms DataGridView с помощью конструктора](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Практическое руководство. Изменение порядка столбцов в элементе управления Windows Forms DataGridView с помощью конструктора](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Практическое руководство. Изменение типа Windows Forms столбца DataGridView с помощью конструктора](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Практическое руководство. Закрепление столбцов в элементе управления Windows Forms DataGridView с помощью конструктора](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Практическое руководство. Скрытие столбцов в элементе управления Windows Forms DataGridView с помощью конструктора](hide-columns-in-the-datagrid-using-the-designer.md)
- [Практическое руководство. Сделать столбцы доступны только для чтения в элементе управления Windows Forms DataGridView с помощью конструктора](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Практическое руководство. Создание проекта приложения Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project).
- [Практическое руководство. Добавление элементов управления в Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Окно "источники данных"](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Практическое руководство. Отображение связанных данных в приложении Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
