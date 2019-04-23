---
title: Практическое руководство. Определение изменения текста в TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091152"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="b1ff9-102">Практическое руководство. Определение изменения текста в TextBox</span><span class="sxs-lookup"><span data-stu-id="b1ff9-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="b1ff9-103">В этом примере показан один из способов использования <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> событий для выполнения метода всякий раз, когда текст в <xref:System.Windows.Controls.TextBox> элемент управления был изменен.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="b1ff9-104">В классе фонового кода для [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , содержащий <xref:System.Windows.Controls.TextBox> элемент управления, который вы хотите отслеживать изменения, вставить метод, вызываемый каждый раз, когда <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b1ff9-105">Этот метод должен иметь сигнатуру, которая соответствует ожидаемых <xref:System.Windows.Controls.TextChangedEventHandler> делегировать.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="b1ff9-106">Обработчик событий вызывается всякий раз, когда содержимое <xref:System.Windows.Controls.TextBox> управления изменяются, либо пользователем, либо программным способом.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="b1ff9-107">**Примечание.** Это событие возникает, когда <xref:System.Windows.Controls.TextBox> создается и изначально была заполнена текстом элемента управления.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ff9-108">Пример</span><span class="sxs-lookup"><span data-stu-id="b1ff9-108">Example</span></span>  
 <span data-ttu-id="b1ff9-109">В [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , определяющий вашей <xref:System.Windows.Controls.TextBox> управления, укажите <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> атрибут со значением, которое соответствует имени метода обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="b1ff9-110">Пример</span><span class="sxs-lookup"><span data-stu-id="b1ff9-110">Example</span></span>  
 <span data-ttu-id="b1ff9-111">В классе фонового кода для [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , содержащий <xref:System.Windows.Controls.TextBox> элемент управления, который вы хотите отслеживать изменения, вставить метод, вызываемый каждый раз, когда <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b1ff9-112">Этот метод должен иметь сигнатуру, которая соответствует ожидаемых <xref:System.Windows.Controls.TextChangedEventHandler> делегировать.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="b1ff9-113">Обработчик событий вызывается всякий раз, когда содержимое <xref:System.Windows.Controls.TextBox> управления изменяются, либо пользователем, либо программным способом.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="b1ff9-114">**Примечание.** Это событие возникает, когда <xref:System.Windows.Controls.TextBox> создается и изначально была заполнена текстом элемента управления.</span><span class="sxs-lookup"><span data-stu-id="b1ff9-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="b1ff9-115">Комментарии</span><span class="sxs-lookup"><span data-stu-id="b1ff9-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ff9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b1ff9-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="b1ff9-117">Общие сведения о TextBox</span><span class="sxs-lookup"><span data-stu-id="b1ff9-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b1ff9-118">Общие сведения о RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b1ff9-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
