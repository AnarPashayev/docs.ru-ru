---
title: Практическое руководство. Определение того, является ли файл сборкой
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: f9bff86ac559e40136ed016b862eef8ba0863ce3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972693"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Практическое руководство. Определение того, является ли файл сборкой

Файл является сборкой только в том случае, если он является управляемым и содержит запись сборки в своих метаданных. Дополнительные сведения о сборках и метаданных см. в разделе [Манифест сборки](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Как вручную определить, является ли файл сборкой  
  
1. Запустите [Ildasm.exe (дизассемблер IL)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Загрузите файл, который нужно протестировать.  
  
3. Если программа **ILDASM** сообщает, что файл не является переносимым исполняемым файлом (PE), то он не является сборкой. Дополнительные сведения см. в разделе [Практическое руководство. Просмотр содержимого сборки](view-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Как программно определить, является ли файл сборкой  
  
1. Вызовите метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>, указав полный путь к файлу и имя файла, который вы тестируете.  
  
2. Если возникает исключение <xref:System.BadImageFormatException>, значит файл не является сборкой.  
  
## <a name="example"></a>Пример  
Этот пример кода проверяет, является ли библиотека DLL сборкой.  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

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
- [Руководство по программированию на C#](../../csharp/programming-guide/index.md)
- [Основные понятия программирования (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Сборки в .NET](index.md)
