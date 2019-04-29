---
title: Практическое руководство. Улучшение производительности прокрутки ListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770868"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="1f2d7-102">Практическое руководство. Улучшение производительности прокрутки ListBox</span><span class="sxs-lookup"><span data-stu-id="1f2d7-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="1f2d7-103">Если <xref:System.Windows.Controls.ListBox> содержит много элементов, ответ пользовательского интерфейса может выполняться медленно, при прокрутке <xref:System.Windows.Controls.ListBox> , используя колесико мыши или перетаскивания ползунка полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="1f2d7-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="1f2d7-104">Можно повысить производительность <xref:System.Windows.Controls.ListBox> при прокрутке, задав `VirtualizingStackPanel.VirtualizationMode` вложенное свойство, чтобы <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f2d7-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f2d7-105">Пример</span><span class="sxs-lookup"><span data-stu-id="1f2d7-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="1f2d7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1f2d7-106">Description</span></span>  
<span data-ttu-id="1f2d7-107">В следующем примере создается <xref:System.Windows.Controls.ListBox> и задает `VirtualizingStackPanel.VirtualizationMode` вложенное свойство, чтобы <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> для повышения производительности при прокрутке.</span><span class="sxs-lookup"><span data-stu-id="1f2d7-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="1f2d7-108">Код</span><span class="sxs-lookup"><span data-stu-id="1f2d7-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="1f2d7-109">В следующем примере показано данные в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="1f2d7-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
