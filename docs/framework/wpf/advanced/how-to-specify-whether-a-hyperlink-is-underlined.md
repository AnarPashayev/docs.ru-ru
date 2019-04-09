---
title: Практическое руководство. Определение того, подчеркнута ли ссылка
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 5718912e24a0697f209669b0ab4e7f4df1765ed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076319"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="96168-102">Практическое руководство. Определение того, подчеркнута ли ссылка</span><span class="sxs-lookup"><span data-stu-id="96168-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="96168-103"><xref:System.Windows.Documents.Hyperlink> Объект — это элемент содержимого потока встроенного уровня, позволяющим размещать гиперссылки в содержимом потока.</span><span class="sxs-lookup"><span data-stu-id="96168-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="96168-104">По умолчанию <xref:System.Windows.Documents.Hyperlink> использует <xref:System.Windows.TextDecoration> объекта для отображения подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="96168-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <xref:System.Windows.TextDecoration> <span data-ttu-id="96168-105">объекты могут быть производительность при создании, особенно в том случае, если имеется много <xref:System.Windows.Documents.Hyperlink> объектов.</span><span class="sxs-lookup"><span data-stu-id="96168-105">objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="96168-106">При внесении широкое использование <xref:System.Windows.Documents.Hyperlink> элементов, может потребоваться отображать подчеркивание только при возникновении события, такие как <xref:System.Windows.ContentElement.MouseEnter> событий.</span><span class="sxs-lookup"><span data-stu-id="96168-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="96168-107">В следующем примере подчеркивание ссылки «Мой MSN» является динамическим, то есть оно появляется только при <xref:System.Windows.ContentElement.MouseEnter> активируется событие.</span><span class="sxs-lookup"><span data-stu-id="96168-107">In the following example, the underline for the "My MSN" link is dynamic, that is, it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
  ![Гиперссылки, отображающие TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  

## <a name="example"></a><span data-ttu-id="96168-109">Пример</span><span class="sxs-lookup"><span data-stu-id="96168-109">Example</span></span>  
 <span data-ttu-id="96168-110">В следующем примере разметки демонстрируется <xref:System.Windows.Documents.Hyperlink> определен с подчеркиванием и без него:</span><span class="sxs-lookup"><span data-stu-id="96168-110">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="96168-111">В следующем образце кода демонстрируется создание подчеркивания для <xref:System.Windows.Documents.Hyperlink> на <xref:System.Windows.ContentElement.MouseEnter> событий и удалите его при <xref:System.Windows.ContentElement.MouseLeave> событий.</span><span class="sxs-lookup"><span data-stu-id="96168-111">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="96168-112">См. также</span><span class="sxs-lookup"><span data-stu-id="96168-112">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="96168-113">Улучшение производительности приложений WPF</span><span class="sxs-lookup"><span data-stu-id="96168-113">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="96168-114">Создание оформления текста</span><span class="sxs-lookup"><span data-stu-id="96168-114">Create a Text Decoration</span></span>](how-to-create-a-text-decoration.md)
