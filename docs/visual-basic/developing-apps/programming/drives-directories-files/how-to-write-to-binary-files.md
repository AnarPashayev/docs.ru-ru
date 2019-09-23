---
title: Практическое руководство. Запись текста в двоичные файлы в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: ab42fa50aaf39397ac51db8a4cc3a3b00f6ce878
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039418"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="fe1d5-102">Практическое руководство. Запись текста в двоичные файлы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe1d5-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="fe1d5-103">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> записывает данные в двоичный файл.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="fe1d5-104">Если параметр `append` имеет значение `True`, данные будут добавляться в файл; в противном случае данные в файле перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="fe1d5-105">Если указанный путь без имени файла является недопустимым, возникает исключение <xref:System.IO.DirectoryNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="fe1d5-106">Если путь является допустимым, но файл не существует, файл будет создан.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="fe1d5-107">Запись в двоичный файл</span><span class="sxs-lookup"><span data-stu-id="fe1d5-107">To write to a binary file</span></span>

<span data-ttu-id="fe1d5-108">Используйте метод `WriteAllBytes`, указав путь к файлу, имя файла и байты, которые требуется записать.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="fe1d5-109">В этом примере массив данных `CustomerData` добавляется в файл `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="fe1d5-110">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="fe1d5-110">Robust Programming</span></span>

<span data-ttu-id="fe1d5-111">Исключение может возникнуть при следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="fe1d5-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="fe1d5-112">Путь является недопустимым по одной из следующих причин: это строка нулевой длины; она содержит только пробелы; она содержит недопустимые знаки.</span><span class="sxs-lookup"><span data-stu-id="fe1d5-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="fe1d5-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="fe1d5-114">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="fe1d5-115">`File` указывает на путь, который не существует (<xref:System.IO.FileNotFoundException> или <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="fe1d5-116">Файл уже используется другим процессом или возникла ошибка ввода-вывода (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="fe1d5-117">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="fe1d5-118">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="fe1d5-119">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fe1d5-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe1d5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="fe1d5-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="fe1d5-121">Практическое руководство. Запись текста в файлы</span><span class="sxs-lookup"><span data-stu-id="fe1d5-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
