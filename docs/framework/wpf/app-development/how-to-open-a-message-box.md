---
title: Практическое руководство. Отображение окна сообщения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: cf7534cdee5e17d53e95294573023d660135e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947697"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="be3e7-102">Практическое руководство. Отображение окна сообщения</span><span class="sxs-lookup"><span data-stu-id="be3e7-102">How to: Open a Message Box</span></span>
<span data-ttu-id="be3e7-103">В этом примере показано, как открыть окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="be3e7-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be3e7-104">Пример</span><span class="sxs-lookup"><span data-stu-id="be3e7-104">Example</span></span>  
 <span data-ttu-id="be3e7-105">Окно сообщения — это готовое модальное диалоговое окно для отображения сведений для пользователей.</span><span class="sxs-lookup"><span data-stu-id="be3e7-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="be3e7-106">Открывается окно сообщения путем вызова статического <xref:System.Windows.MessageBox.Show%2A> метод <xref:System.Windows.MessageBox> класса.</span><span class="sxs-lookup"><span data-stu-id="be3e7-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="be3e7-107">Когда <xref:System.Windows.MessageBox.Show%2A> является именем, сообщение, передается с помощью параметра строки.</span><span class="sxs-lookup"><span data-stu-id="be3e7-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="be3e7-108">Несколько перегрузок <xref:System.Windows.MessageBox.Show%2A> дают возможность настраивать, как будет выглядеть окно сообщения (см. в разделе <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="be3e7-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="be3e7-109">См. также</span><span class="sxs-lookup"><span data-stu-id="be3e7-109">See also</span></span>

- [<span data-ttu-id="be3e7-110">Пример MessageBox</span><span class="sxs-lookup"><span data-stu-id="be3e7-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
