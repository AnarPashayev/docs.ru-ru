---
title: Практическое руководство. Считывание из файлов и запись в файлы в изолированном хранилище
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: d0c95f418ff85654dceed296b7a891c025ab2e62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291803"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Практическое руководство. Считывание из файлов и запись в файлы в изолированном хранилище
Для чтения из файла или записи в файл в изолированном хранилище используется объект <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> с модулем чтения потока (объект <xref:System.IO.StreamReader> ) или модулем записи в поток (объект <xref:System.IO.StreamWriter>).  
  
## <a name="example"></a>Пример  
 Следующий пример создает изолированное хранилище и проверяет, существует ли в хранилище файл с именем TestStore.txt. Если он не существует, код создает файл и записывает в файл текст "Hello Isolated Storage". Если TestStore.txt уже существует, пример кода выполняет чтение из файла.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [Файловый и потоковый ввод-вывод](index.md)
- [Изолированное хранилище](isolated-storage.md)
