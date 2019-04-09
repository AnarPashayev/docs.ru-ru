---
title: Практическое руководство. Применение преобразования к тексту
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 46a57364e0c18cc4c9fe7884642cd0b718c20f31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208674"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="32fa6-102">Практическое руководство. Применение преобразования к тексту</span><span class="sxs-lookup"><span data-stu-id="32fa6-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="32fa6-103">Преобразования могут менять отображение текста в приложении.</span><span class="sxs-lookup"><span data-stu-id="32fa6-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="32fa6-104">В следующих примерах используются различные типы преобразований отрисовки влияющие на отображение текста в <xref:System.Windows.Controls.TextBlock> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="32fa6-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32fa6-105">Пример</span><span class="sxs-lookup"><span data-stu-id="32fa6-105">Example</span></span>  
 <span data-ttu-id="32fa6-106">В следующем примере показан текст, повернутый относительно заданной точки в двухмерной плоскости x-y.</span><span class="sxs-lookup"><span data-stu-id="32fa6-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Текст, повернутый с использованием RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="32fa6-108">В следующем примере кода используется <xref:System.Windows.Media.RotateTransform> вращение текста.</span><span class="sxs-lookup"><span data-stu-id="32fa6-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="32fa6-109"><xref:System.Windows.Media.RotateTransform.Angle%2A> Значение 90, поворачивает элемент на 90 градусов по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="32fa6-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="32fa6-110">В следующем примере показаны вторая строка текста, масштабированная на 150 % вдоль оси X, и третья строка текста, масштабированная на 150 % вдоль оси Y.</span><span class="sxs-lookup"><span data-stu-id="32fa6-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Текст, масштабируемый с использованием ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 <span data-ttu-id="32fa6-112">В следующем примере кода используется <xref:System.Windows.Media.ScaleTransform> для масштабирования текста из исходного размера.</span><span class="sxs-lookup"><span data-stu-id="32fa6-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="32fa6-113">Масштабирование текста не равнозначно увеличению шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="32fa6-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="32fa6-114">Размеры шрифта рассчитываются независимо друг от друга, чтобы обеспечить оптимальное разрешение для разных размеров.</span><span class="sxs-lookup"><span data-stu-id="32fa6-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="32fa6-115">В масштабированном тексте, с другой стороны, сохранены пропорции текста исходного размера.</span><span class="sxs-lookup"><span data-stu-id="32fa6-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="32fa6-116">В следующем примере показан текст, наклоненный вдоль оси X.</span><span class="sxs-lookup"><span data-stu-id="32fa6-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Текст, искаженный с использованием SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 <span data-ttu-id="32fa6-118">В следующем примере кода используется <xref:System.Windows.Media.SkewTransform> для наклона текста.</span><span class="sxs-lookup"><span data-stu-id="32fa6-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="32fa6-119">Отклонение (или срез) — это преобразование, которое неравномерно растягивает пространство координат.</span><span class="sxs-lookup"><span data-stu-id="32fa6-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="32fa6-120">В этом примере две текстовые строки, наклоненные на –30° и 30° вдоль оси X.</span><span class="sxs-lookup"><span data-stu-id="32fa6-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="32fa6-121">В следующем примере показан текст, преобразованный (или перемещенный) вдоль осей X и Y.</span><span class="sxs-lookup"><span data-stu-id="32fa6-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Смещение текста с использованием TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="32fa6-123">В следующем примере кода используется <xref:System.Windows.Media.TranslateTransform> для смещения текста.</span><span class="sxs-lookup"><span data-stu-id="32fa6-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="32fa6-124">В этом примере слегка смещенная копия текста под основным текстом создает эффект тени.</span><span class="sxs-lookup"><span data-stu-id="32fa6-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="32fa6-125"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Предоставляет широкий набор функций для создания эффектов тени.</span><span class="sxs-lookup"><span data-stu-id="32fa6-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="32fa6-126">Дополнительные сведения см. в разделе [Создание текста с тенью](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="32fa6-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fa6-127">См. также</span><span class="sxs-lookup"><span data-stu-id="32fa6-127">See also</span></span>

- [<span data-ttu-id="32fa6-128">Применение анимаций к тексту</span><span class="sxs-lookup"><span data-stu-id="32fa6-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
