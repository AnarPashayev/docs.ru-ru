---
title: Анализ текстовых файлов с помощью объекта TextFieldParser (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 70848e2d53ec4bdb031f73286f2c5be9a7e19387
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813500"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="f3771-102">Анализ текстовых файлов с помощью объекта TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3771-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="f3771-103">Объект `TextFieldParser` позволяет анализировать и обрабатывать файлы очень большого размера, по своей структуре имеющие вид столбцов текста с разделителями, например файлы журнала или старые базы данных.</span><span class="sxs-lookup"><span data-stu-id="f3771-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="f3771-104">Анализ текстового файла с помощью объекта `TextFieldParser` похож на итерацию содержимого текстового файла, а метод анализа, связанный с извлечением полей текста, напоминает методы работы со строками, используемые для маркировки разделенных строк.</span><span class="sxs-lookup"><span data-stu-id="f3771-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="f3771-105">Анализ различных типов текстовых файлов</span><span class="sxs-lookup"><span data-stu-id="f3771-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="f3771-106">Текстовые файлы могут иметь поля различной ширины, разделенные тем или иными символом, например запятой или знаком табуляции.</span><span class="sxs-lookup"><span data-stu-id="f3771-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="f3771-107">Определите `TextFieldType` и разделитель, как в следующем примере, в котором с помощью метода `SetDelimiters` определяется текстовый файл со знаком табуляции в качестве разделителя:</span><span class="sxs-lookup"><span data-stu-id="f3771-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f3771-108">Другие текстовые файлы могут иметь поля фиксированной ширины.</span><span class="sxs-lookup"><span data-stu-id="f3771-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="f3771-109">В этом случае необходимо определить `TextFieldType` как `FixedWidth` и задать ширину каждого поля, как в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="f3771-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="f3771-110">В этом примере столбцы текста определяются с помощью метода `SetFieldWidths`: первый столбец имеет ширину 5 символов, второй — 10, третий — 11, а четвертый столбец имеет переменную ширину.</span><span class="sxs-lookup"><span data-stu-id="f3771-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f3771-111">После определения формата можно обработать весь файл в цикле, используя для обработки каждой строки метод `ReadFields`.</span><span class="sxs-lookup"><span data-stu-id="f3771-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="f3771-112">Если поле не соответствует указанному формату, создается исключение <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>.</span><span class="sxs-lookup"><span data-stu-id="f3771-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="f3771-113">При возникновении таких исключений в свойства `ErrorLine` и `ErrorLineNumber` записывается текст, вызвавший исключение, и номер строки, в которой находится этот текст.</span><span class="sxs-lookup"><span data-stu-id="f3771-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="f3771-114">Анализ файлов с содержимым в нескольких форматах</span><span class="sxs-lookup"><span data-stu-id="f3771-114">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="f3771-115">Метод `PeekChars` объекта `TextFieldParser` можно использовать для проверки каждого поля до его чтения, что позволяет определить несколько форматов для полей и отреагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="f3771-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="f3771-116">Дополнительные сведения см. в разделе [Как Чтение из текстовых файлов различных форматов](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="f3771-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3771-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f3771-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
