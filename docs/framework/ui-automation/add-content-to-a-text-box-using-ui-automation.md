---
title: Добавление содержимого в текстовое поле с помощью модели автоматизации пользовательского интерфейса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 9183aecdc47d54aef26d5cdca8ea11d8398be732
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610079"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="db702-102">Добавление содержимого в текстовое поле с помощью модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="db702-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="db702-103">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="db702-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="db702-104">Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="db702-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="db702-105">В этом разделе содержится пример кода, который демонстрирует использование [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] для вставки текста в однострочное текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="db702-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="db702-106">Альтернативный метод предоставляется для нескольких линий и разнообразные текстовые элементы управления где [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] не применяется.</span><span class="sxs-lookup"><span data-stu-id="db702-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="db702-107">Для сравнения примере также показано, как с помощью методов Win32 выполнить те же результаты.</span><span class="sxs-lookup"><span data-stu-id="db702-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db702-108">Пример</span><span class="sxs-lookup"><span data-stu-id="db702-108">Example</span></span>  
 <span data-ttu-id="db702-109">Следующий пример проходит через последовательность текстовых элементов управления в целевом приложении.</span><span class="sxs-lookup"><span data-stu-id="db702-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="db702-110">Каждый текстовый элемент управления проверяется на предмет <xref:System.Windows.Automation.ValuePattern> может быть получен из строки с помощью <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="db702-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="db702-111">Если текстовый элемент управления поддерживает <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> метод используется для вставки определяемую пользователем строку в текстовый элемент управления.</span><span class="sxs-lookup"><span data-stu-id="db702-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="db702-112">В противном случае <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> используется метод.</span><span class="sxs-lookup"><span data-stu-id="db702-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="db702-113">См. также</span><span class="sxs-lookup"><span data-stu-id="db702-113">See also</span></span>

- <span data-ttu-id="db702-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="db702-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
