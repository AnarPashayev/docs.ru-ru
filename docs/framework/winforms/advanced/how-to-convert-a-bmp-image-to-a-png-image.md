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
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Практическое руководство. Преобразование изображение из формата BMP в формат PNG
Очень часто необходимо преобразовать изображение из одного формата в другой. Это легко сделать, вызвав метод <xref:System.Drawing.Image.Save%2A> класса <xref:System.Drawing.Image> и указав в качестве параметра <xref:System.Drawing.Imaging.ImageFormat> нужный формат файла.  
  
## <a name="example"></a>Пример  
 В примере ниже изображение в формате BMP загружается из типа и сохраняется в формате PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
- приложение Windows Forms;  
  
- ссылка на пространство имен `System.Drawing.Imaging`.  
  
## <a name="see-also"></a>См. также

- [Практическое руководство. Получение списка установленных кодировщиков](how-to-list-installed-encoders.md)
- [Применение кодировщиков и декодеров изображений в управляемом GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
- [Типы растровых изображений](types-of-bitmaps.md)
