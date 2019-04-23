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
ms.openlocfilehash: 64c5bae738cee5249e6c2406a2f94667ecb2931f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337023"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="b7f1e-102">Получение шаблонов элементов управления, поддерживающих модель автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="b7f1e-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="b7f1e-103">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="b7f1e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b7f1e-104">Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b7f1e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b7f1e-105">В этом разделе показано, как получать объекты шаблона элемента управления из элементов [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7f1e-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="b7f1e-106">Получение всех шаблонов элементов управления</span><span class="sxs-lookup"><span data-stu-id="b7f1e-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="b7f1e-107">Получите <xref:System.Windows.Automation.AutomationElement>, шаблоны элементов управления которого вас интересуют.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="b7f1e-108">Вызовите метод <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>, чтобы получить все шаблоны элементов управления из этого элемента.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b7f1e-109">Настоятельно рекомендуется, чтобы клиент не использовал метод <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="b7f1e-110">Производительность может значительно снизиться, так как этот метод вызывает метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> внутренне для каждого существующего шаблона элемента управления.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="b7f1e-111">Если это возможно, клиент должен вызывать метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> для основных интересующих шаблонов.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="b7f1e-112">Получение конкретного шаблона элемента управления</span><span class="sxs-lookup"><span data-stu-id="b7f1e-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="b7f1e-113">Получите <xref:System.Windows.Automation.AutomationElement>, шаблоны элементов управления которого вас интересуют.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="b7f1e-114">Вызовите метод <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> или <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> для запроса определенного шаблона.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="b7f1e-115">Эти методы похожи, но если шаблон не найден, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> вызывает исключение, а <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7f1e-116">Пример</span><span class="sxs-lookup"><span data-stu-id="b7f1e-116">Example</span></span>  
 <span data-ttu-id="b7f1e-117">В следующем примере извлекается <xref:System.Windows.Automation.AutomationElement> для элемента списка и получается <xref:System.Windows.Automation.SelectionItemPattern> из этого элемента.</span><span class="sxs-lookup"><span data-stu-id="b7f1e-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="b7f1e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b7f1e-118">See also</span></span>

- [<span data-ttu-id="b7f1e-119">Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов</span><span class="sxs-lookup"><span data-stu-id="b7f1e-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
