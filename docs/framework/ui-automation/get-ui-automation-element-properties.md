---
title: Получение свойств элементов управления модели автоматизации пользовательского интерфейса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 93e0fba4288ba3231bfed45252bdaa78892d008c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330770"
---
# <a name="get-ui-automation-element-properties"></a>Получение свойств элементов управления модели автоматизации пользовательского интерфейса
> [!NOTE]
>  Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 В этом разделе показано, как получить свойства [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] элемент.  
  
### <a name="get-a-current-property-value"></a>Получение текущего значения свойства  
  
1. Получить <xref:System.Windows.Automation.AutomationElement> , свойство которого вы хотите получить.  
  
2. Вызовите <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, или получить <xref:System.Windows.Automation.AutomationElement.Current%2A> структуры свойства и значение из одного из его членов.  
  
### <a name="get-a-cached-property-value"></a>Получение кэшированного значения свойства  
  
1. Получить <xref:System.Windows.Automation.AutomationElement> , свойство которого вы хотите получить. Свойство должно быть указано в <xref:System.Windows.Automation.CacheRequest>.  
  
2. Вызовите <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, или получить <xref:System.Windows.Automation.AutomationElement.Cached%2A> структуры свойства и значение из одного из его членов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано разных способов получения текущих свойств объекта <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>См. также

- [Свойства автоматизации пользовательского интерфейса для клиентов](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Использование кэширования в модели автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Кэширование в клиентах автоматизации пользовательского интерфейса](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
