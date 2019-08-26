---
title: '#warning. Справочник по C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608528"
---
# <a name="warning-c-reference"></a><span data-ttu-id="371ea-102">#warning (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="371ea-102">#warning (C# Reference)</span></span>
<span data-ttu-id="371ea-103">`#warning` позволяет создать предупреждение компилятора [CS1030](../../misc/cs1030.md) первого уровня из определенного места в коде.</span><span class="sxs-lookup"><span data-stu-id="371ea-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="371ea-104">Например:</span><span class="sxs-lookup"><span data-stu-id="371ea-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="371ea-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="371ea-105">Remarks</span></span>
 <span data-ttu-id="371ea-106">Как правило, `#warning` применяется в условной директиве.</span><span class="sxs-lookup"><span data-stu-id="371ea-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="371ea-107">Кроме того, с помощью директивы [#error](./preprocessor-error.md) можно создать определяемую пользователем ошибку.</span><span class="sxs-lookup"><span data-stu-id="371ea-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="371ea-108">Пример</span><span class="sxs-lookup"><span data-stu-id="371ea-108">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="371ea-109">См. также</span><span class="sxs-lookup"><span data-stu-id="371ea-109">See also</span></span>

- [<span data-ttu-id="371ea-110">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="371ea-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="371ea-111">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="371ea-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="371ea-112">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="371ea-112">C# Preprocessor Directives</span></span>](./index.md)
