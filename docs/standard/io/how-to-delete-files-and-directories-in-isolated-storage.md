---
title: Практическое руководство. Удаление файлов и каталогов из изолированного хранилища
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538028"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Практическое руководство. Удаление файлов и каталогов из изолированного хранилища
Вы можете удалять файлы и папки из файла изолированного хранилища. В хранилище имена файлов и каталогов зависят от используемой операционной системы, а путь к ним указывается относительно корня виртуальной файловой системы. В операционных системах Windows регистр в именах файлов не учитывается.  
  
 Класс <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> предоставляет два метода для удаления каталогов и файлов: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. При попытке удалить несуществующий файл или каталог создается исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>. Если в имени будет указан подстановочный знак, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> создает исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>, а <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> создает исключение <xref:System.ArgumentException>.  
  
 Метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> завершается ошибкой, если удаляемый каталог содержит файлы или подкаталоги. Вы можете использовать методы <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>, чтобы получить существующие файлы и каталоги. Дополнительные сведения о поиске в виртуальной файловой системе хранилища см. в разделе [Практическое руководство. Поиск существующих файлов и каталогов в изолированном хранилище](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода создает несколько каталогов и файлов, а затем удаляет их.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>См. также

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Изолированное хранилище](../../../docs/standard/io/isolated-storage.md)
