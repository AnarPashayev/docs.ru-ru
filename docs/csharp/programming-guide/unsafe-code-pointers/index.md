---
title: Руководство по программированию в C#. Небезопасный код и указатели
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608038"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="b843c-102">Небезопасный код и указатели (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="b843c-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="b843c-103">Для обеспечения типобезопасности и безопасности язык C# по умолчанию не поддерживает арифметику указателей.</span><span class="sxs-lookup"><span data-stu-id="b843c-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="b843c-104">Но ключевое слово [unsafe](../../../csharp/language-reference/keywords/unsafe.md) позволяет задать небезопасный контекст, в котором использование указателей возможно.</span><span class="sxs-lookup"><span data-stu-id="b843c-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="b843c-105">Дополнительные сведения об указателях см. в разделе [Типы указателей](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="b843c-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b843c-106">В общеязыковой среде выполнения (CLR) небезопасный код называется непроверяемым.</span><span class="sxs-lookup"><span data-stu-id="b843c-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="b843c-107">Небезопасный код в C# не обязательно опасен, просто его безопасность нельзя проверить в CLR.</span><span class="sxs-lookup"><span data-stu-id="b843c-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="b843c-108">Поэтому CLR будет выполнять небезопасный код, только если он находится в полностью доверенной сборке.</span><span class="sxs-lookup"><span data-stu-id="b843c-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="b843c-109">Если вы используете небезопасный код, вы сами несете ответственность за возможные риски безопасности и ошибки указателей.</span><span class="sxs-lookup"><span data-stu-id="b843c-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="b843c-110">Общие сведения о небезопасном коде</span><span class="sxs-lookup"><span data-stu-id="b843c-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="b843c-111">Небезопасный код имеет следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="b843c-111">Unsafe code has the following properties:</span></span>  
  
- <span data-ttu-id="b843c-112">Методы, типы и блоки кода можно определить как небезопасные.</span><span class="sxs-lookup"><span data-stu-id="b843c-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
- <span data-ttu-id="b843c-113">В некоторых случаях небезопасный код может увеличить скорость работы приложения, если не проверяются границы массивов.</span><span class="sxs-lookup"><span data-stu-id="b843c-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
- <span data-ttu-id="b843c-114">Небезопасный код необходим при вызове встроенных стандартных функций, требующих указателей.</span><span class="sxs-lookup"><span data-stu-id="b843c-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
- <span data-ttu-id="b843c-115">Использование небезопасного кода создает риски для стабильности и безопасности.</span><span class="sxs-lookup"><span data-stu-id="b843c-115">Using unsafe code introduces security and stability risks.</span></span>  
  
- <span data-ttu-id="b843c-116">Чтобы скомпилировать небезопасный код на C#, приложение нужно компилировать с помощью [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b843c-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b843c-117">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="b843c-117">Related Sections</span></span>  
 <span data-ttu-id="b843c-118">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="b843c-118">For more information, see:</span></span>  
  
- [<span data-ttu-id="b843c-119">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="b843c-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [<span data-ttu-id="b843c-120">Буферы фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="b843c-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [<span data-ttu-id="b843c-121">Практическое руководство. Использование указателей для копирования массива байтов</span><span class="sxs-lookup"><span data-stu-id="b843c-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [<span data-ttu-id="b843c-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="b843c-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b843c-123">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="b843c-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b843c-124">См. также</span><span class="sxs-lookup"><span data-stu-id="b843c-124">See also</span></span>

- [<span data-ttu-id="b843c-125">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="b843c-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
