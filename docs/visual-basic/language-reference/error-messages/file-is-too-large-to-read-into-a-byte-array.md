---
title: Файл слишком велик для чтения в массив байтов
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831518"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Файл слишком велик для чтения в массив байтов
Размер файла, который вы пытаетесь считать в массив байтов превышает 4 ГБ. `My.Computer.FileSystem.ReadAllBytes` Метод не может прочитать файл большего размера.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Используйте <xref:System.IO.StreamReader> для чтения файла. Дополнительные сведения см. в разделе [основы из .NET Framework файлового ввода-вывода и файловой системе (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Доступ к файлам с помощью Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [Практическое руководство. Чтение текста из файлов с помощью StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
