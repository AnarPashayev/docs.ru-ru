---
title: Печать с помощью предварительного просмотра
description: Узнайте, как добавить в приложение службы предварительного просмотра, используя элемент управления Windows Forms PrintPreviewDialog.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621617"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="311b6-103">Практическое руководство. Печать в Windows Forms с использованием предварительного просмотра</span><span class="sxs-lookup"><span data-stu-id="311b6-103">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="311b6-104">При программировании с использованием Windows Forms в качестве дополнения к службам печати часто предлагается возможность предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="311b6-104">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="311b6-105">Легким способом добавления предварительного просмотра в приложение является использование элемента управления <xref:System.Windows.Forms.PrintPreviewDialog> в сочетании с логикой обработки событий <xref:System.Drawing.Printing.PrintDocument.PrintPage> для печати файла.</span><span class="sxs-lookup"><span data-stu-id="311b6-105">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="311b6-106">Предварительный просмотр текстового документа с помощью элемента управления PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="311b6-106">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="311b6-107">Добавьте в форму элемент управления <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>и две строки.</span><span class="sxs-lookup"><span data-stu-id="311b6-107">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="311b6-108">Укажите в качестве значения свойства <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> документ, который нужно напечатать, а затем откройте документ и прочтите его содержимое в строку, добавленную ранее.</span><span class="sxs-lookup"><span data-stu-id="311b6-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="311b6-109">Как и при печати документа, для расчета числа строк на странице и отрисовки содержимого документа в обработчике событий <xref:System.Drawing.Printing.PrintDocument.PrintPage> используется свойство <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> класса <xref:System.Drawing.Printing.PrintPageEventArgs> и содержимое файла.</span><span class="sxs-lookup"><span data-stu-id="311b6-109">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="311b6-110">Нарисовав очередную страницу, проверьте, является ли она последней, и установите соответствующим образом свойство <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> класса <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="311b6-110">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="311b6-111">Событие <xref:System.Drawing.Printing.PrintDocument.PrintPage> возникает до тех пор, пока значение свойства <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> не станет равно `false`.</span><span class="sxs-lookup"><span data-stu-id="311b6-111">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="311b6-112">После завершения отрисовки документа сбросьте строку, подлежащую отрисовке.</span><span class="sxs-lookup"><span data-stu-id="311b6-112">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="311b6-113">Кроме того, убедитесь в том, что событие <xref:System.Drawing.Printing.PrintDocument.PrintPage> связано со своим методом обработки событий.</span><span class="sxs-lookup"><span data-stu-id="311b6-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="311b6-114">Если поддержка печати уже реализована в приложении, то, возможно, шаги 2 и 3 были выполнены ранее.</span><span class="sxs-lookup"><span data-stu-id="311b6-114">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="311b6-115">В примере кода ниже обработчик событий используется для печати файла testPage.txt тем шрифтом, который используется в форме.</span><span class="sxs-lookup"><span data-stu-id="311b6-115">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="311b6-116">Присвойте свойству <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> элемента управления <xref:System.Windows.Forms.PrintPreviewDialog> значение компонента <xref:System.Drawing.Printing.PrintDocument> в форме.</span><span class="sxs-lookup"><span data-stu-id="311b6-116">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="311b6-117">Вызовите метод <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> элемента управления <xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="311b6-117">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="311b6-118">Как правило, метод <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> вызывается из метода обработки событий <xref:System.Windows.Forms.Control.Click> кнопки.</span><span class="sxs-lookup"><span data-stu-id="311b6-118">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="311b6-119">Вызов метода <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> приводит к возникновению события <xref:System.Drawing.Printing.PrintDocument.PrintPage> и отрисовке выходных данных в элементе управления <xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="311b6-119">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="311b6-120">Когда пользователь нажимает на значок печати в диалоговом окне, событие <xref:System.Drawing.Printing.PrintDocument.PrintPage> вызывается снова. При этом выходные данные отправляются на принтер, а не в диалоговое окно предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="311b6-120">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="311b6-121">Вот почему в шаге 3 в конце процесса отрисовки сбрасывалась строка.</span><span class="sxs-lookup"><span data-stu-id="311b6-121">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="311b6-122">В примере ниже показан метод обработки событий <xref:System.Windows.Forms.Control.Click> для кнопки в форме.</span><span class="sxs-lookup"><span data-stu-id="311b6-122">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="311b6-123">Этот метод вызывает методы для чтения документа и вывода окна предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="311b6-123">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="311b6-124">Пример</span><span class="sxs-lookup"><span data-stu-id="311b6-124">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="311b6-125">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="311b6-125">Compiling the Code</span></span>  
 <span data-ttu-id="311b6-126">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="311b6-126">This example requires:</span></span>  
  
- <span data-ttu-id="311b6-127">ссылки на сборки System, System.Windows.Forms и System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="311b6-127">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311b6-128">См. также</span><span class="sxs-lookup"><span data-stu-id="311b6-128">See also</span></span>

- [<span data-ttu-id="311b6-129">Практическое руководство. Печать многостраничных текстовых файлов в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="311b6-129">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="311b6-130">Поддержка печати в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="311b6-130">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="311b6-131">Более безопасная печать в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="311b6-131">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
