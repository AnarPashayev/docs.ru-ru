---
title: Поддержка автоматизированного пользовательского интерфейса для текстовых элементов управления
ms.date: 03/30/2017
helpviewer_keywords:
- Text control type
- UI Automation, Text control type
- control types, Text
ms.assetid: ab0d0ada-8a71-4547-9c03-aadf675938f2
ms.openlocfilehash: f98477117981504b9c4df43626c7bcb8c4088922
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996558"
---
# <a name="ui-automation-support-for-the-text-control-type"></a>Поддержка автоматизированного пользовательского интерфейса для текстовых элементов управления
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 В этом разделе содержатся сведения о поддержке [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] типа элемента управления Text. В [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]тип элемента управления — это набор условий, которым должен удовлетворять элемент управления для использования свойства <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Условия включают конкретные правила для древовидной структуры [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значений свойств [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] и шаблонов элементов управления.  
  
 Элементы управления "Текст" являются основными элементами пользовательского интерфейса, представляющими фрагменты текста на экране.  
  
 В следующих разделах описывается необходимая древовидная структура [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , свойства, шаблоны элементов управления и события для типа элемента управления Text. Требования [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] применяются ко всем элементам управления "Текст", будь это [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]или [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Требуемая древовидная структура модели автоматизации пользовательского интерфейса  
 В следующей таблице описывается представление элемента управления и представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , относящиеся к элементам управления "Текст", и показывается, что может содержаться в каждом представлении. Дополнительные сведения о дереве [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] см. в разделе [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Представление элемента управления|Представление содержимого|  
|------------------|------------------|  
|Текста|Text (если содержимое)|  
  
 Элемент управления "Текст" может использоваться один в качестве метки или статического текста в форме. Он также может содержаться в структуре следующих типов элементов управления:  
  
- ListItem  
  
- TreeItem  
  
- DataItem  
  
 Элементы управления "Текст" могут отсутствовать в представлении содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , поскольку текст часто отображается с помощью `NameProperty` другого элемента управления. Например текст, который используется в качестве метки элемента управления "Поле со списком", предоставляется с помощью значения `NameProperty` элемента управления. Поскольку элемент управления "Поле со списком" находится в представлении содержимого дерева модели автоматизации пользовательского интерфейса, здесь необязательно должен присутствовать элемент управления "Текст". Элементы управления "Текст" никогда не имеют дочерних элементов в представлении содержимого.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Требуемые свойства модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены свойства [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значения или определения которых особенно актуальны для элементов управления "Текст". Дополнительные сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] свойства, см. в разделе [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Свойство[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] |Значение|Примечания|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|См. примечания.|Значение этого свойства должно быть уникальным среди всех элементов управления в приложении.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|См. примечания.|Внешний прямоугольник, содержащий весь элемент управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|См. примечания.|Поддерживается при наличии ограничивающего прямоугольника. Если не все точки внутри ограничивающего прямоугольника являются интерактивными и выполняется специализированная проверка на наличие данных, выполните переопределение и предоставьте интерактивную точку.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|См. примечания.|Если элемент управления может получать фокус клавиатуры, он должен поддерживать это свойство.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|См. примечания.|Элемент управления "Панель текста" всегда является текстом, который он отображает.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Элементы управления "Текст" не имеют меток со статическим текстом.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Текста|Это значение является одинаковым для всех инфраструктур пользовательского интерфейса.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"текст"|Локализованная строка, соответствующая типу элемента управления Text.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Зависит от обстоятельств|Элемент управления "Текст" будет содержимым, если он содержит сведения, которые не представлены в NameProperty другого элемента управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Элемент управления "Текст" всегда должен быть элементом управления.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Необходимые шаблоны элементов управления модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены шаблоны элементов управления [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться элементами управления "Текст". Дополнительные сведения о шаблонах элементов управления см. в разделе [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Шаблон элемента управления|Поддержка|Примечания|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Никогда|Текст никогда не поддерживает ValuePattern. Если текст редактируемый, то он является типом элемента управления Edit.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Зависит от обстоятельств|Для улучшения специальных возможностей элемент управления "Текст" может поддерживать шаблон элемента управления Text, хотя это не обязательно. Шаблон элемента управления Text целесообразно использовать, если текст имеет множество стилей и атрибутов (например, цвет, полужирным шрифт и курсив). Зависит от инфраструктуры.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Зависит от обстоятельств|Если текстовый элемент содержится в элементе управления "Таблица", это должно поддерживаться.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Зависит от обстоятельств|Если текстовый элемент содержится в элементе управления "Таблица", это должно поддерживаться.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Необходимые события модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены события [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться всеми элементами управления "Текст". Дополнительные сведения о событиях см. в разделе [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Событие[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] |Поддержка|Примечания|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Обязательный|Нет|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Обязательно|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> |Обязательно|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> |Обязательно|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> |Обязательно|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> |Обязательно|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> |Никогда|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Обязательно|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Обязательно|Нет|  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Automation.ControlType.Text>
- [Общие сведения о типах элементов управления автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Общие сведения о модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-overview.md)
