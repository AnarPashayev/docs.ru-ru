---
title: Поддержка автоматизированного пользовательского интерфейса для типа элемента управления DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 9bf036271652f8056b79f4c5e389347cd09989e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161035"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Поддержка автоматизированного пользовательского интерфейса для типа элемента управления DataGrid
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 В этом разделе содержатся сведения о поддержке в [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] типа элемента управления DataGrid. В [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]тип элемента управления — это набор условий, которым должен удовлетворять элемент управления для использования свойства `ControlType` . Условия включают конкретные правила для древовидной структуры [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значений свойств [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] и шаблонов элементов управления.  
  
 С помощью типа элемента управления DataGrid пользователь может легко работать с элементами, содержащими метаданные, представленные в столбцах. Элементы управления DataGrid имеют строки элементов и столбцы сведений об этих элементах. Элемент управления ListView в проводнике Microsoft Vista — пример элемента управления, поддерживающего тип DataGrid.  
  
 В следующих разделах описывается необходимая древовидная структура [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , свойства, шаблоны элементов управления и события для типа элемента управления DataGrid. Требования [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] применяются ко всем элементам управления DataGrid, будь это [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]или [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Требуемая древовидная структура модели автоматизации пользовательского интерфейса  
 В следующей таблице описывается представление элемента управления и представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , относящиеся к элементам управления DataGrid, и показывается, что может содержаться в каждом представлении. Дополнительные сведения о дереве [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] см. в разделе [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Дерево - представление элемента управления|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Дерево - представление содержимого|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Заголовок {0, 1 или 2}<br /><br /> <ul><li>HeaderItem (количество столбцов или строк)</li></ul></li><li>DataItem (0 и более; возможна иерархическая структуризация)</li></ul>|DataGrid<br /><br /> -DataItem (0 или больше; могут быть структурированы в иерархии)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Требуемые свойства модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены свойства, значение или определение которых в первую очередь относится к элементам управления DataGrid. Дополнительные сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] свойства, см. в разделе [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Свойство|Значение|Примечания|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|См. примечания.|Значение этого свойства должно быть уникальным среди всех элементов управления в приложении.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|См. примечания.|Внешний прямоугольник, содержащий весь элемент управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|См. примечания.|Поддерживается при наличии ограничивающего прямоугольника. Если не все точки внутри ограничивающего прямоугольника являются интерактивными и выполняется специализированная проверка на наличие данных, выполните переопределение и предоставьте интерактивную точку.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Это значение является одинаковым для всех инфраструктур пользовательского интерфейса.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Это свойство всегда должно иметь значение True. Это означает, что элемент управления DataGrid всегда должен быть в представлении содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Это свойство всегда должно иметь значение True. Это означает, что элемент управления DataGrid всегда должен быть в представлении элемента управления дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|См. примечания.|Если элемент управления может получать фокус клавиатуры, он должен поддерживать это свойство.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|См. примечания.|Если имеется статическая текстовая метка, то данное свойство должно предоставлять ссылку на этот элемент управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"сетка данных"|Локализованная строка, соответствующая типу элемента управления DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|См. примечания.|Элемент управления DataGrid обычно получает значение для своего свойства `Name` из статического текста метки. Если статическая текстовая метка не предусмотрена, разработчик приложения должен назначить значение свойству `Name` . Значение свойства `Name` никогда не должно быть текстовым содержимым элемента управления "Поле ввода".|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Необходимые шаблоны элементов управления модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены шаблоны элементов управления, которые должны поддерживаться всеми элементами управления DataGrid. Дополнительные сведения о шаблонах элементов управления см. в разделе [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Шаблон элемента управления|Поддержка|Примечания|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Да|Сам элемент управления DataGrid всегда поддерживает шаблон элемента управления Grid, поскольку содержит метаданные, которые располагаются в сетке.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Зависит от обстоятельств|Возможность прокрутки сетки данных зависит от содержимого и наличия полос прокрутки.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Зависит от обстоятельств|Возможность выбора сетки данных зависит от содержимого.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Да|Элемент управления DataGrid всегда имеет заголовок в поддереве, поэтому должен поддерживаться шаблон элемента управления Table.|  
  
 Элементы данных в контейнерах DataGrid будут поддерживать как минимум следующие шаблоны:  
  
-   шаблон элемента управления Selection Item (если сетка данных поддерживает выбор);  
  
-   шаблон элемента управления Scroll Item (если сетка данных поддерживает прокрутку);  
  
-   шаблон элемента управления Grid Item;  
  
-   Table Item - шаблон элемента управления  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Необходимые события модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены события [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться всеми элементами управления DataGrid. Дополнительные сведения о событиях см. в разделе [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] событие|Поддержка|Примечания|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Обязательный|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> событие изменения свойства.|Обязательно|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> событие изменения свойства.|Обязательно|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> событие изменения свойства.|Обязательно|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Зависит от обстоятельств|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Обязательно|Нет|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> событие изменения свойства.|Зависит от обстоятельств|Нет|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> событие изменения свойства.|Зависит от обстоятельств|Если элемент управления поддерживает шаблон Scroll, то он должен поддерживать данное событие.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Обязательно|Нет|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Пример элемента управления DataGrid  
 На следующем рисунке показан элемент управления List View, который реализует тип элемента управления DataGrid.  
  
 ![Графического элемента управления представления списка с двумя элементами данных](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Представление элемента управления и представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , относящиеся к элементу управления List View, показаны ниже. Шаблоны элементов управления для каждого элемента автоматизации отображаются в круглых скобках.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Дерево - представление элемента управления|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Дерево - представление содержимого|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Table, Grid, Selection)</li><li>Header<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "Date Modified" (Invoke)</li><li>HeaderItem "Size" (Invoke)</li></ul></li><li>Группе «Contoso» (TableItem, GridItem, SelectionItem, таблица *, сетка\*)<br /><br /> <ul><li>DataItem «учетные записи Receivable.doc» (SelectionItem, вызвать, TableItem\*, GridItem\*)</li><li>DataItem «учетные записи Payable.doc» (SelectionItem, вызвать, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (Table, Grid, Selection)</li><li>Группе «Contoso» (TableItem, GridItem, SelectionItem, таблица *, сетка\*)<br /><br /> <ul><li>DataItem «учетные записи Receivable.doc» (SelectionItem, вызвать, TableItem\*, GridItem\*)</li><li>DataItem «учетные записи Payable.doc» (SelectionItem, вызвать, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 *В предыдущем примере показан элемент управления DataGrid, содержащий несколько уровней элементов управления. Элемент управления Group ("Contoso") содержит два элемента управления DataItem ("Accounts Receivable.doc" и "Accounts Payable.doc"). Пара DataGrid/GridItem не зависит от пары на другом уровне. Элементы управления DataItem в элементе управления Group также могут предоставляться как тип элемента управления ListItem, что позволяет им быть представленными более четко, как выбираемые объекты, а не как простые элементы данных. Этот пример не включает дочерние элементы сгруппированных элементов данных.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Общие сведения о типах элементов управления автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Общие сведения о модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-overview.md)
