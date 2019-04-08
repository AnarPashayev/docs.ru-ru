---
title: Практическое руководство. Переименование файла в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: b86797018e1471590fd4c89848921e696afbc819
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814159"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="bcbdd-102">Практическое руководство. Переименование файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bcbdd-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="bcbdd-103">Метод `RenameFile` объекта `My.Computer.FileSystem` можно использовать, чтобы переименовать файл, указав текущее расположение, имя файла и новое имя файла.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="bcbdd-104">Этот метод нельзя использовать для перемещения файла. Для перемещения и переименования файла используется метод `MoveFile`.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="bcbdd-105">Переименование файла</span><span class="sxs-lookup"><span data-stu-id="bcbdd-105">To rename a file</span></span>  
  
-   <span data-ttu-id="bcbdd-106">Используйте метод `My.Computer.FileSystem.RenameFile`, чтобы переименовать файл.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="bcbdd-107">В этом примере переименовывается файл с именем `Test.txt` в `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="bcbdd-108">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="bcbdd-109">В средстве выбора фрагментов кода фрагмент находится в разделе **файловая система: обработка дисков, папок и файлов**.</span><span class="sxs-lookup"><span data-stu-id="bcbdd-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="bcbdd-110">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bcbdd-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="bcbdd-111">Robust Programming</span></span>  
 <span data-ttu-id="bcbdd-112">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="bcbdd-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bcbdd-113">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-114">`newName` содержит сведения о пути (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-115">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-116">Параметр`newName` имеет значение `Nothing` или является пустой строкой (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-117">Исходный файл является недопустимым или не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-118">Имеется существующий файл или каталог с именем, указанным в `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-119">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-120">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-121">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="bcbdd-122">У пользователя отсутствует необходимое разрешение (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="bcbdd-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbdd-123">См. также</span><span class="sxs-lookup"><span data-stu-id="bcbdd-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="bcbdd-124">Практическое руководство. Перемещение файла</span><span class="sxs-lookup"><span data-stu-id="bcbdd-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [<span data-ttu-id="bcbdd-125">Создание, удаление и перемещение файлов и каталогов</span><span class="sxs-lookup"><span data-stu-id="bcbdd-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="bcbdd-126">Практическое руководство. Создание копии файла в том же каталоге</span><span class="sxs-lookup"><span data-stu-id="bcbdd-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="bcbdd-127">Практическое руководство. Создание копии файла в другом каталоге</span><span class="sxs-lookup"><span data-stu-id="bcbdd-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
