---
title: Общие сведения о типах элементов управления автоматизации пользовательского интерфейса
description: Ознакомьтесь с обзором типов элементов управления модели автоматизации пользовательского интерфейса, которые представляют собой хорошо известные идентификаторы, которые можно использовать для указания типа элемента управления, представляемого элементом.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 851d509e719afb658971ea5f6fc2f8fdd6bd2cf7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261349"
---
# <a name="ui-automation-control-types-overview"></a>Общие сведения о типах элементов управления автоматизации пользовательского интерфейса

> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).  
  
 Типы элементов управления[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] — это хорошо известные идентификаторы, которые можно использовать для указания вида элемента управления, например поля со списком или кнопки.  
  
 Известный идентификатор упрощает для вспомогательных устройств определение типов элементов управления, доступных в [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , и способов взаимодействия с ними.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>

## <a name="ui-automation-control-type-requisites"></a>Необходимые компоненты элементов управления автоматизации пользовательского интерфейса  

 Тип элемента управления[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] предоставляют набор условий, которым должны соответствовать поставщики. При выполнении этих условий элемент управления может использовать имя типа определенного элемента управления. Каждый тип элемента управления использует следующие условия:  
  
- Шаблоны элементов управления[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] — какие шаблоны элементов управления должны поддерживаться, какой шаблоны необязательные и какие шаблоны не должны поддерживаться элементом управления.  
  
- Значения свойств[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] — какие значения свойств поддерживаются.  
  
- Структура дерева[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] — обязательная древовидная структура [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] элемента управления.  
  
 Если элемент управления удовлетворяет условиям определенного типа элемента управления, значение свойства <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> указывает этот тип.  
  
<a name="Current_UI_Automation_Control_Types"></a>

## <a name="current-ui-automation-control-types"></a>Текущие типы элементов управления автоматизации пользовательского интерфейса  

 Следующий список содержит текущий набор типов элементов управления [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] :  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления кнопки](ui-automation-support-for-the-button-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Calendar](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Поддержка модели автоматизированного пользовательского интерфейса для элемента управления CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Поддержка автоматизированного пользовательского интерфейса для типа элемента управления DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для элемента управления типа DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Поддержка автоматизированного пользовательского интерфейса для типа элемента управления Document](ui-automation-support-for-the-document-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления "Поле вода"](ui-automation-support-for-the-edit-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления Group](ui-automation-support-for-the-group-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления "Заголовок"](ui-automation-support-for-the-header-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса типа элемента управления HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Поддержка автоматизированного пользовательского интерфейса для элемента управления типа Hyperlink](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления изображения](ui-automation-support-for-the-image-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для элемента управления "Список"](ui-automation-support-for-the-list-control-type.md)  
  
- [Поддержка автоматизированного пользовательского интерфейса для типа элемента управления ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления меню](ui-automation-support-for-the-menu-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для элемента управления Pane](ui-automation-support-for-the-pane-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для элемента управления типа RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для элемента управления Separator](ui-automation-support-for-the-separator-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ползунка](ui-automation-support-for-the-slider-control-type.md)  
  
- [Поддержка Автоматизации Пользовательского Интерфейса для типа элемента управления "Счетчик"](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Поддержка UI Automation для типа элемента управления Tab](ui-automation-support-for-the-tab-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Table](ui-automation-support-for-the-table-control-type.md)  
  
- [Поддержка автоматизированного пользовательского интерфейса для текстовых элементов управления](ui-automation-support-for-the-text-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для элемента управления типа Thumb](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Поддержка Автоматизации Пользовательского Интерфейса для Элементов Управления Типа "Заголовок Окна"](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления ToolBar](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элементов управления ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для древовидного типа элемента управления](ui-automation-support-for-the-tree-control-type.md)  
  
- [Поддержка автоматизации пользовательского интерфейса для типа элемента управления TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Window](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Automation.ControlType>
