---
title: Практическое руководство. Создание элемента сетки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: ebb9369da73bd595338e5b6ef42bda639bde6ed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001362"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="1ff4a-102">Практическое руководство. Создание элемента сетки</span><span class="sxs-lookup"><span data-stu-id="1ff4a-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="1ff4a-103">Пример</span><span class="sxs-lookup"><span data-stu-id="1ff4a-103">Example</span></span>  
 <span data-ttu-id="1ff4a-104">В следующем примере показано, как создать и использовать экземпляр <xref:System.Windows.Controls.Grid> либо при помощи [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] или кода.</span><span class="sxs-lookup"><span data-stu-id="1ff4a-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="1ff4a-105">В этом примере используются три <xref:System.Windows.Controls.ColumnDefinition> объектов и три <xref:System.Windows.Controls.RowDefinition> объектов для создания сетки, который принимает девять ячеек, как в рабочем листе.</span><span class="sxs-lookup"><span data-stu-id="1ff4a-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="1ff4a-106">Каждая ячейка содержит <xref:System.Windows.Controls.TextBlock> содержит элемент, который представляет данные, а верхняя строка <xref:System.Windows.Controls.TextBlock> с <xref:System.Windows.Controls.Grid.ColumnSpan%2A> свойства применен.</span><span class="sxs-lookup"><span data-stu-id="1ff4a-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="1ff4a-107">Показать границы каждой ячейки, <xref:System.Windows.Controls.Grid.ShowGridLines%2A> включено свойство.</span><span class="sxs-lookup"><span data-stu-id="1ff4a-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="1ff4a-108">Любой из этих подходов создаст пользовательский интерфейс, который всегда выглядит практически так же, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="1ff4a-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![Снимок экрана показан пользовательский интерфейс WPF, который содержит сетку разбить на три столбца.](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="1ff4a-112">См. также</span><span class="sxs-lookup"><span data-stu-id="1ff4a-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="1ff4a-113">Общие сведения о панелях</span><span class="sxs-lookup"><span data-stu-id="1ff4a-113">Panels Overview</span></span>](panels-overview.md)
