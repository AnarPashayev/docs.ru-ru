---
title: Практическое руководство. Создание копии файла в том же каталоге
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401684"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="88ef3-102">Практическое руководство. Создание копии файла в том же каталоге в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88ef3-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="88ef3-103">Для копирования файлов используйте метод `My.Computer.FileSystem.CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="88ef3-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="88ef3-104">Эти параметры обеспечивают возможность перезаписи существующих файлов, переименования файлов и отображения хода выполнения операции, а также отмены операции пользователем.</span><span class="sxs-lookup"><span data-stu-id="88ef3-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="88ef3-105">Создание копии файла в том же каталоге</span><span class="sxs-lookup"><span data-stu-id="88ef3-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="88ef3-106">Используйте метод `CopyFile`, указав конечный файл и расположение.</span><span class="sxs-lookup"><span data-stu-id="88ef3-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="88ef3-107">В следующем примере создается копия `test.txt` с именем `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="88ef3-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="88ef3-108">Создание копии файла в том же каталоге, перезапись существующих файлов</span><span class="sxs-lookup"><span data-stu-id="88ef3-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="88ef3-109">Используйте метод `CopyFile`, указав конечный файл и расположение и задав для параметра `overwrite` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="88ef3-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="88ef3-110">В следующем примере создается копия `test.txt` с именем `test2.txt` и перезаписываются существующие файлы с этим именем.</span><span class="sxs-lookup"><span data-stu-id="88ef3-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="88ef3-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="88ef3-111">Robust Programming</span></span>  

 <span data-ttu-id="88ef3-112">Исключение может возникнуть в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="88ef3-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="88ef3-113">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="88ef3-114">Системе не удалось получить абсолютный путь (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="88ef3-115">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="88ef3-116">Исходный файл является недопустимым или не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="88ef3-117">Объединенный путь указывает на существующий каталог (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="88ef3-118">Конечный файл существует, а параметр `overwrite` имеет значение `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="88ef3-119">Пользователь не имеет необходимых разрешений для доступа к файлу (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="88ef3-120">Файл в папке назначения с тем же именем уже используется (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="88ef3-121">Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="88ef3-122">Параметр `ShowUI` имеет значение `True`, параметр `onUserCancel` имеет значение `ThrowException`, и пользователь отменил операцию (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="88ef3-123">`ShowUI` имеет значение `True`, параметр `onUserCancel` имеет значение `ThrowException`, и возникла неопределенная ошибка ввода-вывода (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="88ef3-124">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="88ef3-125">У пользователя отсутствует необходимое разрешение (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="88ef3-126">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="88ef3-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ef3-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="88ef3-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="88ef3-128">Практическое руководство. Копирование файлов по заданному шаблону в каталог</span><span class="sxs-lookup"><span data-stu-id="88ef3-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="88ef3-129">Практическое руководство. Создание копии файла в другом каталоге</span><span class="sxs-lookup"><span data-stu-id="88ef3-129">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="88ef3-130">Практическое руководство. Копирование каталога в другой каталог</span><span class="sxs-lookup"><span data-stu-id="88ef3-130">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="88ef3-131">Практическое руководство. Переименование файла</span><span class="sxs-lookup"><span data-stu-id="88ef3-131">How to: Rename a File</span></span>](how-to-rename-a-file.md)
