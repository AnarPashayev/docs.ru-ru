---
title: Практическое руководство. Определить, является ли файл сборкой (Visual Basic)
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: 47ac7f29509af86819006a4394ca661140b95ab0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316067"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Практическое руководство. Определить, является ли файл сборкой (Visual Basic)
Файл является сборкой только в том случае, если он является управляемым и содержит запись сборки в своих метаданных. Дополнительные сведения о сборках и метаданных см. в разделе [Манифест сборки](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Как вручную определить, является ли файл сборкой  
  
1. Запустите [Ildasm.exe (дизассемблер IL)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Загрузите файл, который нужно протестировать.  
  
3. Если программа **ILDASM** сообщает, что файл не является переносимым исполняемым файлом (PE), то он не является сборкой. Дополнительные сведения см. в разделе [Практическое руководство. просмотреть одержимое сборки](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Как программно определить, является ли файл сборкой  
  
1. Вызовите метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, указав полный путь к файлу и имя файла, который вы тестируете.  
  
2. Если возникает исключение <xref:System.BadImageFormatException>, значит файл не является сборкой.  
  
## <a name="example"></a>Пример  
 Этот пример кода проверяет, является ли библиотека DLL сборкой.  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 Метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> загружает тестовый файл и освобождает его после того, как информация будет прочитана.  
  
## <a name="see-also"></a>См. также

- <xref:System.Reflection.AssemblyName>
- [Основные понятия программирования](../../../../visual-basic/programming-guide/concepts/index.md)
- [Сборки и глобальный кэш сборок (Visual Basic)](index.md)
