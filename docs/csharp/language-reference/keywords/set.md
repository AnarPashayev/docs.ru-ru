---
title: Ключевое слово set. Справочник по C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795070"
---
# <a name="set-c-reference"></a><span data-ttu-id="dd879-102">set (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="dd879-102">set (C# Reference)</span></span>

<span data-ttu-id="dd879-103">Ключевое слово `set` определяет *метод доступа* в свойстве или индексаторе, который присваивает значение свойству элемента индексатора.</span><span class="sxs-lookup"><span data-stu-id="dd879-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="dd879-104">Дополнительные сведения и примеры см. в разделах [Свойства](../../programming-guide/classes-and-structs/properties.md), [Автоматически реализуемые свойства](../../programming-guide/classes-and-structs/auto-implemented-properties.md) и [Индексаторы](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd879-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="dd879-105">В приведенном ниже примере определен как метод доступа `get`, так и метод доступа `set` для свойства с именем `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="dd879-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="dd879-106">Для возвращения значения свойства в нем используется закрытое поле с именем `_seconds`.</span><span class="sxs-lookup"><span data-stu-id="dd879-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="dd879-107">Метод доступа `set` часто состоит из одного оператора, который присваивает значение, как в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="dd879-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="dd879-108">Начиная с C# версии 7.0 метод доступа `set` можно реализовывать как член, воплощающий выражение.</span><span class="sxs-lookup"><span data-stu-id="dd879-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="dd879-109">В приведенном ниже примере методы доступа `get` и `set` реализуются как члены, воплощающие выражение.</span><span class="sxs-lookup"><span data-stu-id="dd879-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="dd879-110">В простых случаях, когда методы доступа `get` и `set` свойства не выполняют никаких иных операций, кроме задания или извлечения значения в закрытом поле, можно использовать поддержку автоматически реализуемых свойств в компиляторе C#.</span><span class="sxs-lookup"><span data-stu-id="dd879-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="dd879-111">В приведенном ниже примере `Hours` реализуется как автоматически реализуемое свойство.</span><span class="sxs-lookup"><span data-stu-id="dd879-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="dd879-112">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="dd879-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dd879-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd879-113">See also</span></span>

- [<span data-ttu-id="dd879-114">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="dd879-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd879-115">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="dd879-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd879-116">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="dd879-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dd879-117">Свойства</span><span class="sxs-lookup"><span data-stu-id="dd879-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
