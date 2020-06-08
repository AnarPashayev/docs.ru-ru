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
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Практическое руководство. Получение коллекции содержащихся в каталоге файлов в Visual Basic

Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> вернет доступную только для чтения коллекцию строк, представляющих собой имена файлов в каталоге:  
  
- Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> позволяет найти простой файл в указанном каталоге без поиска подкаталогов.  
  
- Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> позволяет указать дополнительные параметры поиска. Для указания шаблона поиска можно использовать параметр `wildCards`. Чтобы включить подкаталоги в поиск, присвойте параметру `searchType` значение <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Если файлы, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.  
  
### <a name="to-list-files-in-a-directory"></a>Составление списка файлов в каталоге  
  
- Используйте перегрузки одного из методов <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>, указывая имя и путь к каталогу для поиска в параметре `directory`. В следующем примере возвращаются и добавляются в список `ListBox1` все файлы, находящиеся в каталоге.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  

 При следующих условиях возможно возникновение исключения:  
  
- Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).  
  
- Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` не существует (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` указывает на существующий файл (<xref:System.IO.IOException>).  
  
- Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).  
  
- Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).  
  
- У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).  
  
- У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Практическое руководство. Поиск файлов по конкретному шаблону](how-to-find-files-with-a-specific-pattern.md)
- [Практическое руководство. Поиск подкаталогов по шаблону](how-to-find-subdirectories-with-a-specific-pattern.md)
