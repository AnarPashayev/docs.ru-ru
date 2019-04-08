---
title: Практическое руководство. Поиск подкаталогов по шаблону в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823406"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Практическое руководство. Поиск подкаталогов по шаблону в Visual Basic
Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> возвращает доступную только для чтения коллекцию строк, представляющих имена путей к подкаталогам каталога. Для указания определенного шаблона можно использовать параметр `wildCards` . Если требуется включить в поиск содержимое подкаталогов, присвойте параметру `searchType` значение `SearchOption.SearchAllSubDirectories`.  
  
 Если каталоги, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Поиск подкаталогов по заданному шаблону  
  
-   Используйте метод `GetDirectories`, указав имя и путь к каталогу для поиска. В следующем примере возвращаются все каталоги в структуре каталогов, имена которых содержат слово "Logs". Затем они добавляются в `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При следующих условиях возможно возникновение исключения:  
  
-   Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Один или несколько указанных подстановочных знаков являются `Nothing`, пустой строкой или содержат только пробелы (<xref:System.ArgumentNullException>).  
  
-   `directory` не существует (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` указывает на существующий файл (<xref:System.IO.IOException>).  
  
-   Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).  
  
-   Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).  
  
-   У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).  
  
-   У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Практическое руководство. Поиск файлов по конкретному шаблону](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
