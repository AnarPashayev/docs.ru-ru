---
title: Практическое руководство. Создать новую переменную (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630899"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="d0ca3-102">Практическое руководство. Создать новую переменную (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0ca3-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="d0ca3-103">Переменная создается с помощью [оператора Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d0ca3-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="d0ca3-104">Создание новой переменной</span><span class="sxs-lookup"><span data-stu-id="d0ca3-104">To create a new variable</span></span>

1. <span data-ttu-id="d0ca3-105">Объявите переменную в `Dim` операторе.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="d0ca3-106">Включите спецификации для характеристик переменной, например [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) или [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="d0ca3-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="d0ca3-107">Дополнительные сведения см. в разделе [Характеристики объявленных элементов](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="d0ca3-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="d0ca3-108">`Dim` Ключевое слово не требуется, если в объявлении используются другие ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="d0ca3-109">Используйте спецификации с именем переменной, которое должно соответствовать правилам и соглашениям Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="d0ca3-110">Дополнительные сведения см. в разделе [Имена объявленных элементов](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d0ca3-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="d0ca3-111">Чтобы указать тип данных переменной, используйте имя с предложением [as](../../../../visual-basic/language-reference/statements/as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="d0ca3-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="d0ca3-112">Если тип данных не указан, используется значение по умолчанию: `Object`.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="d0ca3-113">Следуйте предложению со знаком равенства (`=`) и выполните знак равенства с начальным значением переменной. `As`</span><span class="sxs-lookup"><span data-stu-id="d0ca3-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="d0ca3-114">Visual Basic назначает указанное значение переменной при каждом выполнении `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="d0ca3-115">Если не указать начальное значение, Visual Basic присваивает начальное значение по умолчанию для типа данных переменной при первом входе в код, содержащий `Dim` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="d0ca3-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="d0ca3-116">Если переменная является ссылочным типом, можно создать экземпляр его класса, включив в `As` предложение ключевое слово [New operator](../../../../visual-basic/language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="d0ca3-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="d0ca3-117">Если не используется `New`, начальное значение переменной равно [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d0ca3-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="d0ca3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d0ca3-118">See also</span></span>

- [<span data-ttu-id="d0ca3-119">Переменные</span><span class="sxs-lookup"><span data-stu-id="d0ca3-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="d0ca3-120">Объявление переменных</span><span class="sxs-lookup"><span data-stu-id="d0ca3-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="d0ca3-121">Имена объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="d0ca3-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="d0ca3-122">Характеристики объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="d0ca3-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="d0ca3-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="d0ca3-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="d0ca3-124">Операторы</span><span class="sxs-lookup"><span data-stu-id="d0ca3-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="d0ca3-125">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="d0ca3-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d0ca3-126">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="d0ca3-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
