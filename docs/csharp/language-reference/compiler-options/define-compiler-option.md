---
description: -define (параметры компилятора C#)
title: -define (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125882"
---
# <a name="-define-c-compiler-options"></a>-define (параметры компилятора C#)
Параметр **-define** определяет `name` как символ во всех файлах исходного кода программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Аргументы  
 `name`, `name2`  
 Имя одного или нескольких символов, которые требуется определить.  
  
## <a name="remarks"></a>Remarks  
 Параметр компилятора **-define** действует так же, как директива препроцессора [#define](../preprocessor-directives/preprocessor-define.md), однако, в отличие от нее, применяется ко всем файлам проекта. Символ остается определенным в файле исходного кода до тех пор, пока определение не будет отменено с помощью директивы [#undef](../preprocessor-directives/preprocessor-undef.md) в файле исходного кода. При использовании параметра -define директива `#undef` в одном файле не действует для других файлов исходного кода в проекте.  
  
 Вы можете использовать символы, созданные этим параметром, с директивами [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md) и [#endif](../preprocessor-directives/preprocessor-endif.md) для условной компиляции исходных файлов.  
  
 **-d** является краткой формой **-define**.  
  
 Вы можете определить несколько символов с помощью **-define**, разделяя их имена точкой с запятой или запятой. Пример:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Компилятор C# сам по себе не определяет символы и макросы, которые можно использовать в исходном коде. Все такие определения задаются пользователем.  
  
> [!NOTE]
> C# `#define` не поддерживает присваивание значения символу, как, например, в языке C++. Например, с помощью директивы `#define` нельзя создать макрос или определить константу. Чтобы определить константу, используйте переменную `enum`. Для создания макросов в стиле C++ необходимо использовать альтернативные способы, например универсальные шаблоны. Поскольку макросы по своей природе подвержены ошибкам, в C# они запрещены, однако вместо них предлагаются более безопасные альтернативы.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1. Откройте страницу **Свойства** проекта.  
  
2. На вкладке **Сборка** введите символ, который требуется определить, в поле **Символы условной компиляции**. Например, для представленного ниже примера кода просто введите `xx` в текстовое поле.  
  
 Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Пример  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>См. также раздел

- [Параметры компилятора C# ](./index.md)
- [Управление свойствами проектов и решений](/visualstudio/ide/managing-project-and-solution-properties)
