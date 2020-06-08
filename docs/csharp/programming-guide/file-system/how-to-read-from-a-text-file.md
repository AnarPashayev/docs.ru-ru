---
title: Руководство по программированию на C#. Чтение из текстового файла
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 8f79d22a86390ca931b05262e50865d852c154c7
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241751"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Руководство по программированию на C#. Чтение из текстового файла
В этом примере считывается содержимое текстового файла с помощью статических методов <xref:System.IO.File.ReadAllText%2A> и <xref:System.IO.File.ReadAllLines%2A> из класса <xref:System.IO.File?displayProperty=nameWithType>.  
  
См. пример использования <xref:System.IO.StreamReader> в руководстве по [построчному чтению текстового файла](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Файлы, которые используются в этом примере, созданы в руководстве по [записи в текстовый файл](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Пример  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Скопируйте код и вставьте его в консольное приложение C#.  
  
Если вы не используете текстовые файлы из руководства по [записи в текстовый файл](./how-to-write-to-a-text-file.md), замените аргумент `ReadAllText` и `ReadAllLines` соответствующими путем и именем файла на компьютере.
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При следующих условиях возможно возникновение исключения:  
  
- Файл не существует или не существует в указанном месте. Проверьте правильность написания имени файла и путь к нему.  
  
## <a name="net-security"></a>Безопасность .NET  
 Не следует полагаться на имя файла, чтобы определить содержимое файла. Например, файл `myFile.cs` может вовсе не быть исходным файлом C#.  
  
## <a name="see-also"></a>См. также

- <xref:System.IO?displayProperty=nameWithType>
- [Руководство по программированию на C#](../index.md)
- [Файловая система и реестр (руководство по программированию на C#)](./index.md)
