---
title: Практическое руководство. Создание контурного текста
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776770"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="c3cf7-102">Практическое руководство. Создание контурного текста</span><span class="sxs-lookup"><span data-stu-id="c3cf7-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="c3cf7-103">В большинстве случаев при добавлении декоративных элементов в текстовые строки в вашей [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] приложения, вы используете текст в виде коллекции дискретных символов или глифов.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="c3cf7-104">Например, можно создать кисть линейного градиента и применить его к <xref:System.Windows.Controls.Control.Foreground%2A> свойство <xref:System.Windows.Controls.TextBox> объекта.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="c3cf7-105">При отображении или измените текстовое поле, кисти линейного градиента применяется автоматически в текущий набор символов в текстовой строке.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Текст, отображенный при помощи кисти линейного градиента](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 <span data-ttu-id="c3cf7-107">Тем не менее, можно также преобразовать текст в <xref:System.Windows.Media.Geometry> объектами, позволяет создавать другие типы визуально форматированного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="c3cf7-108">Например, можно создать <xref:System.Windows.Media.Geometry> объект, основанный на контуре строки текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Оконтуривание текста с использованием кисти линейного градиента](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="c3cf7-110">Если текст преобразуется в <xref:System.Windows.Media.Geometry> объекта, он больше не является набором символов — изменение символов в текстовой строке невозможно.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="c3cf7-111">Тем не менее можно повлиять на внешний вид преобразованного текст, изменив его свойства штриха и заливки.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="c3cf7-112">Штрих — это контур преобразованного текста; заливка — это область внутри контура преобразованного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="c3cf7-113">Следующие примеры иллюстрируют несколько способов создания визуальных эффектов посредством изменения штриха и заливки преобразованного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Текст с различными цветами для заполнения штриха](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Текст с кистью изображения, примененной к штриху](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="c3cf7-116">Можно также изменить ограничивающий прямоугольник или выделения преобразованного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="c3cf7-117">Следующий пример иллюстрирует способ создания визуальных эффектов посредством изменения штриха и выделения преобразованного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-117">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Текст с кистью изображения, примененной для вычерчивания и выделения](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="c3cf7-119">Пример</span><span class="sxs-lookup"><span data-stu-id="c3cf7-119">Example</span></span>  
 <span data-ttu-id="c3cf7-120">Ключ, чтобы преобразовать текст в <xref:System.Windows.Media.Geometry> объекта заключается в использовании <xref:System.Windows.Media.FormattedText> объекта.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="c3cf7-121">После создания этот объект можно использовать <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> и <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> методы, чтобы преобразовать текст в <xref:System.Windows.Media.Geometry> объектов.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="c3cf7-122">Первый метод возвращает геометрию форматированного текста. Второй метод возвращает ограничивающий прямоугольник геометрии форматированного текста.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="c3cf7-123">В следующем примере кода показано, как создать <xref:System.Windows.Media.FormattedText> объекта и извлечение геометрических форм форматированного текста и его ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="c3cf7-124">Чтобы отобразить извлеченные <xref:System.Windows.Media.Geometry> объектов, необходимо получить доступ к <xref:System.Windows.Media.DrawingContext> объекта, который отображает преобразованный текст.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="c3cf7-125">В этих примерах кода это делается путем создания объекта пользовательского элемента управления, производный от класса, поддерживающего пользовательской отрисовки.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-125">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="c3cf7-126">Для отображения <xref:System.Windows.Media.Geometry> объектов в пользовательском элементе управления, переопределите для <xref:System.Windows.UIElement.OnRender%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="c3cf7-127">Переопределенный метод должен использовать <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> метод для отображения <xref:System.Windows.Media.Geometry> объектов.</span><span class="sxs-lookup"><span data-stu-id="c3cf7-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="c3cf7-128">Источник объекта пример настраиваемого пользовательского элемента управления, см. в разделе [OutlineTextControl.cs для C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) и [OutlineTextControl.vb для Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="c3cf7-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c3cf7-129">См. также</span><span class="sxs-lookup"><span data-stu-id="c3cf7-129">See also</span></span>

- [<span data-ttu-id="c3cf7-130">Рисование форматированного текста</span><span class="sxs-lookup"><span data-stu-id="c3cf7-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
