---
title: Практическое руководство. Получение коллекции содержащихся в каталоге файлов
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401619"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="8eda6-102">Практическое руководство. Получение коллекции содержащихся в каталоге файлов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8eda6-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="8eda6-103">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> вернет доступную только для чтения коллекцию строк, представляющих собой имена файлов в каталоге:</span><span class="sxs-lookup"><span data-stu-id="8eda6-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="8eda6-104">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> позволяет найти простой файл в указанном каталоге без поиска подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="8eda6-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="8eda6-105">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> позволяет указать дополнительные параметры поиска.</span><span class="sxs-lookup"><span data-stu-id="8eda6-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="8eda6-106">Для указания шаблона поиска можно использовать параметр `wildCards`.</span><span class="sxs-lookup"><span data-stu-id="8eda6-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="8eda6-107">Чтобы включить подкаталоги в поиск, присвойте параметру `searchType` значение <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8eda6-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8eda6-108">Если файлы, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.</span><span class="sxs-lookup"><span data-stu-id="8eda6-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="8eda6-109">Составление списка файлов в каталоге</span><span class="sxs-lookup"><span data-stu-id="8eda6-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="8eda6-110">Используйте перегрузки одного из методов <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>, указывая имя и путь к каталогу для поиска в параметре `directory`.</span><span class="sxs-lookup"><span data-stu-id="8eda6-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="8eda6-111">В следующем примере возвращаются и добавляются в список `ListBox1` все файлы, находящиеся в каталоге.</span><span class="sxs-lookup"><span data-stu-id="8eda6-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8eda6-112">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="8eda6-112">Robust Programming</span></span>  

 <span data-ttu-id="8eda6-113">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="8eda6-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8eda6-114">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="8eda6-115">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="8eda6-116">`directory` не существует (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="8eda6-117">`directory` указывает на существующий файл (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="8eda6-118">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="8eda6-119">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="8eda6-120">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="8eda6-121">У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="8eda6-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eda6-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8eda6-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="8eda6-123">Практическое руководство. Поиск файлов по конкретному шаблону</span><span class="sxs-lookup"><span data-stu-id="8eda6-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="8eda6-124">Практическое руководство. Поиск подкаталогов по шаблону</span><span class="sxs-lookup"><span data-stu-id="8eda6-124">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
