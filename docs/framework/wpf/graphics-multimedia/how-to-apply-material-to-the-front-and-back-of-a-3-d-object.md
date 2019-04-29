---
title: Практическое руководство. Применение материала к лицевой и обратной стороне трехмерного объекта
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 1d3f6a0622b5e0ccccf14af99782bb78dfe87ccb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698974"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="6c739-102">Практическое руководство. Применение материала к лицевой и обратной стороне трехмерного объекта</span><span class="sxs-lookup"><span data-stu-id="6c739-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="6c739-103">В следующем примере показано, как применить <xref:System.Windows.Media.Media3D.Material> к лицевой и обратной стороне трехмерного объекта и анимация объекта для отображения обеих сторон объекта.</span><span class="sxs-lookup"><span data-stu-id="6c739-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="6c739-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Свойство <xref:System.Windows.Media.Media3D.GeometryModel3D> используется для применения красной <xref:System.Windows.Media.Brush> к передней части объекта и <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> свойство <xref:System.Windows.Media.Media3D.GeometryModel3D> используется для применения синим <xref:System.Windows.Media.Brush> к обратной стороне объекта.</span><span class="sxs-lookup"><span data-stu-id="6c739-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="6c739-105">В приведенном ниже коде показано применение материалов к объекту:</span><span class="sxs-lookup"><span data-stu-id="6c739-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="6c739-106">Пример</span><span class="sxs-lookup"><span data-stu-id="6c739-106">Example</span></span>  
 <span data-ttu-id="6c739-107">В следующем коде показано весь пример.</span><span class="sxs-lookup"><span data-stu-id="6c739-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6c739-108">См. также</span><span class="sxs-lookup"><span data-stu-id="6c739-108">See also</span></span>

- [<span data-ttu-id="6c739-109">Создание трехмерной сцены</span><span class="sxs-lookup"><span data-stu-id="6c739-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="6c739-110">Обзор трехмерной графики</span><span class="sxs-lookup"><span data-stu-id="6c739-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="6c739-111">Анимация свойств материалов в трехмерной сцене</span><span class="sxs-lookup"><span data-stu-id="6c739-111">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="6c739-112">Применение эмиссионного материала к трехмерному объекту</span><span class="sxs-lookup"><span data-stu-id="6c739-112">Apply Emissive Material to a 3-D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
