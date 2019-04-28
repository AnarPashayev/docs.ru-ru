---
title: Практическое руководство. Создание и использование холста
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001004"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="5a232-102">Практическое руководство. Создание и использование холста</span><span class="sxs-lookup"><span data-stu-id="5a232-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="5a232-103">В этом примере показано, как создать и использовать экземпляр <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5a232-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a232-104">Пример</span><span class="sxs-lookup"><span data-stu-id="5a232-104">Example</span></span>  
 <span data-ttu-id="5a232-105">Следующий пример явным образом располагает два <xref:System.Windows.Controls.TextBlock> элементов с помощью <xref:System.Windows.Controls.Canvas.SetTop%2A> и <xref:System.Windows.Controls.Canvas.SetLeft%2A> методы <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5a232-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="5a232-106">В примере также назначается <xref:System.Windows.Controls.Control.Background%2A> цвет `LightSteelBlue` для <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5a232-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a232-107">При использовании [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] позицию <xref:System.Windows.Controls.TextBlock> элементы, используют <xref:System.Windows.Controls.Canvas.Top%2A> и <xref:System.Windows.Controls.Canvas.Left%2A> свойства.</span><span class="sxs-lookup"><span data-stu-id="5a232-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5a232-108">См. также</span><span class="sxs-lookup"><span data-stu-id="5a232-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="5a232-109">Общие сведения о панелях</span><span class="sxs-lookup"><span data-stu-id="5a232-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="5a232-110">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="5a232-110">How-to Topics</span></span>](canvas-how-to-topics.md)
