---
title: Практическое руководство. Определение свойств ширины элемента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096879"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="32364-102">Практическое руководство. Определение свойств ширины элемента</span><span class="sxs-lookup"><span data-stu-id="32364-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="32364-103">Пример</span><span class="sxs-lookup"><span data-stu-id="32364-103">Example</span></span>  
 <span data-ttu-id="32364-104">В этом примере визуально показаны различия в поведении между четырьмя свойствами, связанными с шириной в отрисовки [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32364-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="32364-105"><xref:System.Windows.FrameworkElement> Класс предоставляет четыре свойства, описывающие характеристики ширины элемента.</span><span class="sxs-lookup"><span data-stu-id="32364-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="32364-106">Эти четыре свойства могут конфликтовать и когда это значение, которое имеет более высокий приоритет определяется следующим образом: <xref:System.Windows.FrameworkElement.MinWidth%2A> значение имеет приоритет над <xref:System.Windows.FrameworkElement.MaxWidth%2A> значение, которое в свою очередь имеет приоритет над <xref:System.Windows.FrameworkElement.Width%2A> значение.</span><span class="sxs-lookup"><span data-stu-id="32364-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="32364-107">Четвертое свойство <xref:System.Windows.FrameworkElement.ActualWidth%2A>доступно только для чтения и сообщает фактическую ширину, определенной при взаимодействии с процессом макета.</span><span class="sxs-lookup"><span data-stu-id="32364-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="32364-108">Следующие [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] примерах <xref:System.Windows.Shapes.Rectangle> элемент (`rect1`) как дочерний <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="32364-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="32364-109">Можно изменить свойства ширины <xref:System.Windows.Shapes.Rectangle> с помощью ряда <xref:System.Windows.Controls.ListBox> элементы, представляющие значения свойств <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, и <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="32364-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="32364-110">Таким образом визуально отображается приоритет каждого свойства.</span><span class="sxs-lookup"><span data-stu-id="32364-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="32364-111">В следующих примерах кода обработки событий, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="32364-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="32364-112">Каждый пользовательский метод принимает входные данные из <xref:System.Windows.Controls.ListBox>, анализирует его как <xref:System.Double>и применяет значение к указанному свойству ширины.</span><span class="sxs-lookup"><span data-stu-id="32364-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="32364-113">Значения ширины также преобразуются в строку и записываются в различные <xref:System.Windows.Controls.TextBlock> элементы (определение этих элементов не представлено в выбранной XAML).</span><span class="sxs-lookup"><span data-stu-id="32364-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="32364-114">Полный пример см. в разделе [примере сравнения свойств ширины](https://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="32364-114">For the complete sample, see [Width Properties Comparison Sample](https://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32364-115">См. также</span><span class="sxs-lookup"><span data-stu-id="32364-115">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="32364-116">Общие сведения о панелях</span><span class="sxs-lookup"><span data-stu-id="32364-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="32364-117">Определение свойств высоты элемента</span><span class="sxs-lookup"><span data-stu-id="32364-117">Set the Height Properties of an Element</span></span>](how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="32364-118">Пример сравнения свойств ширины</span><span class="sxs-lookup"><span data-stu-id="32364-118">Width Properties Comparison Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160050)
