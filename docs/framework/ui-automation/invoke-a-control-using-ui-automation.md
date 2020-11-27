---
title: Вызов элемента управления с помощью модели автоматизации пользовательского интерфейса
description: Используйте автоматизацию пользовательского интерфейса для поиска элемента управления, соответствующего определенным условиям свойства, создайте AutomationElement, получите InvokePattern и используйте Invoke для элемента управления.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 7c6f5d26d16642f978fd79fd40701c240a53f16a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278002"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="07898-103">Вызов элемента управления с помощью модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="07898-103">Invoke a Control Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="07898-104">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="07898-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="07898-105">Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="07898-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="07898-106">В этом примере показано выполнение следующих задач.</span><span class="sxs-lookup"><span data-stu-id="07898-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="07898-107">Поиск элемента управления, который соответствует конкретным условиям свойств путем прохода представления элемента управления дерева [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] для целевого приложения.</span><span class="sxs-lookup"><span data-stu-id="07898-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="07898-108">Создание <xref:System.Windows.Automation.AutomationElement> для каждого элемента управления.</span><span class="sxs-lookup"><span data-stu-id="07898-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="07898-109">Получение объекта <xref:System.Windows.Automation.InvokePattern> из любого найденного элемента [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , который поддерживает шаблон элемента управления <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="07898-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="07898-110">Использование <xref:System.Windows.Automation.InvokePattern.Invoke%2A> для вызова элемента управления из обработчика событий клиента.</span><span class="sxs-lookup"><span data-stu-id="07898-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07898-111">Пример</span><span class="sxs-lookup"><span data-stu-id="07898-111">Example</span></span>  

 <span data-ttu-id="07898-112">В этом примере используется метод <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> класса <xref:System.Windows.Automation.AutomationElement> для создания объекта <xref:System.Windows.Automation.InvokePattern> и вызова элемента управления с помощью метода <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="07898-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="07898-113">См. также</span><span class="sxs-lookup"><span data-stu-id="07898-113">See also</span></span>

- [<span data-ttu-id="07898-114">Пример InvokePattern, ExpandCollapsePattern и Тогглепаттерн</span><span class="sxs-lookup"><span data-stu-id="07898-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
