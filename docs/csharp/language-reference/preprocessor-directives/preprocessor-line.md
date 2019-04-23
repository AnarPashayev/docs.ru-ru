---
title: '#line. Справочник по C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: f4e3c3edbe1d542f9bf5c984c403e0486a9da61b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611982"
---
# <a name="line-c-reference"></a>#line (Справочник по C#)

Директива `#line` позволяет изменять номер строки компилятора и при необходимости имя файла, в который будут выводиться ошибки и предупреждения.

В следующем примере показано, как включить в отчет два предупреждения, связанные с номерами строк. Директива `#line 200` принудительно устанавливает номер следующей строки 200 (по умолчанию используется номер 6). До выполнения следующей директивы `#line` в отчете будет указываться имя файла Special. Директива `#line default` по умолчанию восстанавливает нумерацию строк в исходное состояние с учетом строк, номера которых были изменены с помощью предшествующей директивы.

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

В результате компиляции формируются следующие результаты:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Примечания

Директива `#line` может использоваться на автоматизированном промежуточном этапе процесса построения. Например, если строки были удалены из первоначального файла с исходным кодом, но вам по-прежнему требуется создавать выходные файлы компилятора на основе изначальной нумерации строк в файле, можно удалить строки и затем смоделировать их первичную нумерацию с помощью директивы `#line`.

Директива `#line hidden` скрывает последующие строки для отладчика. В этом случае при пошаговой проверке кода разработчиком все строки между `#line hidden` и следующей директивой `#line` (кроме случаев, когда это также директива `#line hidden`) будут пропущены. Этот параметр также можно использовать для того, чтобы дать ASP.NET возможность различать определяемый пользователем и создаваемый компьютером код. В основном эта функция используется в ASP.NET, но также может быть полезна и в других генераторах исходного кода.

Директива `#line hidden` не влияет на имена файлов и номера строк в отчетах об ошибках. Это значит, что при обнаружении ошибки в скрытом блоке компилятор укажет в отчете текущие имя файла и номер строки, где найдена ошибка.

Директива `#line filename` задает имя файла, которое будет отображаться в выходных данных компилятора. По умолчанию используется фактическое имя файла с исходным кодом. Имя файла должно заключаться в двойные кавычки (" "). Перед ним должен указываться номер строки.

Файл с исходным кодом может содержать любое количество директив `#line`.

## <a name="example-1"></a>Пример 1

В следующем примере демонстрируется, как отладчик игнорирует скрытые строки кода. При выполнении этого примера будут показаны три строки текста. Тем не менее, если задать точку останова, как показано в этом примере, и нажать клавишу F10 для пошаговой отладки кода, вы увидите, что отладчик игнорирует скрытую строку. Обратите внимание, что даже если точка останова установлена на скрытой строке, отладчик по-прежнему будет игнорировать ее.

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Директивы препроцессора C#](../../../csharp/language-reference/preprocessor-directives/index.md)
