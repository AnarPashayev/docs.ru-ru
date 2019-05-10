---
title: Практическое руководство. Печать формы Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 68dbad807e79f16bdc3cbdd3f55c62c3d6c854e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621302"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="37e07-102">Практическое руководство. Печать формы Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37e07-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="37e07-103">Как часть процесса разработки обычно требуется распечатать копию в форму Windows.</span><span class="sxs-lookup"><span data-stu-id="37e07-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="37e07-104">В следующем примере кода показано, как распечатать копию текущей формы с помощью <xref:System.Drawing.Graphics.CopyFromScreen%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="37e07-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37e07-105">Пример</span><span class="sxs-lookup"><span data-stu-id="37e07-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37e07-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="37e07-106">Compiling the Code</span></span>  
 <span data-ttu-id="37e07-107">Это полный пример кода, содержащий `Main` метод.</span><span class="sxs-lookup"><span data-stu-id="37e07-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="37e07-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="37e07-108">Robust Programming</span></span>  
 <span data-ttu-id="37e07-109">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="37e07-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="37e07-110">У вас нет разрешения на доступ к принтеру.</span><span class="sxs-lookup"><span data-stu-id="37e07-110">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="37e07-111">Нет нет установленных принтеров.</span><span class="sxs-lookup"><span data-stu-id="37e07-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="37e07-112">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="37e07-112">.NET Framework Security</span></span>  
 <span data-ttu-id="37e07-113">Чтобы запустить этот пример кода, необходимо разрешение на доступ к принтеру, используемые с компьютера.</span><span class="sxs-lookup"><span data-stu-id="37e07-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e07-114">См. также</span><span class="sxs-lookup"><span data-stu-id="37e07-114">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="37e07-115">Практическое руководство. Вывод изображений с использованием GDI +</span><span class="sxs-lookup"><span data-stu-id="37e07-115">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="37e07-116">Практическое руководство. Печать графических изображений в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37e07-116">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
