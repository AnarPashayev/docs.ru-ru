---
title: Практическое руководство. Печать многостраничных текстовых файлов в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931793"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Практическое руководство. Печать многостраничных текстовых файлов в Windows Forms
В приложениях Windows очень часто используется печать текста. Класс <xref:System.Drawing.Graphics> предоставляет методы для рисования объектов (графических или текстовых) на таких устройствах, как экран или принтер.  
  
> [!NOTE]
> Методы <xref:System.Windows.Forms.TextRenderer.DrawText%2A> класса <xref:System.Windows.Forms.TextRenderer> не поддерживаются для печати. Для рисования текста в целях печати следует всегда использовать методы <xref:System.Drawing.Graphics.DrawString%2A> класса <xref:System.Drawing.Graphics>, как показано в примере кода ниже.  
  
### <a name="to-print-text"></a>Печать текста  
  
1. Добавьте в форму компонент <xref:System.Drawing.Printing.PrintDocument> и строку.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Для печати документа укажите его в качестве значения свойства <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>, а затем откройте и прочтите содержимое документа до добавленной ранее строки.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. Чтобы вычислить длину строки и число строк на страницу, в обработчике событий <xref:System.Drawing.Printing.PrintDocument.PrintPage> используйте свойство <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> класса <xref:System.Drawing.Printing.PrintPageEventArgs> и содержимое документа. Нарисовав очередную страницу, проверьте, является ли она последней, и установите соответствующим образом свойство <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> класса <xref:System.Drawing.Printing.PrintPageEventArgs> . Событие <xref:System.Drawing.Printing.PrintDocument.PrintPage> возникает до тех пор, пока значение свойства <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> не станет равно `false`. Кроме того, убедитесь в том, что событие <xref:System.Drawing.Printing.PrintDocument.PrintPage> связано со своим методом обработки событий.  
  
     В примере кода ниже обработчик событий используется для печати содержимого файла testPage.txt тем шрифтом, который используется в форме.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Вызовите метод <xref:System.Drawing.Printing.PrintDocument.Print%2A> для инициации события <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
- текстовый файл с именем testPage.txt, содержащий текст для печати и находящийся в корне диска C:\\; чтобы напечатать другой файл, измените код;  
  
- ссылки на сборки System, System.Windows.Forms и System.Drawing.  
  
- Сведения о создании этого примера из командной строки для Visual Basic или визуального элемента C#см. в разделе [Сборка из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [Сборка из командной строки с помощью csc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Этот пример можно также построить в Visual Studio, вставляя код в новый проект.  
  
## <a name="see-also"></a>См. также

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Поддержка печати в Windows Forms](windows-forms-print-support.md)
