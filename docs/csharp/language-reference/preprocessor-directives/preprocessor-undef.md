---
description: '#undef. Справочник по C#'
title: '#undef. Справочник по C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150561"
---
# <a name="undef-c-reference"></a>#undef (Справочник по C#)

`#undef` позволяет отменить определение символа таким образом, чтобы при использовании этого символа в качестве выражения в директиве [#if](./preprocessor-if.md) возвращалось значение `false`.  
  
 Символ можно определить с помощью директивы [#define](./preprocessor-define.md) или параметра компилятора [-define](../compiler-options/define-compiler-option.md). Директива `#undef` должна находиться в файле перед использованием любых инструкций, которые также не являются директивами.  
  
## <a name="example"></a>Пример  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

**DEBUG не определено**

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Директивы препроцессора C#](./index.md)
