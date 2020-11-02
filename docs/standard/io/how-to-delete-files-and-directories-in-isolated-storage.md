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
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: 7797f319ca3b143bac6a4e68eaf820e966f1560e
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187948"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Практическое руководство. Удаление файлов и каталогов из изолированного хранилища
Вы можете удалять файлы и папки из файла изолированного хранилища. В хранилище имена файлов и каталогов зависят от используемой операционной системы, а путь к ним указывается относительно корня виртуальной файловой системы. В операционных системах Windows регистр в именах файлов не учитывается.  
  
 Класс <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> предоставляет два метода для удаления каталогов и файлов: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. При попытке удалить несуществующий файл или каталог создается исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>. Если в имени будет указан подстановочный знак, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> создает исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException>, а <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> создает исключение <xref:System.ArgumentException>.  
  
 Метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> завершается ошибкой, если удаляемый каталог содержит файлы или подкаталоги. Вы можете использовать методы <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>, чтобы получить существующие файлы и каталоги. Дополнительные сведения о поиске в виртуальной файловой системе хранилища см. в статье [Практическое руководство. Поиск существующих файлов и каталоги в изолированном хранилище](how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода создает несколько каталогов и файлов, а затем удаляет их.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Изолированное хранилище](isolated-storage.md)
