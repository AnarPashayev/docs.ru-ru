---
title: Практическое руководство. Заливка области с помощью видео
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: be09d1310847cd7214ea795a704c25d994f07b7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151181"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="8b3dc-102">Практическое руководство. Заливка области с помощью видео</span><span class="sxs-lookup"><span data-stu-id="8b3dc-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="8b3dc-103">В этом примере показано, как заливка области с медиа-носителями.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="8b3dc-104">Закраска области с медиа-носителями один из способов является использование <xref:System.Windows.Controls.MediaElement> вместе с <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8b3dc-105">Используйте <xref:System.Windows.Controls.MediaElement> для загрузки и воспроизведения мультимедиа и затем использовать его для задания <xref:System.Windows.Media.VisualBrush.Visual%2A> свойство <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8b3dc-106">Затем можно использовать <xref:System.Windows.Media.VisualBrush> для закраски области с загруженным мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b3dc-107">Пример</span><span class="sxs-lookup"><span data-stu-id="8b3dc-107">Example</span></span>  
 <span data-ttu-id="8b3dc-108">В следующем примере используется <xref:System.Windows.Controls.MediaElement> и <xref:System.Windows.Media.VisualBrush> для закрашивания <xref:System.Windows.Controls.TextBlock.Foreground%2A> из <xref:System.Windows.Controls.TextBlock> элемента управления с видео.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="8b3dc-109">В этом примере устанавливается <xref:System.Windows.Controls.MediaElement.IsMuted%2A> свойство <xref:System.Windows.Controls.MediaElement> для `true` таким образом, чтобы отключить звук.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="8b3dc-110">Пример</span><span class="sxs-lookup"><span data-stu-id="8b3dc-110">Example</span></span>  
 <span data-ttu-id="8b3dc-111">Так как <xref:System.Windows.Media.VisualBrush> наследует от <xref:System.Windows.Media.TileBrush> класс, он предоставляет несколько режимов заполнения.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="8b3dc-112">Установив <xref:System.Windows.Media.TileBrush.TileMode%2A> свойство <xref:System.Windows.Media.VisualBrush> для <xref:System.Windows.Media.TileMode.Tile> и установив его <xref:System.Windows.Media.TileBrush.Viewport%2A> свойства со значением меньше, чем область закрашивания, можно создать шаблон заполнения.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="8b3dc-113">Следующий пример идентичен предыдущему примеру, за исключением случаев, <xref:System.Windows.Media.VisualBrush> создает шаблон из видео.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="8b3dc-114">Сведения о том, как добавить файл содержимого, такие как файл мультимедиа в приложение, см. в разделе [ресурса приложения WPF, содержимое и файлы данных](../app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="8b3dc-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="8b3dc-115">При добавлении файла мультимедиа, необходимо добавить его как файл содержимого, а не как файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8b3dc-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3dc-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8b3dc-116">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="8b3dc-117">Заполнение с использованием изображений, рисунков и визуальных элементов</span><span class="sxs-lookup"><span data-stu-id="8b3dc-117">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="8b3dc-118">Общие сведения об объекте TileBrush</span><span class="sxs-lookup"><span data-stu-id="8b3dc-118">TileBrush Overview</span></span>](tilebrush-overview.md)
- [<span data-ttu-id="8b3dc-119">Общие сведения о мультимедиа</span><span class="sxs-lookup"><span data-stu-id="8b3dc-119">Multimedia Overview</span></span>](multimedia-overview.md)
