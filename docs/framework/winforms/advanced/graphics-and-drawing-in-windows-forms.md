---
title: Объекты Graphics и Drawing в Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 08f87436ade62bb54295b012a1c24dc177ea9667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938181"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="77d8f-102">Объекты Graphics и Drawing в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77d8f-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="77d8f-103">Среда CLR использует расширенную реализацию интерфейса графических устройств Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) под названием [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="77d8f-104">С помощью [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] можно создавать графические элементы, рисовать текст и управлять графическими изображениями как объектами.</span><span class="sxs-lookup"><span data-stu-id="77d8f-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="77d8f-105">Интерфейс [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] отличается высоким быстродействием и удобен в использовании.</span><span class="sxs-lookup"><span data-stu-id="77d8f-105">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is designed to offer performance and ease of use.</span></span> <span data-ttu-id="77d8f-106">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] можно использовать для отрисовки графических изображений в формах и элементах управления Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="77d8f-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="77d8f-107">Хотя [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] нельзя использовать непосредственно в веб-формах, графические изображения можно выводить через элемент управления веб-сервера Image.</span><span class="sxs-lookup"><span data-stu-id="77d8f-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="77d8f-108">В этом разделе описаны основы программирования с использованием [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="77d8f-109">Хотя он не является полным справочником, в нем содержатся сведения об объектах <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush> и <xref:System.Drawing.Color> и способах выполнения таких задач, как рисование фигур, создание текста, отображение рисунков.</span><span class="sxs-lookup"><span data-stu-id="77d8f-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="77d8f-110">Дополнительные сведения см. в разделе [GDI + ссылку](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="77d8f-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="77d8f-111">Если вы хотите немедленно приступить к работе, см. статью [Приступая к программированию графики](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="77d8f-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="77d8f-112">Она содержит разделы, посвященные использованию кода для рисования линий, фигур, текста и других элементов в формах Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="77d8f-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77d8f-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="77d8f-113">In This Section</span></span>  
 [<span data-ttu-id="77d8f-114">Общие сведения о графике</span><span class="sxs-lookup"><span data-stu-id="77d8f-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="77d8f-115">Общие сведения об управляемых классах, связанных с графикой.</span><span class="sxs-lookup"><span data-stu-id="77d8f-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="77d8f-116">Управляемый код GDI+</span><span class="sxs-lookup"><span data-stu-id="77d8f-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="77d8f-117">Сведения об управляемых классах [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="77d8f-118">Использование управляемых графических классов</span><span class="sxs-lookup"><span data-stu-id="77d8f-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="77d8f-119">Демонстрируется выполнение различных задач с помощью управляемых классов [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="77d8f-120">Ссылка</span><span class="sxs-lookup"><span data-stu-id="77d8f-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="77d8f-121">Доступ к основным графическим функциям [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="77d8f-122">Расширенные функциональные возможности для создания двухмерной и векторной графики.</span><span class="sxs-lookup"><span data-stu-id="77d8f-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="77d8f-123">Расширенный набор графических функций [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="77d8f-124">Расширенный набор типографических функций [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d8f-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="77d8f-125">Классы в этом пространстве имен позволяют создавать и использовать коллекции шрифтов.</span><span class="sxs-lookup"><span data-stu-id="77d8f-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="77d8f-126">Функции печати.</span><span class="sxs-lookup"><span data-stu-id="77d8f-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77d8f-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="77d8f-127">Related Sections</span></span>  
 [<span data-ttu-id="77d8f-128">Рисование и отрисовка пользовательского элемента управления</span><span class="sxs-lookup"><span data-stu-id="77d8f-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="77d8f-129">Подробные сведения о способах написания кода для рисования элементов управления.</span><span class="sxs-lookup"><span data-stu-id="77d8f-129">Details how to provide code for painting controls.</span></span>
