---
title: Как выполнить Анализ путей к файлам в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: c089910e3fd5d02b674cfed3062fb15275d91486
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834612"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Как выполнить Анализ путей к файлам в Visual Basic
Объект <xref:Microsoft.VisualBasic.FileIO.FileSystem> предоставляет ряд полезных методов при анализе путей к файлам.  
  
-   Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> получает два пути и возвращает комбинированный путь в правильном формате.  
  
-   Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> возвращает абсолютный путь к родительскому элементу указанного пути.  
  
-   Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> возвращает объект <xref:System.IO.FileInfo> , к которому можно выполнить запрос, чтобы определить свойства файла, например имя и путь.  
  
 По расширению файла не всегда можно с уверенностью судить о его содержимом. Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Определение имени и пути для файла  
  
-   Используйте свойства <xref:System.IO.FileInfo.DirectoryName%2A> и <xref:System.IO.FileInfo.Name%2A> объекта <xref:System.IO.FileInfo> , чтобы определить для файла имя и путь. В этом примере определяются и отображаются имя и путь.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Объединение имени и каталога файла для создания полного пути  
  
-   Используйте метод `CombinePath` , указав каталог и имя. В этом примере объединяются строки `folderPath` и `fileName` , созданные в предыдущем примере, и отображается результат.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Практическое руководство. Получение коллекции содержащихся в каталоге файлов](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
