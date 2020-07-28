---
title: Поддержка автоматизированного пользовательского интерфейса для типа элемента управления ListItem
description: Получение сведений о поддержке модели автоматизации пользовательского интерфейса для типа элемента управления ListItem. Сведения о требуемой древовидной структуре, свойствах, шаблонах элементов управления и событиях.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: bf1690b094e9d472fd4213f7fa3df545dca6ebac
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166060"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Поддержка автоматизированного пользовательского интерфейса для типа элемента управления ListItem
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).  
  
 В этом разделе содержатся сведения о поддержке [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] типа элемента управления <xref:System.Windows.Automation.ControlType.ListItem> . В [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]тип элемента управления — это набор условий, которым должен удовлетворять элемент управления для использования свойства <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Условия включают конкретные правила для древовидной структуры [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значений свойств [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] и шаблонов элементов управления.  
  
 Элементы управления "Список" являются примерами элементов управления, реализующих тип элемента управления ListItem.  
  
 В следующих разделах описывается необходимая древовидная структура [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , свойства, шаблоны элементов управления и события для типа элемента управления ListItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Требования применяются ко всем элементам управления "список", будь это [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 или Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Требуемая древовидная структура модели автоматизации пользовательского интерфейса  
 В следующей таблице описывается представление элемента управления и представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , относящиеся к элементам управления "Список", и показывается, что может содержаться в каждом представлении. Дополнительные сведения о дереве [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] см. в разделе [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Представление элемента управления|Представление содержимого|  
|------------------|------------------|  
|ListItem<br /><br /> -Image (0 или более)<br />— Текст (0 или более)<br />-Edit (0 или более)|ListItem|  
  
 Дочерний элемент элемента управления "Список" в представлении содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] всегда должен быть "0". Если структура элемента управления состоит в том, что в элементе списка содержатся другие элементы, они должны удовлетворять требованиям [модели автоматизации пользовательского интерфейса для](ui-automation-support-for-the-treeitem-control-type.md) типа элемента управления типа TreeItem.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Требуемые свойства модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены свойства [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , значение или определение которых в первую очередь относится к элементам управления "Список". Дополнительные сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] свойствах см. в разделе [Свойства модели автоматизации пользовательского интерфейса для клиентов](ui-automation-properties-for-clients.md).  
  
|Свойство[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|Значение|Примечания|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|См. примечания.|Значение этого свойства должно быть уникальным среди всех элементов управления в приложении.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|См. примечания.|Это значение данного свойства должно включать область изображения и текста элемента списка.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Зависит|Если элемент управления "Список" имеет активную точку (точка, которую можно щелкнуть, чтобы перенести фокус в этот список), то такая точка должна предоставляться через это свойство. Если элемент управления "Список" полностью покрывается дочерними элементами списка, он будет вызывать <xref:System.Windows.Automation.NoClickablePointException> для указания, что клиент должен запрашивать активную точку в элементе внутри элемента управления "Список".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|См. примечания.|Значение свойства имени элемента управления "Список" берется из текстового содержимого элемента.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|См. примечания.|Если имеется статическая текстовая метка, то данное свойство должно предоставлять ссылку на этот элемент управления.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|Это значение одинаково для всех инфраструктур пользовательского интерфейса.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"элемент списка"|Локализованная строка, соответствующая типу элемента управления ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Элемент управления "Список" всегда включается в представление содержимого дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Элемент управления "Список" всегда включается в представление элемента управления дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Если контейнер может принимать ввод с клавиатуры, это свойство должно иметь значение true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Текст справки для элементов управления "Список" должен объяснять, почему пользователю предлагается сделать выбор из списка вариантов; обычно в этой справке содержатся сведения того же типа, что и в подсказке. Например, "Выберите элемент, чтобы установить разрешение экрана монитора".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Зависит|Это свойство должно предоставляться для элементов управления "Список", которые представляют базовый объект. Такие элементы управления "Список" обычно имеют значок, связанный с элементом управления, который пользователи связывают с базовым объектом.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Зависит|Это свойство должно возвращать значение, указывающее, прокручивается ли в данный момент элемент списка в представление в родительском контейнере, реализующем шаблон элемента управления Scroll.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Необходимые шаблоны элементов управления модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены шаблоны элементов управления [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться элементами управления "Список". Дополнительные сведения о шаблонах элементов управления см. в разделе [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Шаблон элемента управления|Поддержка|Примечания|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Да|Элемент управления "Список" должен реализовывать данный шаблон элемента управления. Это позволяет элементам управления передавать информацию при их выборе.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Зависит|Если элемент списка находится в контейнере, поддерживающем прокрутку, то этот шаблон элемента управления должен быть реализован.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Зависит|Если элемент списка является проверяемым и действие не производит изменение состояния выделения, то этот шаблон элемента управления должен быть реализован.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Зависит|Если элемент можно изменять, чтобы показать или скрыть сведения, то этот шаблон элемента управления должен быть реализован.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Зависит|Если элемент можно редактировать, то этот шаблон элемента управления должен быть реализован. Изменения элемента управления "Список" приведут к изменениям значений <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>и <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Зависит|Если в контейнере списка поддерживается пространственная навигация от элемента к элементу и этот контейнер размещается в строках и столбцах, то должен быть реализован шаблон элемента управления Grid Item.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Зависит|Если элемент содержит команду, которая может выполняться в этом элементе, то этот шаблон должен быть реализован. Обычно это действие, связанное с двойным щелчком элемента управления "Список". Примерами может быть запуск документа из проводника Microsoft Windows или воспроизведение музыкального файла в проигрывателе Microsoft Windows Media Player.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Необходимые события модели автоматизации пользовательского интерфейса  
 В следующей таблице перечислены события [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , которые должны поддерживаться всеми элементами управления "Список". Дополнительные сведения о событиях см. в разделе [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|Событие[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Поддержка|Примечания|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Зависит|Нет|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Требуется|Нет|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Требуется|Нет|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Требуется|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Требуется|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Требуется|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Требуется|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Требуется|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Зависит|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>|Зависит|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>|Зависит|Нет|  
|Событие изменения свойства<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Зависит|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Требуется|Нет|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Требуется|Нет|  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Общие сведения о типах элементов управления автоматизации пользовательского интерфейса](ui-automation-control-types-overview.md)
- [Общие сведения о модели автоматизации пользовательского интерфейса](ui-automation-overview.md)
