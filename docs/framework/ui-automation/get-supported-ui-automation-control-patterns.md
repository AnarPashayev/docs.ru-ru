---
title: Получение шаблонов элементов управления, поддерживающих модель автоматизации пользовательского интерфейса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 133dabe861fbbcf5cac3fbb8669b78e582f8b87b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043647"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Получение шаблонов элементов управления, поддерживающих модель автоматизации пользовательского интерфейса
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.  
  
 В этом разделе показано, как получать объекты шаблона элемента управления из элементов [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="obtain-all-control-patterns"></a>Получение всех шаблонов элементов управления  
  
1. Получите <xref:System.Windows.Automation.AutomationElement>, шаблоны элементов управления которого вас интересуют.  
  
2. Вызовите метод <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>, чтобы получить все шаблоны элементов управления из этого элемента.  
  
> [!CAUTION]
> Настоятельно рекомендуется, чтобы клиент не использовал метод <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Производительность может значительно снизиться, так как этот метод вызывает метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> внутренне для каждого существующего шаблона элемента управления. Если это возможно, клиент должен вызывать метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> для основных интересующих шаблонов.  
  
### <a name="obtain-a-specific-control-pattern"></a>Получение конкретного шаблона элемента управления  
  
1. Получите <xref:System.Windows.Automation.AutomationElement>, шаблоны элементов управления которого вас интересуют.  
  
2. Вызовите метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> или <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> для запроса определенного шаблона. Эти методы похожи, но если шаблон не найден, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> вызывает исключение, а <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> возвращает значение `false`.  
  
## <a name="example"></a>Пример  
 В следующем примере извлекается <xref:System.Windows.Automation.AutomationElement> для элемента списка и получается <xref:System.Windows.Automation.SelectionItemPattern> из этого элемента.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>См. также

- [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](ui-automation-control-patterns-for-clients.md)
