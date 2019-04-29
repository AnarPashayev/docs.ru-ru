---
title: Практическое руководство. Использование пользовательского контекстного меню с элементом TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699179"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="4fff5-102">Практическое руководство. Использование пользовательского контекстного меню с элементом TextBox</span><span class="sxs-lookup"><span data-stu-id="4fff5-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="4fff5-103">В этом примере показано, как определить и реализовать простое пользовательское контекстное меню для <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="4fff5-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fff5-104">Пример</span><span class="sxs-lookup"><span data-stu-id="4fff5-104">Example</span></span>  
 <span data-ttu-id="4fff5-105">Следующие [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] примере определяется <xref:System.Windows.Controls.TextBox> элемент управления, который включает в себя пользовательского контекстного меню.</span><span class="sxs-lookup"><span data-stu-id="4fff5-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="4fff5-106">В контекстном меню определяется с помощью <xref:System.Windows.Controls.ContextMenu> элемент.</span><span class="sxs-lookup"><span data-stu-id="4fff5-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="4fff5-107">Само контекстное меню состоит из ряда <xref:System.Windows.Controls.MenuItem> элементов и <xref:System.Windows.Controls.Separator> элементов.</span><span class="sxs-lookup"><span data-stu-id="4fff5-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="4fff5-108">Каждый <xref:System.Windows.Controls.MenuItem> элемент определяет команду в контекстном меню; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> атрибут определяет отображаемый текст для команды меню и <xref:System.Windows.Controls.MenuItem.Click> атрибут задает метод обработчика для каждого пункта меню.</span><span class="sxs-lookup"><span data-stu-id="4fff5-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="4fff5-109"><xref:System.Windows.Controls.Separator> Элемент просто отображает разделяющую строку между предыдущей и последующей пунктов.</span><span class="sxs-lookup"><span data-stu-id="4fff5-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="4fff5-110">Пример</span><span class="sxs-lookup"><span data-stu-id="4fff5-110">Example</span></span>  
 <span data-ttu-id="4fff5-111">В следующем примере показано, код реализации предыдущего определения контекстного меню, а также код, который включает и отключает контекстного меню.</span><span class="sxs-lookup"><span data-stu-id="4fff5-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="4fff5-112"><xref:System.Windows.Controls.ContextMenu.Opened> Событие используется для динамического включения или отключения определенных команд в зависимости от текущего состояния <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="4fff5-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="4fff5-113">Чтобы восстановить контекстное меню по умолчанию, используйте <xref:System.Windows.DependencyObject.ClearValue%2A> метод, чтобы удалить значение <xref:System.Windows.FrameworkElement.ContextMenu%2A> свойства.</span><span class="sxs-lookup"><span data-stu-id="4fff5-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="4fff5-114">Чтобы полностью отключить контекстное меню, задайте <xref:System.Windows.FrameworkElement.ContextMenu%2A> свойство пустую ссылку (`Nothing` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4fff5-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="4fff5-115">См. также</span><span class="sxs-lookup"><span data-stu-id="4fff5-115">See also</span></span>

- [<span data-ttu-id="4fff5-116">Использование проверки орфографии с помощью контекстного меню</span><span class="sxs-lookup"><span data-stu-id="4fff5-116">Use Spell Checking with a Context Menu</span></span>](how-to-use-spell-checking-with-a-context-menu.md)
- [<span data-ttu-id="4fff5-117">Общие сведения о TextBox</span><span class="sxs-lookup"><span data-stu-id="4fff5-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="4fff5-118">Общие сведения о RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4fff5-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
