---
title: Практическое руководство. Изменение цвета элемента с помощью событий фокуса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 744963cc543110121a777e1d4c3cdcb3cec40d9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217644"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="e14fb-102">Практическое руководство. Изменение цвета элемента с помощью событий фокуса</span><span class="sxs-lookup"><span data-stu-id="e14fb-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="e14fb-103">В этом примере показано, как изменение цвета элемента, когда он получает и теряет фокус с помощью <xref:System.Windows.UIElement.GotFocus> и <xref:System.Windows.UIElement.LostFocus> события.</span><span class="sxs-lookup"><span data-stu-id="e14fb-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="e14fb-104">В этом примере состоит из [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] файл и файл с выделенным кодом.</span><span class="sxs-lookup"><span data-stu-id="e14fb-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e14fb-105">Пример</span><span class="sxs-lookup"><span data-stu-id="e14fb-105">Example</span></span>  
 <span data-ttu-id="e14fb-106">Следующие [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] создает пользовательский интерфейс, который состоит из двух <xref:System.Windows.Controls.Button> объектов, а также присоединяет обработчики событий для <xref:System.Windows.UIElement.GotFocus> и <xref:System.Windows.UIElement.LostFocus> событий <xref:System.Windows.Controls.Button> объектов.</span><span class="sxs-lookup"><span data-stu-id="e14fb-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="e14fb-107">Следующий код создает <xref:System.Windows.UIElement.GotFocus> и <xref:System.Windows.UIElement.LostFocus> обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="e14fb-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="e14fb-108">Когда <xref:System.Windows.Controls.Button> прирост фокус <xref:System.Windows.Controls.Control.Background%2A> из <xref:System.Windows.Controls.Button> изменяется на красный.</span><span class="sxs-lookup"><span data-stu-id="e14fb-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="e14fb-109">Когда <xref:System.Windows.Controls.Button> теряет фокус клавиатуры, <xref:System.Windows.Controls.Control.Background%2A> из <xref:System.Windows.Controls.Button> изменяется обратно на белое.</span><span class="sxs-lookup"><span data-stu-id="e14fb-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="e14fb-110">См. также</span><span class="sxs-lookup"><span data-stu-id="e14fb-110">See also</span></span>

- [<span data-ttu-id="e14fb-111">Общие сведения о входных данных</span><span class="sxs-lookup"><span data-stu-id="e14fb-111">Input Overview</span></span>](input-overview.md)
