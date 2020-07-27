---
title: Реализация шаблона элемента управления сеткой автоматизации пользовательского интерфейса
description: Общие сведения о правилах и соглашениях по реализации шаблона элемента управления Grid GridPattern в модели автоматизации пользовательского интерфейса. Узнайте, как реализовать интерфейс IGridProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: c7aae8e8070c989c4b36e0581aa5f48f51416f97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165871"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Реализация шаблона элемента управления сеткой автоматизации пользовательского интерфейса
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).  
  
 В этом разделе приводятся рекомендации и соглашения для реализации <xref:System.Windows.Automation.Provider.IGridProvider>, включая сведения о свойствах, методах и событиях. Ссылки на дополнительные материалы перечислены в конце раздела.  
  
 Шаблон элемента управления <xref:System.Windows.Automation.GridPattern> используется для поддержки элементов управления, которые действуют как контейнеры для коллекции дочерних элементов. Дочерние элементы данного элемента должны реализовывать <xref:System.Windows.Automation.Provider.IGridItemProvider> и быть организованы в двумерной логической системе координат, к которой можно обращаться по строкам и столбцам. Примеры элементов управления, реализующих данный шаблон элемента управления, см. в разделе [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Правила и соглашения реализации  
 При реализации шаблона элемента управления Grid обратите внимание на следующие правила и соглашения.  
  
- Координаты сетки отсчитываются начиная с нуля и от левой верхней ячейки (или правой верхней ячейки в зависимости от языкового стандарта), имеющей координаты (0, 0).  
  
- Если ячейка пуста, элемент модели автоматизации пользовательского интерфейса по-прежнему должен возвращаться для поддержки свойства <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> для этой ячейки. Это возможно, когда макет дочерних элементов сетки подобен массиву с переменной длиной (см. пример ниже).  
  
 ![Windows Explorer, отображающий неровную структуру.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Пример элемента управления "Сетка" с пустыми координатами  
  
- Сетка с единственным элементом по-прежнему должна реализовывать <xref:System.Windows.Automation.Provider.IGridProvider> , если она логически считается сеткой. Количество дочерних элементов в сетке не имеет значения.  
  
- Скрытые строки и столбцы, в зависимости от реализации поставщика, могут быть загружены в дерево [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] и поэтому будут отражаться в свойствах <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> и <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> . Если скрытые строки и столбцы еще не загружены, они не должны учитываться.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider> не позволяет активно манипулировать сеткой; для включения этой функциональности необходимо реализовать <xref:System.Windows.Automation.Provider.ITransformProvider> .  
  
- Используйте <xref:System.Windows.Automation.StructureChangedEventHandler> для прослушивания изменений структуры или макета сетки, таких как добавление, удаление или слияние ячеек.  
  
- Используйте <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> для отслеживания прохождения по элементам или ячейкам сетки.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>Обязательные члены для IGridProvider  
 Следующие свойства и методы обязательны для реализации интерфейса IGridProvider.  
  
|Обязательные члены|Тип|Примечания|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Свойство|None|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Свойство|None|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Метод|None|  
  
 Этот шаблон элемента управления не имеет связанных событий.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Исключения  
 Поставщики должны вызывать следующие исключения.  
  
|Тип исключения|Условие|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Если запрошенная координата строки больше, чем, <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> или значение координаты столбца больше, чем <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Если любая из запрошенных координат строки или столбца меньше нуля.|  
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса](ui-automation-control-patterns-overview.md)
- [Поддержка шаблонов элементов управления в поставщике модели автоматизации пользовательского интерфейса](support-control-patterns-in-a-ui-automation-provider.md)
- [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](ui-automation-control-patterns-for-clients.md)
- [Реализация шаблона элемента управления GridItem модели автоматизации пользовательского интерфейса](implementing-the-ui-automation-griditem-control-pattern.md)
- [Общие сведения о дереве модели автоматизации пользовательского интерфейса](ui-automation-tree-overview.md)
- [Использование кэширования в модели автоматизации пользовательского интерфейса](use-caching-in-ui-automation.md)
