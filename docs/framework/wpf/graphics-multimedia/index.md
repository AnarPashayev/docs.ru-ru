---
title: Графика и мультимедиа
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 58ee58577b9ff71112103abb4d33c8b85d3c806f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786171"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="46afe-102">Графика и мультимедиа</span><span class="sxs-lookup"><span data-stu-id="46afe-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="46afe-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] обеспечивает поддержку мультимедиа, векторную графику, анимацию и композицию содержимого, что упрощает для разработчиков создание интересных пользовательских интерфейсов и содержимого.</span><span class="sxs-lookup"><span data-stu-id="46afe-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="46afe-104">С помощью [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] можно создать векторную графику или сложную анимацию и интегрировать мультимедиа в приложения.</span><span class="sxs-lookup"><span data-stu-id="46afe-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="46afe-105">В этом разделе представлены возможности графики, анимации и мультимедиа в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], которые позволяют добавлять в приложения рисунки, эффекты перехода, звук и видео.</span><span class="sxs-lookup"><span data-stu-id="46afe-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="46afe-106">Использование типов WPF в службе Windows настоятельно не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="46afe-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="46afe-107">При попытке использовать типы WPF в службе Windows, службы могут не работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="46afe-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="46afe-108">Новые графические и мультимедийные возможности в WPF 4</span><span class="sxs-lookup"><span data-stu-id="46afe-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="46afe-109">В части графики и анимации были сделаны некоторые изменения.</span><span class="sxs-lookup"><span data-stu-id="46afe-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="46afe-110">Округление макета</span><span class="sxs-lookup"><span data-stu-id="46afe-110">Layout Rounding</span></span>

  <span data-ttu-id="46afe-111">Когда граница объекта попадает в середину пикселя устройства, не зависящая от разрешения система графики может создавать артефакты отрисовки, например нечеткие или полупрозрачные границы.</span><span class="sxs-lookup"><span data-stu-id="46afe-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="46afe-112">Предыдущие версии WPF для обработки таких случаев включали функцию привязки пикселей.</span><span class="sxs-lookup"><span data-stu-id="46afe-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="46afe-113">В Silverlight 2 появилось округление макета, являющееся другим способом перемещения элементов так, чтобы границы попадали между пикселями.</span><span class="sxs-lookup"><span data-stu-id="46afe-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="46afe-114">Теперь WPF поддерживает округление макета с помощью <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> вложенного свойства зависимостей <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="46afe-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="46afe-115">Кэшированная композиция</span><span class="sxs-lookup"><span data-stu-id="46afe-115">Cached Composition</span></span>

  <span data-ttu-id="46afe-116">С помощью нового <xref:System.Windows.Media.BitmapCache> и <xref:System.Windows.Media.BitmapCacheBrush> классы, можно кэшировать сложной частью визуального дерева как растровое изображение и значительно уменьшить время отрисовки.</span><span class="sxs-lookup"><span data-stu-id="46afe-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="46afe-117">Растровое изображение продолжает реагировать на действия пользователя, например на щелчки мыши, и им можно рисовать на других элементах, как любой кистью.</span><span class="sxs-lookup"><span data-stu-id="46afe-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="46afe-118">Поддержка построителя текстур 3</span><span class="sxs-lookup"><span data-stu-id="46afe-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="46afe-119">WPF 4 строится на основе <xref:System.Windows.Media.Effects.ShaderEffect> реализованной в WPF 3.5 SP1, позволяя приложениям записывать эффекты с помощью построителя текстуры (PS) версии 3.0.</span><span class="sxs-lookup"><span data-stu-id="46afe-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="46afe-120">Шейдерная модель PS 3.0 сложнее, чем PS 2.0, что позволяет реализовать гораздо больше эффектов на поддерживаемом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="46afe-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="46afe-121">Функции плавности</span><span class="sxs-lookup"><span data-stu-id="46afe-121">Easing Functions</span></span>

  <span data-ttu-id="46afe-122">Можно усовершенствовать анимацию с помощью функций плавности, которые обеспечивают дополнительный контроль над поведением анимации.</span><span class="sxs-lookup"><span data-stu-id="46afe-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="46afe-123">Например, можно применить <xref:System.Windows.Media.Animation.ElasticEase> к анимации, чтобы придать анимации быстроту.</span><span class="sxs-lookup"><span data-stu-id="46afe-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="46afe-124">Дополнительные сведения см. в описании типов плавности <xref:System.Windows.Media.Animation> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="46afe-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="46afe-125">Графика и отрисовка</span><span class="sxs-lookup"><span data-stu-id="46afe-125">Graphics and Rendering</span></span>

