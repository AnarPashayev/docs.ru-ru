---
title: Исправление неполадок, связанных с чтением из текстовых файлов и записью в такие файлы (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 90a04d9de2ac77c28a92d99e1fe118a1f8ecf448
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831791"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="8af75-102">Исправление неполадок, связанных с чтением из текстовых файлов и записью в такие файлы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af75-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="8af75-103">В этом разделе обсуждаются распространенные проблемы, возникающие при работе с текстовыми файлами, и предлагаются способы их устранения.</span><span class="sxs-lookup"><span data-stu-id="8af75-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="8af75-104">Распространенные проблемы</span><span class="sxs-lookup"><span data-stu-id="8af75-104">Common problems</span></span>  
 <span data-ttu-id="8af75-105">Чаще всего при работе с текстовыми файлами возникают проблемы, связанные с исключениями безопасности, кодировкой файлов и неверными путями.</span><span class="sxs-lookup"><span data-stu-id="8af75-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="8af75-106">Исключения безопасности</span><span class="sxs-lookup"><span data-stu-id="8af75-106">Security exceptions</span></span>  
 <span data-ttu-id="8af75-107">Исключение <xref:System.Security.SecurityException> создается в случае ошибки безопасности.</span><span class="sxs-lookup"><span data-stu-id="8af75-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="8af75-108">Обычно проблема возникает из-за отсутствия необходимых разрешений и устраняется путем добавления разрешений или работы с файлами в изолированном хранилище.</span><span class="sxs-lookup"><span data-stu-id="8af75-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="8af75-109">Кодировки файлов</span><span class="sxs-lookup"><span data-stu-id="8af75-109">File encodings</span></span>  
 <span data-ttu-id="8af75-110">Кодировки файлов (или кодировки символов) определяют отображение символов при обработке текстов.</span><span class="sxs-lookup"><span data-stu-id="8af75-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="8af75-111">При неправильной кодировке в текстовом файле могут появиться непредвиденные символы.</span><span class="sxs-lookup"><span data-stu-id="8af75-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="8af75-112">Для большинства файлов больше подходят определенные кодировки (это связано с тем, какие языковые символы они могут или не могут обрабатывать), хотя обычно предпочтительной является кодировка Юникод.</span><span class="sxs-lookup"><span data-stu-id="8af75-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="8af75-113">Дополнительные сведения см. в статьях [Кодировки файлов](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) и <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8af75-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="8af75-114">Неверные пути</span><span class="sxs-lookup"><span data-stu-id="8af75-114">Incorrect paths</span></span>  
 <span data-ttu-id="8af75-115">Прописывая пути к файлам (особенно если речь идет об относительных путях), легко ошибиться.</span><span class="sxs-lookup"><span data-stu-id="8af75-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="8af75-116">Большинство неполадок можно устранить, просто проверив правильность указанного пути.</span><span class="sxs-lookup"><span data-stu-id="8af75-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="8af75-117">Дополнительные сведения см. в разделе [Как Анализ путей к файлам](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="8af75-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af75-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8af75-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="8af75-119">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="8af75-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="8af75-120">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="8af75-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="8af75-121">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="8af75-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
