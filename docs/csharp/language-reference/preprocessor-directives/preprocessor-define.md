---
title: '#Справочник по C#. Директива #define'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: d207c96621564acd8070c9d5f618f43a6d8f15a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924605"
---
# <a name="define-c-reference"></a><span data-ttu-id="d7258-102">#define (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d7258-102">#define (C# Reference)</span></span>
<span data-ttu-id="d7258-103">`#define` позволяет определить символ.</span><span class="sxs-lookup"><span data-stu-id="d7258-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="d7258-104">При использовании символа в качестве выражения, которое передается директиве [#if](./preprocessor-if.md), выражение будет иметь значение `true`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d7258-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="d7258-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="d7258-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7258-106">Директиву `#define` нельзя использовать для объявления значений констант, как это обычно делается в C и C++.</span><span class="sxs-lookup"><span data-stu-id="d7258-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="d7258-107">Для определения констант в C# следует использовать статические элементы класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="d7258-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="d7258-108">При наличии нескольких констант имеет смысл создать для них отдельный класс "Constants".</span><span class="sxs-lookup"><span data-stu-id="d7258-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="d7258-109">Символы можно использовать для указания условий компиляции.</span><span class="sxs-lookup"><span data-stu-id="d7258-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="d7258-110">Для проверки символов можно использовать директивы [#if](./preprocessor-if.md) или [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="d7258-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="d7258-111">Для условной компиляции также можно использовать <xref:System.Diagnostics.ConditionalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d7258-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="d7258-112">Можно определить символ, но нельзя назначить символу значение.</span><span class="sxs-lookup"><span data-stu-id="d7258-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="d7258-113">Директива `#define` должна находиться в файле перед использованием любых инструкций, которые также не являются директивами препроцессора.</span><span class="sxs-lookup"><span data-stu-id="d7258-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="d7258-114">Также символ можно определить с помощью параметра компилятора [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d7258-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d7258-115">Для отмены определения символа служит директива [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="d7258-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="d7258-116">Символ, определенный с помощью `-define` или `#define`, не конфликтует с одноименной переменной.</span><span class="sxs-lookup"><span data-stu-id="d7258-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="d7258-117">Имя переменной не должно передаваться директиве препроцессора, а символ может вычисляться только директивой препроцессора.</span><span class="sxs-lookup"><span data-stu-id="d7258-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="d7258-118">Область символа, которая была создана с помощью директивы `#define`, — это файл, в котором был определен символ.</span><span class="sxs-lookup"><span data-stu-id="d7258-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="d7258-119">Как показано в следующем примере, необходимо поместить директивы `#define` в верхнюю часть файла.</span><span class="sxs-lookup"><span data-stu-id="d7258-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="d7258-120">Пример отмены определения символа см. в разделе [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="d7258-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7258-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d7258-121">See also</span></span>

- [<span data-ttu-id="d7258-122">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="d7258-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d7258-123">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="d7258-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d7258-124">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="d7258-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="d7258-125">const</span><span class="sxs-lookup"><span data-stu-id="d7258-125">const</span></span>](../keywords/const.md)
- <span data-ttu-id="d7258-126">[Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="d7258-126">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)</span></span>
- [<span data-ttu-id="d7258-127">#undef</span><span class="sxs-lookup"><span data-stu-id="d7258-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="d7258-128">#if</span><span class="sxs-lookup"><span data-stu-id="d7258-128">#if</span></span>](./preprocessor-if.md)
