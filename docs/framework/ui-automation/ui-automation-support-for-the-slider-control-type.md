---
title: Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ползунка
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
ms.openlocfilehash: 4c1b965075de3f0954a3873cc6bb3411a86c0923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954733"
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ползунка
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.  
  
 В этом разделе содержатся сведения о поддержке [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] типа элемента управления Slider. В [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]тип элемента управления — это набор условий, которым должен удовлетворять элемент управления для использования свойства <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Условия включают конкретные правила для древовидной структуры [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значений свойств [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] и типов элементов управления.  
  
 Элемент управления "Ползунок" является составным элементом управления с кнопками, которые предоставляют пользователю возможность с помощью мыши задать числовой диапазон или выбрать из набора элементов.  
  
 В следующих разделах описывается необходимая древовидная структура [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , свойства, шаблоны элементов управления и события для типа элемента управления Slider. Требования [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] применяются ко всем элементам управления "Ползунок", будь это [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]или [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Требуемая древовидная структура модели автоматизации пользовательского интерфейса  
 В следующей таблице описывается представление элемента управления и представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , относящиеся к элементам управления "Ползунок", и показывается, что может содержаться в каждом представлении. Дополнительные сведения о дереве [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] см. в разделе [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Представление элемента управления|Представление содержимого|  
|------------------|------------------|  
|Slider<br /><br /> -Кнопка (2 или 4)<br />-Thumb (только 1)<br />— Элемент списка (0 или более)|Slider<br /><br /> — Элемент списка (0 или более)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Требуемые свойства модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены свойства [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значения или определения которых особенно актуальны для типа элемента управления Slider. Дополнительные сведения о свойствах см. в [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] разделе [Свойства модели автоматизации пользовательского интерфейса для клиентов](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Свойство[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Значение|Примечания|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|См. примечания.|Значение этого свойства должно быть уникальным среди всех элементов управления в приложении.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|См. примечания.|Внешний прямоугольник, содержащий весь элемент управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|См. примечания.|Большинство элементов управления "Ползунок" должно вызывать исключение <xref:System.Windows.Automation.NoClickablePointException> , так как весь ограничивающий прямоугольник элемента управления "Ползунок" занят дочерними элементами управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|См. примечания.|Если элемент управления может получать фокус клавиатуры, он должен поддерживать это свойство.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|См. примечания.|Имя элемента управления "Поле ввода" обычно создается из статического текста метки. Если статическая текстовая метка не предусмотрена, разработчик приложения должен предоставить значение для свойства `Name` . Значение свойства `Name` никогда не должно быть текстовым содержимым элемента управления "Поле ввода".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|См. примечания.|Если статическая текстовая метка связана с элементом управления, то данное свойство должно предоставлять ссылку на этот элемент управления. Если элемент управления "Текст" является подкомпонентом другого элемента управления, он не будет иметь набор свойств `LabeledBy` .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Slider|Это значение является одинаковым для всех инфраструктур [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ползунок"|Локализованная строка, соответствующая типу элемента управления Edit.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Элемент управления "Поле ввода" всегда включается в представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Элемент управления "Поле ввода" всегда включается в представление элемента управления дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Необходимые шаблоны элементов управления модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены шаблоны элементов управления [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться всеми элементами управления "Ползунок". Дополнительные сведения о шаблонах элементов управления см. в разделе [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Шаблон элемента управления|Поддержка|Примечания|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Зависит от обстоятельств|Если содержимое представляет одно из значений дискретного набора параметров, ползунок должен поддерживать шаблон элемента управления Selection. Если шаблон элемента управления Selection поддерживается, соответствующий выбор должен представляться как один или несколько дочерних элементов списка ползунка.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Зависит от обстоятельств|Если содержимому может быть присвоено значение из числового диапазона, ползунок должен поддерживать шаблон элемента управления RangeValue.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Зависит от обстоятельств|Если содержимое представляет одно из значений дискретного набора параметров, ползунок должен поддерживать шаблон элемента управления Value.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Необходимые события модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены события [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться всеми элементами управления "Ползунок".  
  
 Дополнительные сведения о событиях см. в разделе [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Событие[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Поддержка|Примечания|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Зависит от обстоятельств|Отсутствуют|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Обязательно|Отсутствуют|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Обязательно|Отсутствуют|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Обязательно|Отсутствуют|  
|Событие изменения свойства<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>|Зависит от обстоятельств|Отсутствуют|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Обязательно|Отсутствуют|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Обязательно|Отсутствуют|  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Automation.ControlType.Slider>
- [Общие сведения о типах элементов управления автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Общие сведения о модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-overview.md)
