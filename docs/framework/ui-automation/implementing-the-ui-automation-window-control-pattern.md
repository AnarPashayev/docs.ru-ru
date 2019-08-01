---
title: Реализация шаблона элемента управления Window автоматизированного пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: 9cab4dbbcd3302a6e74783eaefdbbd8463332224
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710246"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Реализация шаблона элемента управления Window автоматизированного пользовательского интерфейса
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.  
  
 В этом разделе приводятся рекомендации и соглашения для реализации <xref:System.Windows.Automation.Provider.IWindowProvider>, включая сведения о свойствах, методах и событиях <xref:System.Windows.Automation.WindowPattern> . Ссылки на дополнительные материалы перечислены в конце раздела.  
  
 Шаблон <xref:System.Windows.Automation.WindowPattern> элемента управления используется для поддержки элементов управления, которые предоставляют фундаментальные функции на основе окна в традиционном графическом интерфейсе пользователя. В качестве примеров элементов управления, которые должны реализовывать этот шаблон элемента управления, можно назвать окна приложения верхнего уровня, дочерние окна [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] , элементы управления "Область разделения с возможностью изменения размера", модальные диалоговые окна и окна всплывающей справки.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Правила и соглашения реализации  
 При реализации шаблона элемента управления Window обратите внимание на следующие правила и соглашения.  
  
- Для поддержки возможности изменения размера окна и его положения на экране с помощью модели автоматизации пользовательского интерфейса элемент управления должен реализовать <xref:System.Windows.Automation.Provider.ITransformProvider> в дополнение к <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Элементы управления, содержащие заголовки окон и элементы этих заголовков, позволяющие перемещать, разворачивать, сворачивать, закрывать элемент управления или изменять его размер, обычно должны реализовывать <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Такие элементы управления, как всплывающие подсказки, поля со списком или раскрывающиеся меню, обычно не реализуют <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Окна всплывающей справки отличаются от обычных всплывающих подсказок тем, что предоставляют кнопку закрытия окна.  
  
- IWindowProvider не поддерживает полноэкранный режим, так как он зависит от компонентов в приложении и не является типичным поведением окна.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Обязательные члены для IWindowProvider  
 Следующие свойства, методы и события обязательны для реализации интерфейса IWindowProvider.  
  
|Обязательный член|Тип члена|Примечания|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Свойство.|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Метод|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Метод|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Метод|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|событие|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|событие|None|  
|<xref:System.Windows.Automation.WindowInteractionState>|событие|Не гарантируется, что будет <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Исключения  
 Поставщики должны вызывать следующие исключения.  
  
|Тип исключения|Условие|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> — Если элемент управления не поддерживает запрошенное поведение.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> — Если параметр не является допустимым числом.|  
  
## <a name="see-also"></a>См. также

- [Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Поддержка шаблонов элементов управления в поставщике автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Общие сведения о дереве модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Использование кэширования в модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
