---
title: Практическое руководство. Вызов страничной функции
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: e7c7c5ef98feeb4c5557295d92a8b219d9799865
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364152"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="a625d-102">Практическое руководство. Вызов страничной функции</span><span class="sxs-lookup"><span data-stu-id="a625d-102">How to: Call a Page Function</span></span>
<span data-ttu-id="a625d-103">В этом примере показано, как вызвать функцию страницы из [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] страницы.</span><span class="sxs-lookup"><span data-stu-id="a625d-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a625d-104">Пример</span><span class="sxs-lookup"><span data-stu-id="a625d-104">Example</span></span>  
 <span data-ttu-id="a625d-105">Можно переходить к функции страницы с помощью [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], точно так же, как и при переходе на страницу.</span><span class="sxs-lookup"><span data-stu-id="a625d-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="a625d-106">Эти действия показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a625d-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="a625d-107">Если необходимо передать данные в функцию страницы, можно создать ее экземпляр и передать данные путем установки свойства.</span><span class="sxs-lookup"><span data-stu-id="a625d-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="a625d-108">Или, как показано в следующем примере, можно передать данные с помощью конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="a625d-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="a625d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="a625d-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
