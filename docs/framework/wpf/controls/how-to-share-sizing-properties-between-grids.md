---
title: Практическое руководство. Совместное использование свойств размера между сетками
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: d5ab2ac612d55c8cbc34ae6d7d9d63b9f8aa23e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190344"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="3c7a1-102">Практическое руководство. Совместное использование свойств размера между сетками</span><span class="sxs-lookup"><span data-stu-id="3c7a1-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="3c7a1-103">В этом примере показано совместное использование данных о размере столбцов и строк для <xref:System.Windows.Controls.Grid> элементов, чтобы сохранить согласование размеров.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c7a1-104">Пример</span><span class="sxs-lookup"><span data-stu-id="3c7a1-104">Example</span></span>  
 <span data-ttu-id="3c7a1-105">В следующем примере представлены два <xref:System.Windows.Controls.Grid> элементы как дочерние элементы родительского элемента <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="3c7a1-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Присоединенное свойство <xref:System.Windows.Controls.Grid> определенные в родительском <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="3c7a1-107">Пример манипулирует значением свойства с помощью двух <xref:System.Windows.Controls.Button> элементов; каждый элемент представляет одно из значений свойства типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="3c7a1-108">Когда <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> имеет значение `true`, каждый член столбца или строки <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> совместно использует сведения о размере, независимо от того, содержимое строки или столбца.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="3c7a1-109">...</span><span class="sxs-lookup"><span data-stu-id="3c7a1-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="3c7a1-110">В следующем примере кода программной части обрабатывает методы, кнопки <xref:System.Windows.Controls.Primitives.ButtonBase.Click> вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="3c7a1-111">Пример записывает результаты вызовов этого метода для <xref:System.Windows.Controls.TextBlock> элементы, которые используют связанные методы получения для вывода новых значений свойств в виде строк.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3c7a1-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3c7a1-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="3c7a1-113">Общие сведения о панелях</span><span class="sxs-lookup"><span data-stu-id="3c7a1-113">Panels Overview</span></span>](panels-overview.md)
