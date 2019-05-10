---
title: Практическое руководство. Извлечение связанного с файлом значка в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: c3173a3fa756a3294154217f5cf0a13dbc8721f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645401"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="50fe9-102">Практическое руководство. Извлечение связанного с файлом значка в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50fe9-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="50fe9-103">Большое количество файлов с внедренными значки, которые обеспечивают визуальное представление сопоставленного типа файлов.</span><span class="sxs-lookup"><span data-stu-id="50fe9-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="50fe9-104">Например документы Microsoft Word содержит значок, который определяет их как документы Word.</span><span class="sxs-lookup"><span data-stu-id="50fe9-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="50fe9-105">При отображении файлов в список элементов управления, или таблицы, можно отобразить значок, представляющий тип файла рядом с именами файлов.</span><span class="sxs-lookup"><span data-stu-id="50fe9-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="50fe9-106">Вы можете сделать это с помощью <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="50fe9-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fe9-107">Пример</span><span class="sxs-lookup"><span data-stu-id="50fe9-107">Example</span></span>  
 <span data-ttu-id="50fe9-108">В следующем примере кода показано, как извлекать значок, связанный с файлом и отобразить имя файла и его значок в <xref:System.Windows.Forms.ListView> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="50fe9-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50fe9-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="50fe9-109">Compiling the Code</span></span>  
 <span data-ttu-id="50fe9-110">Чтобы скомпилировать этот пример:</span><span class="sxs-lookup"><span data-stu-id="50fe9-110">To compile the example:</span></span>  
  
- <span data-ttu-id="50fe9-111">Вставьте приведенный выше код в форму Windows и вызовите `ExtractAssociatedIconExample` метод из конструктора формы или <xref:System.Windows.Forms.Form.Load> метод обработки событий.</span><span class="sxs-lookup"><span data-stu-id="50fe9-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="50fe9-112">Необходимо убедиться, что форма импортирует <xref:System.IO> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="50fe9-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50fe9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="50fe9-113">See also</span></span>

- [<span data-ttu-id="50fe9-114">Изображения, точечные рисунки и метафайлы</span><span class="sxs-lookup"><span data-stu-id="50fe9-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="50fe9-115">Элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="50fe9-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
