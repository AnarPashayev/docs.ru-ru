---
title: Практическое руководство. Реализация пользовательских преобразований между структурами (Руководство по программированию на C#)
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: f33d8791791543704c8a49a44167b94c0f0c86b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608177"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="fdda2-102">Практическое руководство. Реализация пользовательских преобразований между структурами (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="fdda2-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="fdda2-103">В этом примере определяются две структуры (`RomanNumeral` и `BinaryNumeral`) и демонстрируются преобразования между ними.</span><span class="sxs-lookup"><span data-stu-id="fdda2-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdda2-104">Пример</span><span class="sxs-lookup"><span data-stu-id="fdda2-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fdda2-105">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="fdda2-105">Robust Programming</span></span>  
  
- <span data-ttu-id="fdda2-106">В предыдущем примере инструкция:</span><span class="sxs-lookup"><span data-stu-id="fdda2-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     <span data-ttu-id="fdda2-107">выполняет преобразование из `RomanNumeral` в `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="fdda2-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="fdda2-108">Поскольку прямого преобразования из `RomanNumeral` в `BinaryNumeral` не существует, используется приведение для преобразования из `RomanNumeral` в `int` и еще одно приведение для преобразования из `int` в `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="fdda2-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
- <span data-ttu-id="fdda2-109">Кроме того, инструкция</span><span class="sxs-lookup"><span data-stu-id="fdda2-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     <span data-ttu-id="fdda2-110">выполняет преобразование из `BinaryNumeral` в `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="fdda2-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="fdda2-111">Поскольку `RomanNumeral` определяет неявное преобразование из `BinaryNumeral`, приведение не требуется.</span><span class="sxs-lookup"><span data-stu-id="fdda2-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdda2-112">См. также</span><span class="sxs-lookup"><span data-stu-id="fdda2-112">See also</span></span>

- [<span data-ttu-id="fdda2-113">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="fdda2-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="fdda2-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="fdda2-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fdda2-115">Операторы преобразования</span><span class="sxs-lookup"><span data-stu-id="fdda2-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
