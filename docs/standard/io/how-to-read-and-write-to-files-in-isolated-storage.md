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
ms.openlocfilehash: a1ea65b0b8280faf51595b2fe9edcbf17eaabd8f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706690"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="ae28d-102">Практическое руководство. Считывание из файлов и запись в файлы в изолированном хранилище</span><span class="sxs-lookup"><span data-stu-id="ae28d-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="ae28d-103">Для чтения из файла или записи в файл в изолированном хранилище используется объект <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> с модулем чтения потока (объект <xref:System.IO.StreamReader> ) или модулем записи в поток (объект <xref:System.IO.StreamWriter>).</span><span class="sxs-lookup"><span data-stu-id="ae28d-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae28d-104">Пример</span><span class="sxs-lookup"><span data-stu-id="ae28d-104">Example</span></span>  
 <span data-ttu-id="ae28d-105">Следующий пример создает изолированное хранилище и проверяет, существует ли в хранилище файл с именем TestStore.txt.</span><span class="sxs-lookup"><span data-stu-id="ae28d-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="ae28d-106">Если он не существует, код создает файл и записывает в файл текст "Hello Isolated Storage".</span><span class="sxs-lookup"><span data-stu-id="ae28d-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="ae28d-107">Если TestStore.txt уже существует, пример кода выполняет чтение из файла.</span><span class="sxs-lookup"><span data-stu-id="ae28d-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ae28d-108">См. также</span><span class="sxs-lookup"><span data-stu-id="ae28d-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="ae28d-109">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="ae28d-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="ae28d-110">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="ae28d-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
