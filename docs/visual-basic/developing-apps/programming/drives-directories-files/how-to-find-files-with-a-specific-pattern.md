---
title: Практическое руководство. Поиск файлов по конкретному шаблону
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401645"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Практическое руководство. Поиск файлов по конкретному шаблону в Visual Basic

Метод <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> возвращает доступную только для чтения коллекцию строк, представляющих имена путей для файлов. Для указания определенного шаблона можно использовать параметр `wildCards` . Если требуется включить подкаталоги в поиск, присвойте параметру `searchType` значение `SearchOption.SearchAllSubDirectories`.  
  
 Если файлы, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.  
  
> [!NOTE]
> Сведения о возврате списка файлов с помощью класса `DirectoryInfo` пространства имен `System.IO` см. в разделе <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Поиск файлов по конкретному шаблону  
  
- Используйте метод `GetFiles`, указав имя и путь к каталогу, в котором требуется выполнить поиск, и шаблон. В следующем примере возвращаются все файлы с расширением `.dll`, имеющиеся в каталоге, и добавляются в `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  

 При следующих условиях возможно возникновение исключения:  
  
- Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).  
  
- Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` не существует (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` указывает на существующий файл (<xref:System.IO.IOException>).  
  
- Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).  
  
- Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).  
  
- У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).  
  
- У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Практическое руководство. Поиск подкаталогов по шаблону](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Исправление неполадок, связанных с чтением из текстовых файлов и записью в такие файлы](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Практическое руководство. Получение коллекции содержащихся в каталоге файлов](how-to-get-the-collection-of-files-in-a-directory.md)
