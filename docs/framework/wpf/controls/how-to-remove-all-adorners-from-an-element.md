---
title: Практическое руководство. Удаление всех декоративных элементов из элемента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770777"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="c5cdc-102">Практическое руководство. Удаление всех декоративных элементов из элемента</span><span class="sxs-lookup"><span data-stu-id="c5cdc-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="c5cdc-103">В этом примере показано, как программным способом удаление всех декоративных элементов из указанного <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5cdc-104">Пример</span><span class="sxs-lookup"><span data-stu-id="c5cdc-104">Example</span></span>  
 <span data-ttu-id="c5cdc-105">Этот подробный пример кода удаляет всех графических элементов в массиве декоративных элементов, возвращенных <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="c5cdc-106">В этом примере происходит с графические <xref:System.Windows.UIElement> с именем *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="c5cdc-107">Если этот элемент указан в вызове <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> нет графических объектов, `null` возвращается.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="c5cdc-108">Этот код явно проверяет пустой массив и лучше всего подходит для приложений, где должен быть относительно распространенную пустой массив.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="c5cdc-109">Пример</span><span class="sxs-lookup"><span data-stu-id="c5cdc-109">Example</span></span>  
 <span data-ttu-id="c5cdc-110">Данный сжатый пример кода функционально эквивалентен подробному примеру, приведенному выше.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="c5cdc-111">Этот код явно не проверяет пустой массив, так что вполне возможно, <xref:System.NullReferenceException> может быть вызвано исключение.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="c5cdc-112">Этот код лучше всего подходит для приложений, где ожидается пустой массив довольно редки.</span><span class="sxs-lookup"><span data-stu-id="c5cdc-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="c5cdc-113">См. также</span><span class="sxs-lookup"><span data-stu-id="c5cdc-113">See also</span></span>

- [<span data-ttu-id="c5cdc-114">Общие сведения о декоративных элементах</span><span class="sxs-lookup"><span data-stu-id="c5cdc-114">Adorners Overview</span></span>](adorners-overview.md)
