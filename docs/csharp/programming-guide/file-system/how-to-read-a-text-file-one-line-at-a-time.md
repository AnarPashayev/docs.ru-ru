---
title: Руководство по программированию на C#. Построчное чтение текстового файла
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241777"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Руководство по программированию на C#. Построчное чтение текстового файла
В этом примере производится построчное чтение содержимого текстового файла в строку с помощью метода `ReadLine` класса `StreamReader`. Каждая строка текста сохраняется в строке `line` и отображается на экране.  
  
## <a name="example"></a>Пример  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Скопируйте код и вставьте его в метод `Main` консольного приложения.  
  
 Замените `"c:\test.txt"` фактическим именем файла.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При следующих условиях возможно возникновение исключения:  
  
- Возможно, файл не существует.  
  
## <a name="net-security"></a>Безопасность .NET  
 По имени файла не всегда можно с уверенностью судить о его содержимом. Например, файл с именем `myFile.cs` может вовсе не быть исходным файлом C#.  
  
## <a name="see-also"></a>См. также

- <xref:System.IO?displayProperty=nameWithType>
- [Руководство по программированию на C#](../index.md)
- [Файловая система и реестр (руководство по программированию на C#)](./index.md)
