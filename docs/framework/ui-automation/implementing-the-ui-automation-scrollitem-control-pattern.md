---
title: Реализация шаблона элемента управления ScrollItem модели автоматизации пользовательского интерфейса
description: Ознакомьтесь с правилами и соглашениями по реализации шаблона элемента управления Скроллитем в модели автоматизации пользовательского интерфейса. См. раздел обязательные элементы для интерфейса Искроллитемпровидер.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163569"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Реализация шаблона элемента управления ScrollItem модели автоматизации пользовательского интерфейса
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).  
  
 В этом разделе приводятся рекомендации и соглашения для реализации <xref:System.Windows.Automation.Provider.IScrollItemProvider>, включая сведения о свойствах, методах и событиях. Ссылки на дополнительные материалы перечислены в конце раздела.  
  
 Шаблон элемента управления <xref:System.Windows.Automation.ScrollItemPattern> используется для поддержки отдельных дочерних элементов управления контейнеров, реализующих <xref:System.Windows.Automation.Provider.IScrollProvider>. Этот шаблон элемента управления действует как отдельный канал связи между дочерним элементом управления и его контейнером, чтобы контейнер гарантированно мог изменять видимое в настоящий момент содержимое (или область) в его области просмотра для отображения дочернего элемента управления. Примеры элементов управления, реализующих данный шаблон элемента управления, см. в разделе [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Правила и соглашения реализации  
 При реализации шаблона элемента управления ScrollItem обратите внимание на следующие правила и соглашения.  
  
- Не требуется, чтобы элементы, содержащиеся в элементе управления "Окно" или "Полотно", реализовывали интерфейс IScrollItemProvider. Однако в качестве альтернативы они должны предоставлять действительное расположение для <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Это позволит клиентскому приложению модели автоматизации пользовательского интерфейса использовать методы шаблона элемента управления <xref:System.Windows.Automation.ScrollPattern> в контейнере для отображения дочернего элемента шаблона элемента управления.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a>Обязательные члены для IScrollItemProvider  
 Следующий метод является обязательным для реализации интерфейса IScrollProvider.  
  
|Обязательные члены|Тип члена|Примечания|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Method|Нет|  
  
 Этот шаблон элемента управления не имеет связанных свойств или событий.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Исключения  
 Поставщики должны вызывать следующие исключения.  
  
|Тип исключения|Условие|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Если элемент не может быть прокручен в представлении:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>См. также

- [Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса](ui-automation-control-patterns-overview.md)
- [Поддержка шаблонов элементов управления в поставщике модели автоматизации пользовательского интерфейса](support-control-patterns-in-a-ui-automation-provider.md)
- [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](ui-automation-control-patterns-for-clients.md)
- [Общие сведения о дереве модели автоматизации пользовательского интерфейса](ui-automation-tree-overview.md)
- [Использование кэширования в модели автоматизации пользовательского интерфейса](use-caching-in-ui-automation.md)