<span data-ttu-id="46afe-126">WPF включает поддержку двумерной графики высокого качества.</span><span class="sxs-lookup"><span data-stu-id="46afe-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="46afe-127">Возможности включают кисти, геометрические объекты, изображения, фигуры и преобразования.</span><span class="sxs-lookup"><span data-stu-id="46afe-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="46afe-128">Дополнительные сведения см. в разделе [Графика](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="46afe-129">Отрисовка графических элементов основана на <xref:System.Windows.Media.Visual> класса.</span><span class="sxs-lookup"><span data-stu-id="46afe-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="46afe-130">Структура визуальных объектов на экране описывается визуальным деревом.</span><span class="sxs-lookup"><span data-stu-id="46afe-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="46afe-131">Дополнительные сведения см. в разделе [Общие сведения об отрисовке графики в WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="46afe-132">Двумерные фигуры</span><span class="sxs-lookup"><span data-stu-id="46afe-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="46afe-133">предоставляет библиотеку стандартных векторных фигур [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], таких как прямоугольники и эллипсы, показанные на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="46afe-133">provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Схема отображение эллипсы и прямоугольники.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="46afe-135">Эти встроенные фигуры [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] являются не просто фигурами: это программируемые элементы, в которых реализованы многие возможности, ожидаемые от наиболее распространенных элементов управления, включая клавиатуру и мышь.</span><span class="sxs-lookup"><span data-stu-id="46afe-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="46afe-136">В следующем примере показано, как обрабатывать <xref:System.Windows.UIElement.MouseUp> события, возникающего при щелчке <xref:System.Windows.Shapes.Ellipse> элемент.</span><span class="sxs-lookup"><span data-stu-id="46afe-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

<span data-ttu-id="46afe-137">На следующем рисунке показан результат выполнения предыдущей разметки [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] и кода.</span><span class="sxs-lookup"><span data-stu-id="46afe-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Окно сообщения, сообщение, «You clicked the ellipse!»](./media/index/messagebox-text-output.png)

<span data-ttu-id="46afe-139">Более подробную информацию см. в разделе [Обзор фигур и базовых средств рисования в приложении WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="46afe-140">Вводный пример см. в разделе [Пример элементов-фигур](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="46afe-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="46afe-141">Двумерные геометрические объекты</span><span class="sxs-lookup"><span data-stu-id="46afe-141">2-D Geometries</span></span>

<span data-ttu-id="46afe-142">Когда фигур [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], предоставляемых [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], недостаточно, можно использовать поддержку [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] геометрических фигур и путей для создания собственных.</span><span class="sxs-lookup"><span data-stu-id="46afe-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="46afe-143">Ниже показано, как можно использовать геометрические объекты для создания фигур (например, кисти рисования) и обрезки других элементов [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46afe-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![Снимок экрана, показывающий, как можно использовать геометрические объекты для создания фигур.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="46afe-145">Более подробную информацию см. в разделе [Общие сведения о классе Geometry](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="46afe-146">Вводный пример в разделе [Примеры геометрических объектов](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="46afe-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="46afe-147">Двумерные эффекты</span><span class="sxs-lookup"><span data-stu-id="46afe-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="46afe-148">предоставляет библиотеку классов [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], которые можно использовать для создания различных эффектов.</span><span class="sxs-lookup"><span data-stu-id="46afe-148">provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="46afe-149">Возможности отрисовки в [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] для [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] позволяют рисовать элементы [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], имеющие градиентные заливки, растровые изображения, рисунки и видео, а также управлять ими с помощью вращения, масштабирования и наклона.</span><span class="sxs-lookup"><span data-stu-id="46afe-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="46afe-150">На следующем рисунке приведен пример многих эффектов, которых можно добиться с помощью кисти [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46afe-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![Иллюстрация различных кистей WPF и элементов заливкой.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="46afe-152">Более подробную информацию см. в разделе [Общие сведения о кистях WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="46afe-153">Вводный пример см. в разделе [Пример использования кистей](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="46afe-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="46afe-154">Трехмерная отрисовка</span><span class="sxs-lookup"><span data-stu-id="46afe-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="46afe-155">предоставляет набор возможностей отрисовки [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], которые интегрируются с поддержкой графики [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] в [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] для создания более интересного макета, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] и визуализации данных.</span><span class="sxs-lookup"><span data-stu-id="46afe-155">provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="46afe-156">С одной стороны, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] позволяет отрисовывать изображения [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] на поверхностях фигур [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], что показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="46afe-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>

![Снимок экрана: пример, показывающий трехмерных фигур с помощью различных текстур.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="46afe-158">Более подробную информацию см. в разделе [Обзор трехмерной графики](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="46afe-159">Вводный пример см. в разделе [Пример трехмерных тел](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="46afe-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="46afe-160">Анимация</span><span class="sxs-lookup"><span data-stu-id="46afe-160">Animation</span></span>

<span data-ttu-id="46afe-161">Использование анимации позволяет применять к элементам управления и графическим элементам такие эффекты, как увеличение, дрожание, вращение и исчезание, создавать интересные эффекты смены страниц и другие эффекты.</span><span class="sxs-lookup"><span data-stu-id="46afe-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="46afe-162">Поскольку [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] позволяет анимировать большинство свойств, можно анимировать не только большинство объектов [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], но и использовать [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] для анимации пользовательских объектов.</span><span class="sxs-lookup"><span data-stu-id="46afe-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![Снимок экрана анимированного куба.](./media/index/animate-custom-objects.png)

<span data-ttu-id="46afe-164">Более подробную информацию см. в разделе [Общие сведения об эффектах анимации](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="46afe-165">Вводный пример в разделе [Коллекция примеров анимации](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="46afe-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="46afe-166">Мультимедиа</span><span class="sxs-lookup"><span data-stu-id="46afe-166">Media</span></span>

<span data-ttu-id="46afe-167">Изображения, видео и аудио являются мультимедийными способами передачи информации и взаимодействия с пользователями.</span><span class="sxs-lookup"><span data-stu-id="46afe-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="46afe-168">Изображений</span><span class="sxs-lookup"><span data-stu-id="46afe-168">Images</span></span>

<span data-ttu-id="46afe-169">Изображения, которые включают значки, фоновые рисунки и даже части анимаций, являются одним из основных элементов большинства приложений.</span><span class="sxs-lookup"><span data-stu-id="46afe-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="46afe-170">Так как с изображениями приходится работать часто, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] предоставляет возможность работать с ними различными способами.</span><span class="sxs-lookup"><span data-stu-id="46afe-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="46afe-171">На следующем рисунке показан один из таких способов.</span><span class="sxs-lookup"><span data-stu-id="46afe-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="46afe-172">![Снимок экрана стилей](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="46afe-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="46afe-173">Более подробную информацию см. в разделе [Общие сведения об обработке изображений](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="46afe-174">Видео и звук</span><span class="sxs-lookup"><span data-stu-id="46afe-174">Video and Audio</span></span>

<span data-ttu-id="46afe-175">Одна из основных особенностей графических возможностей [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — встроенная поддержка работы с мультимедиа, что включает видео и аудио.</span><span class="sxs-lookup"><span data-stu-id="46afe-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="46afe-176">Следующий пример демонстрирует вставку в приложение медиапроигрывателя.</span><span class="sxs-lookup"><span data-stu-id="46afe-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="46afe-177"><xref:System.Windows.Controls.MediaElement> позволяет воспроизводить видео и аудио и достаточно расширяемым для простого создания пользовательских [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46afe-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>

<span data-ttu-id="46afe-178">Дополнительные сведения см. в разделе [Общие сведения о мультимедиа](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46afe-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46afe-179">См. также</span><span class="sxs-lookup"><span data-stu-id="46afe-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="46afe-180">Двумерная графика и изображения</span><span class="sxs-lookup"><span data-stu-id="46afe-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="46afe-181">Обзор фигур и базовых средств рисования в приложении WPF</span><span class="sxs-lookup"><span data-stu-id="46afe-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="46afe-182">Общие сведения о закраске сплошным цветом и градиентом</span><span class="sxs-lookup"><span data-stu-id="46afe-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="46afe-183">Заполнение с использованием изображений, рисунков и визуальных элементов</span><span class="sxs-lookup"><span data-stu-id="46afe-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="46afe-184">Анимации и практические руководства</span><span class="sxs-lookup"><span data-stu-id="46afe-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="46afe-185">Обзор трехмерной графики</span><span class="sxs-lookup"><span data-stu-id="46afe-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="46afe-186">Общие сведения о мультимедиа</span><span class="sxs-lookup"><span data-stu-id="46afe-186">Multimedia Overview</span></span>](multimedia-overview.md)
