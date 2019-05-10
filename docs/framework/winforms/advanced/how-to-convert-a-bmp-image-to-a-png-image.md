---
title: Практическое руководство. Преобразование изображение из формата BMP в формат PNG
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 59200941aa0f872a0bd99510bfaa8a8b878a9061
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648307"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="2b262-102">Практическое руководство. Преобразование изображение из формата BMP в формат PNG</span><span class="sxs-lookup"><span data-stu-id="2b262-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="2b262-103">Очень часто необходимо преобразовать изображение из одного формата в другой.</span><span class="sxs-lookup"><span data-stu-id="2b262-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="2b262-104">Это легко сделать, вызвав метод <xref:System.Drawing.Image.Save%2A> класса <xref:System.Drawing.Image> и указав в качестве параметра <xref:System.Drawing.Imaging.ImageFormat> нужный формат файла.</span><span class="sxs-lookup"><span data-stu-id="2b262-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b262-105">Пример</span><span class="sxs-lookup"><span data-stu-id="2b262-105">Example</span></span>  
 <span data-ttu-id="2b262-106">В примере ниже изображение в формате BMP загружается из типа и сохраняется в формате PNG.</span><span class="sxs-lookup"><span data-stu-id="2b262-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2b262-107">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="2b262-107">Compiling the Code</span></span>  
 <span data-ttu-id="2b262-108">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="2b262-108">This example requires:</span></span>  
  
- <span data-ttu-id="2b262-109">приложение Windows Forms;</span><span class="sxs-lookup"><span data-stu-id="2b262-109">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="2b262-110">ссылка на пространство имен `System.Drawing.Imaging`.</span><span class="sxs-lookup"><span data-stu-id="2b262-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b262-111">См. также</span><span class="sxs-lookup"><span data-stu-id="2b262-111">See also</span></span>

- [<span data-ttu-id="2b262-112">Практическое руководство. Получение списка установленных кодировщиков</span><span class="sxs-lookup"><span data-stu-id="2b262-112">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="2b262-113">Применение кодировщиков и декодеров изображений в управляемом GDI+</span><span class="sxs-lookup"><span data-stu-id="2b262-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="2b262-114">Типы растровых изображений</span><span class="sxs-lookup"><span data-stu-id="2b262-114">Types of Bitmaps</span></span>](types-of-bitmaps.md)
