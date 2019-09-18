---
title: Сопоставление шаблона элемента управления для клиентов автоматизации пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: cfd8e5dbe34df7b947646c714a360cf56b0435a4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043862"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Сопоставление шаблона элемента управления для клиентов автоматизации пользовательского интерфейса
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.  
  
 В этом разделе перечислены типы элементов управления и связанные с ними шаблоны элементов управления.  
  
 В таблице ниже шаблоны элементов управления распределены по следующим категориям.  
  
- Поддерживается. Элемент управления должен поддерживать этот шаблон элемента управления.  
  
- Условно поддерживается. Элемент управления может поддерживать этот шаблон элемента управления в зависимости от состояния элемента управления.  
  
- Не поддерживается. Элемент управления не поддерживает этот шаблон элемента управления; пользовательские элементы управления могут поддерживать этот шаблон элемента управления.  
  
> [!NOTE]
> Некоторые элементы управления имеют условную поддержку нескольких шаблонов элементов управления, в зависимости от функциональности этих элементов управления. Например, элемент управления "Пункт меню" имеет условную поддержку шаблона элемента управления <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>или <xref:System.Windows.Automation.SelectionItemPattern> , в зависимости от его функции в элементе управления "Меню".  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов  
  
|Тип элемента управления|Поддерживается|Условно поддерживается|Не поддерживается|  
|------------------|---------------|-------------------------|-------------------|  
|Кнопка|Отсутствуют|Invoke, Toggle, Expand Collapse|Отсутствуют|  
|Календарь|Grid, Table|Selection, Scroll|Значение|  
|Флажок|Toggle|Отсутствуют|Отсутствуют|  
|Combo Box|Развернуть свернуть|Selection, Value|Scroll|  
|Data Grid|Grid|Scroll, Selection, Table|Отсутствуют|  
|Data Item|Selection Item|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|Отсутствуют|  
|Document|Текст|Scroll, Value|Отсутствуют|  
|Правка|Отсутствуют|Text, Range Value, Value|Отсутствуют|  
|Группа|Отсутствуют|Развернуть свернуть|Отсутствуют|  
|Header|Отсутствуют|Transform|Отсутствуют|  
|элемент заголовка|Отсутствуют|Transform, Invoke|Отсутствуют|  
|Hyperlink|Вызвать|Значение|Отсутствуют|  
|Изображение|Отсутствуют|Grid Item, Table Item|Invoke, Selection Item|  
|Список|Отсутствуют|Grid, Multiple View, Scroll, Selection|Таблица|  
|List Item|Selection Item|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|Отсутствуют|  
|Меню|Отсутствуют|Отсутствуют|Отсутствуют|  
|Menu Bar|Отсутствуют|Expand Collapse, Dock, Transform|Отсутствуют|  
|Menu Item|Отсутствуют|Expand Collapse, Invoke, Selection Item, Toggle|Отсутствуют|  
|Панель|Отсутствуют|Dock Scroll, Transform|Окно|  
|Progress Bar|Отсутствуют|Range Value, Value|Отсутствуют|  
|Radio Button|Selection Item|Отсутствуют|Toggle|  
|Scroll Bar|Отсутствуют|Range Value|Scroll|  
|Separator|Отсутствуют|Отсутствуют|Отсутствуют|  
|Slider|Отсутствуют|Range Value, Selection, Value|Отсутствуют|  
|Spinner|Отсутствуют|Range Value, Selection, Value|Отсутствуют|  
|Разворачивающаяся кнопка|Invoke, Expand Collapse|Отсутствуют|Отсутствуют|  
|Status Bar|Отсутствуют|Grid|Отсутствуют|  
|Вкладка|Выбранное|Scroll|Отсутствуют|  
|Tab Item|Selection Item|Отсутствуют|Вызвать|  
|Таблица|Grid, Grid Item, Table, Table Item|Отсутствуют|Отсутствуют|  
|Текст|Отсутствуют|Grid Item, Table Item, Text|Значение|  
|Бегунок|Transform|Отсутствуют|Отсутствуют|  
|Title Bar|Отсутствуют|Отсутствуют|Отсутствуют|  
|Tool Bar|Отсутствуют|Dock, Expand Collapse, Transform|Отсутствуют|  
|Tool Tip|Отсутствуют|Text, Window|Отсутствуют|  
|Дерево|Отсутствуют|Scroll, Selection|Отсутствуют|  
|Tree Item|Развернуть свернуть|Invoke, Scroll Item, Selection Item, Toggle|Отсутствуют|  
|Окно|Transform, Window|Закрепить|Отсутствуют|  
  
> [!NOTE]
> Если тип элемента управления не имеет поддерживаемых шаблонов элементов управления в списке, но имеет один или несколько условно поддерживаемых шаблонов элементов управления, то один из этих условных шаблонов элементов управления будет поддерживаться все время.  
  
## <a name="see-also"></a>См. также

- [Общие сведения о модели автоматизации пользовательского интерфейса](ui-automation-overview.md)
