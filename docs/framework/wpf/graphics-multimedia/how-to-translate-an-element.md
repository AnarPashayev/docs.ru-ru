---
title: Практическое руководство. Перемещение элемента
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051446"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="3d3ce-102">Практическое руководство. Перемещение элемента</span><span class="sxs-lookup"><span data-stu-id="3d3ce-102">How to: Translate an Element</span></span>
<span data-ttu-id="3d3ce-103">В этом примере показано, как для переноса (перемещения) элемента с помощью <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="3d3ce-104"><xref:System.Windows.Media.TranslateTransform> Класс особенно полезен для перемещения элементов внутри панелей, которые не поддерживают абсолютное позиционирование.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="3d3ce-105">Например, применяя <xref:System.Windows.Media.TranslateTransform> для <xref:System.Windows.UIElement.RenderTransform%2A> свойства элемента, можно переместить элемент в пределах <xref:System.Windows.Controls.StackPanel> или <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="3d3ce-106">Используйте <xref:System.Windows.Media.TranslateTransform.X%2A> свойство <xref:System.Windows.Media.TranslateTransform> Чтобы задать интервал в пикселях для перемещения элемента вдоль оси x.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="3d3ce-107">Используйте <xref:System.Windows.Media.TranslateTransform.Y%2A> свойство, чтобы задать интервал в пикселях для перемещения элемента вдоль оси y.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="3d3ce-108">Наконец, примените <xref:System.Windows.Media.TranslateTransform> для <xref:System.Windows.UIElement.RenderTransform%2A> свойство элемента.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="3d3ce-109">В следующем примере используется <xref:System.Windows.Media.TranslateTransform> для перемещения элемента на 50 пикселей вправо и 50 пикселей вниз.</span><span class="sxs-lookup"><span data-stu-id="3d3ce-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d3ce-110">Пример</span><span class="sxs-lookup"><span data-stu-id="3d3ce-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="3d3ce-111">Полный пример см. в разделе [Примеры двумерных преобразований](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="3d3ce-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3ce-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3d3ce-112">See also</span></span>

- [<span data-ttu-id="3d3ce-113">Общие сведения о классах Transform</span><span class="sxs-lookup"><span data-stu-id="3d3ce-113">Transforms Overview</span></span>](transforms-overview.md)
