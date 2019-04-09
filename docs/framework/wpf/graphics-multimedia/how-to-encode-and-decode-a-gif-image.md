---
title: Практическое руководство. Кодирование и декодирование изображения в формате GIF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: 35bd08f0d5e4d2ee9b8731706c9f1d770d67f633
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124745"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="77d79-102">Практическое руководство. Кодирование и декодирование изображения в формате GIF</span><span class="sxs-lookup"><span data-stu-id="77d79-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="77d79-103">Следующие примеры показывают, как декодировать и кодировать [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] изображений, используя заданный <xref:System.Windows.Media.Imaging.GifBitmapDecoder> и <xref:System.Windows.Media.Imaging.GifBitmapEncoder> объектов.</span><span class="sxs-lookup"><span data-stu-id="77d79-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77d79-104">Пример</span><span class="sxs-lookup"><span data-stu-id="77d79-104">Example</span></span>  
 <span data-ttu-id="77d79-105">В этом примере показано, как декодировать [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] изображений с помощью <xref:System.Windows.Media.Imaging.GifBitmapDecoder> из <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="77d79-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="77d79-106">Пример</span><span class="sxs-lookup"><span data-stu-id="77d79-106">Example</span></span>  
 <span data-ttu-id="77d79-107">В этом примере показаны способы кодирования <xref:System.Windows.Media.Imaging.BitmapSource> в [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] изображений с помощью <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="77d79-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="77d79-108">См. также</span><span class="sxs-lookup"><span data-stu-id="77d79-108">See also</span></span>

- [<span data-ttu-id="77d79-109">Общие сведения об обработке изображений</span><span class="sxs-lookup"><span data-stu-id="77d79-109">Imaging Overview</span></span>](imaging-overview.md)
