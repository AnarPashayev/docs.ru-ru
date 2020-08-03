---
title: Руководство по программированию на C#. Передача массивов в качестве аргументов
description: В C# массивы можно передавать в качестве аргументов в параметры метода. Поскольку массивы представляют собой ссылочные типы, метод может изменять значения элементов.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474635"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="cb190-104">Передача массивов в качестве аргументов (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="cb190-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="cb190-105">Массивы можно передавать в качестве аргументов в параметры метода.</span><span class="sxs-lookup"><span data-stu-id="cb190-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="cb190-106">Поскольку массивы представляют собой ссылочные типы, метод может изменять значения элементов.</span><span class="sxs-lookup"><span data-stu-id="cb190-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="cb190-107">Передача одномерных массивов в качестве аргументов</span><span class="sxs-lookup"><span data-stu-id="cb190-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="cb190-108">Инициализированный одномерный массив можно передать в метод.</span><span class="sxs-lookup"><span data-stu-id="cb190-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="cb190-109">Например, следующий оператор передает массив в метод печати.</span><span class="sxs-lookup"><span data-stu-id="cb190-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="cb190-110">В следующем примере кода показана разделяемая реализация метода печати.</span><span class="sxs-lookup"><span data-stu-id="cb190-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="cb190-111">Новый массив можно инициализировать и передать за один шаг, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cb190-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="cb190-112">Пример</span><span class="sxs-lookup"><span data-stu-id="cb190-112">Example</span></span>

<span data-ttu-id="cb190-113">В следующем примере массив строк инициализируется и передается в качестве аргумента в метод `DisplayArray` для строк.</span><span class="sxs-lookup"><span data-stu-id="cb190-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="cb190-114">Этот метод отображает элементы массива.</span><span class="sxs-lookup"><span data-stu-id="cb190-114">The method displays the elements of the array.</span></span> <span data-ttu-id="cb190-115">Затем метод `ChangeArray` размещает элементы массива в обратном порядке, а метод `ChangeArrayElements` изменяет первые три элемента массива.</span><span class="sxs-lookup"><span data-stu-id="cb190-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="cb190-116">После возврата каждого метода метод `DisplayArray` показывает, что передача массива по значению не препятствует изменению элементов массива.</span><span class="sxs-lookup"><span data-stu-id="cb190-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="cb190-117">Передача многомерных массивов в качестве аргументов</span><span class="sxs-lookup"><span data-stu-id="cb190-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="cb190-118">Инициализированный многомерный массив можно передать в метод так же, как и одномерный массив.</span><span class="sxs-lookup"><span data-stu-id="cb190-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="cb190-119">В следующем коде показано разделяемое объявление метода печати, который принимает в качестве аргумента двухмерный массив.</span><span class="sxs-lookup"><span data-stu-id="cb190-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="cb190-120">Новый массив можно инициализировать и передать за один шаг, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="cb190-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="cb190-121">Пример</span><span class="sxs-lookup"><span data-stu-id="cb190-121">Example</span></span>

<span data-ttu-id="cb190-122">В следующем примере инициализируется двухмерный массив целых чисел, который передается в метод `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="cb190-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="cb190-123">Этот метод отображает элементы массива.</span><span class="sxs-lookup"><span data-stu-id="cb190-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="cb190-124">См. также</span><span class="sxs-lookup"><span data-stu-id="cb190-124">See also</span></span>

- [<span data-ttu-id="cb190-125">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="cb190-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cb190-126">Массивы</span><span class="sxs-lookup"><span data-stu-id="cb190-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="cb190-127">Одномерные массивы</span><span class="sxs-lookup"><span data-stu-id="cb190-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="cb190-128">Многомерные массивы</span><span class="sxs-lookup"><span data-stu-id="cb190-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="cb190-129">Массивы массивов</span><span class="sxs-lookup"><span data-stu-id="cb190-129">Jagged Arrays</span></span>](jagged-arrays.md)
