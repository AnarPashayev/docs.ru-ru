---
title: Практическое руководство. Чтение из текстовых файлов с фиксированной шириной полей
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 77b2e0a4ebe36b68501f821ef5731935ee3b16a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411633"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="ea173-102">Практическое руководство. Чтение из текстовых файлов с фиксированной шириной полей в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea173-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="ea173-103">Объект `TextFieldParser` позволяет легко и эффективно анализировать структурированные текстовые файлы, например файлы журналов.</span><span class="sxs-lookup"><span data-stu-id="ea173-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="ea173-104">Свойство `TextFieldType` определяет, является ли анализируемый файл файлом с разделителями или с полями фиксированной ширины текста.</span><span class="sxs-lookup"><span data-stu-id="ea173-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="ea173-105">В текстовом файле с полями фиксированного размера поле в конце может иметь переменную ширину.</span><span class="sxs-lookup"><span data-stu-id="ea173-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="ea173-106">Чтобы указать, что поле в конце имеет переменную длину, определите для его ширины значение меньше или равное нулю.</span><span class="sxs-lookup"><span data-stu-id="ea173-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="ea173-107">Анализ текстового файла с полями фиксированной ширины</span><span class="sxs-lookup"><span data-stu-id="ea173-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="ea173-108">Создайте `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="ea173-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="ea173-109">Следующий код создает объект `TextFieldParser` с именем `Reader` и открывает файл `test.log`.</span><span class="sxs-lookup"><span data-stu-id="ea173-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="ea173-110">Определение свойство `TextFieldType` как `FixedWidth`, задав ширину и формат.</span><span class="sxs-lookup"><span data-stu-id="ea173-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="ea173-111">Следующий код определяет столбцы текста; первый имеет ширину 5 символов, второй 10, третий 11, а четвертый столбец имеет переменную ширину.</span><span class="sxs-lookup"><span data-stu-id="ea173-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="ea173-112">Просмотрите поля в файле.</span><span class="sxs-lookup"><span data-stu-id="ea173-112">Loop through the fields in the file.</span></span> <span data-ttu-id="ea173-113">Если какие-либо строки повреждены, выведите сообщение об ошибке и продолжите анализ.</span><span class="sxs-lookup"><span data-stu-id="ea173-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="ea173-114">Закройте блоки `While` и `Using` операторами `End While` и `End Using`.</span><span class="sxs-lookup"><span data-stu-id="ea173-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="ea173-115">Пример</span><span class="sxs-lookup"><span data-stu-id="ea173-115">Example</span></span>  

 <span data-ttu-id="ea173-116">В этом примере производится чтение данных из файла `test.log`.</span><span class="sxs-lookup"><span data-stu-id="ea173-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ea173-117">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="ea173-117">Robust programming</span></span>  

 <span data-ttu-id="ea173-118">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="ea173-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ea173-119">Строка не может быть проанализирована с использованием указанного формата (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="ea173-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="ea173-120">Сообщение исключения содержит строку, вызвавшую исключение, а свойство <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> присвоено тексту, который содержится в этой строке.</span><span class="sxs-lookup"><span data-stu-id="ea173-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="ea173-121">Указанный файл не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ea173-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="ea173-122">Ситуация частичного доверия, в которой пользователь не имеет достаточных разрешений для доступа к файлу.</span><span class="sxs-lookup"><span data-stu-id="ea173-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="ea173-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ea173-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="ea173-124">Слишком длинный путь (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ea173-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ea173-125">Пользователь не имеет необходимых разрешений для доступа к файлу (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ea173-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea173-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ea173-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="ea173-127">Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми</span><span class="sxs-lookup"><span data-stu-id="ea173-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="ea173-128">Практическое руководство. Чтение из текстовых файлов различных форматов</span><span class="sxs-lookup"><span data-stu-id="ea173-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="ea173-129">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ea173-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="ea173-130">Пошаговое руководство. Операции с файлами и каталогами в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea173-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="ea173-131">Исправление неполадок, связанных с чтением из текстовых файлов и записью в такие файлы</span><span class="sxs-lookup"><span data-stu-id="ea173-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
