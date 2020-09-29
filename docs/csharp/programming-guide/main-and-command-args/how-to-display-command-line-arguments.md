---
title: Руководство по программированию на C#. Отображение аргументов командной строки
description: Узнайте, как отобразить аргументы командной строки. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 717e27c23724e63c03a38b028ef99dc6530b4745
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195484"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Руководство по программированию на C#. Отображение аргументов командной строки

Аргументы, предоставляемые исполняемому файлу в командной строке, доступны через необязательный параметр для `Main`. Аргументы предоставляются в форме массива строк. Каждый элемент массива содержит один аргумент. Пробелы между аргументами удаляются. Например, рассмотрим следующие вызовы из командной строки вымышленного исполняемого файла:  
  
|Входные данные в командной строке|Массив строк, передаваемых в метод Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"один два"<br /><br /> "три"|  
  
> [!NOTE]
> При выполнении приложения в Visual Studio аргументы командной строки можно указать на [странице "Отладка" в конструкторе проектов](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Пример  

 Этот пример отображает аргументы командной строки, передаваемые в приложение командной строки. Показанные выходные данные — первая запись в таблице выше.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Сборка из командной строки с помощью csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() и аргументы командной строки](./index.md)
- [Значения, возвращаемые методом main()](./main-return-values.md)
