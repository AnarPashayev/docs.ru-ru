---
title: Практическое руководство. Создание трехмерной сцены
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: a431b78993d197dac99f0b6e365823acb295f0b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611638"
---
# <a name="how-to-create-a-3-d-scene"></a>Практическое руководство. Создание трехмерной сцены
В этом примере демонстрируется создание трехмерного объекта, который выглядит как плоский листа бумаги, вращающийся. Объект <xref:System.Windows.Controls.Viewport3D> вместе с следующие компоненты, используются для создания этой простой трехмерной сцены:  
  
- Камера создается с помощью <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Камеры указывает, какая часть трехмерной сцены можно просматривать.  
  
- Сетка создается для задания формы трехмерного объекта (лист бумаги) с помощью <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> свойство <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Материал указывается отображаемый на поверхности объекта (линейного градиента в этом образце) с помощью <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> свойство <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Источник света создается для освещения объекта с помощью <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Пример  
 В приведенном ниже коде показано, как создание трехмерной сцены в XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Пример  
 В приведенном ниже коде показано создание одной и той же трехмерной сцены в процедурном коде.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>См. также

- [Обзор трехмерной графики](3-d-graphics-overview.md)
