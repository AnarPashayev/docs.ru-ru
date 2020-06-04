---
title: Создание исходного документа в формате Office Open XML
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410842"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="57e8c-102">Создание исходного документа Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e8c-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="57e8c-103">В этом разделе показано создание документа Office Open XML WordprocessingML, который используется в примерах этого учебника.</span><span class="sxs-lookup"><span data-stu-id="57e8c-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="57e8c-104">Если следовать приведенным ниже инструкциям, выходные данные будут соответствовать выходным данным каждого примера.</span><span class="sxs-lookup"><span data-stu-id="57e8c-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="57e8c-105">Тем не менее примеры в этом учебнике работают с любым допустимым документом WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="57e8c-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="57e8c-106">Чтобы создать документ, который используется в этом учебнике, необходимо иметь установленный выпуск 2007 системы Microsoft Office или более поздней версии либо Microsoft Office 2003 с пакетом обеспечения совместимости Microsoft Office для форматов файлов Word, Excel и PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="57e8c-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="57e8c-107">Создание документа WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="57e8c-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="57e8c-108">Создание документа WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="57e8c-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="57e8c-109">Создайте документ Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="57e8c-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="57e8c-110">Вставьте в новый документ следующий текст.</span><span class="sxs-lookup"><span data-stu-id="57e8c-110">Paste the following text into the new document:</span></span>  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. <span data-ttu-id="57e8c-111">Отформатируйте первую строку стилем «Заголовок 1».</span><span class="sxs-lookup"><span data-stu-id="57e8c-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="57e8c-112">Выберите строки, которые содержат код Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57e8c-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="57e8c-113">Первая строка начинается с ключевого слова `Imports`.</span><span class="sxs-lookup"><span data-stu-id="57e8c-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="57e8c-114">Последняя строка — "конечный класс".</span><span class="sxs-lookup"><span data-stu-id="57e8c-114">The last line is "End Class".</span></span> <span data-ttu-id="57e8c-115">Отформатируйте эти строки шрифтом courier.</span><span class="sxs-lookup"><span data-stu-id="57e8c-115">Format the lines with the courier font.</span></span> <span data-ttu-id="57e8c-116">Создайте из них новый стиль и присвойте ему имя «Code».</span><span class="sxs-lookup"><span data-stu-id="57e8c-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="57e8c-117">Наконец, выделите всю строку, содержащую выходные данные, и отформатируйте ее стилем `Code`.</span><span class="sxs-lookup"><span data-stu-id="57e8c-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="57e8c-118">Сохраните документ с именем SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="57e8c-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="57e8c-119">Если используется Microsoft Word 2003, в раскрывающемся списке **Тип файла** выберите **Документ Word 2007**.</span><span class="sxs-lookup"><span data-stu-id="57e8c-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e8c-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="57e8c-120">See also</span></span>

- [<span data-ttu-id="57e8c-121">Руководство. Управление содержимым в документе WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e8c-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
