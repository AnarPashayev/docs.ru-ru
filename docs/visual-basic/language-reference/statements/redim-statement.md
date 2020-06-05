---
title: Оператор reDim
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404282"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="bb20a-102">Оператор ReDim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb20a-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="bb20a-103">Перераспределяет область хранения для переменной массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb20a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb20a-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="bb20a-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="bb20a-105">Parts</span></span>  
  
|<span data-ttu-id="bb20a-106">Термин</span><span class="sxs-lookup"><span data-stu-id="bb20a-106">Term</span></span>|<span data-ttu-id="bb20a-107">Определение</span><span class="sxs-lookup"><span data-stu-id="bb20a-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="bb20a-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="bb20a-108">Optional.</span></span> <span data-ttu-id="bb20a-109">Модификатор, используемый для сохранения данных в существующем массиве при изменении размера только последнего измерения.</span><span class="sxs-lookup"><span data-stu-id="bb20a-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="bb20a-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="bb20a-110">Required.</span></span> <span data-ttu-id="bb20a-111">Имя переменной массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-111">Name of the array variable.</span></span> <span data-ttu-id="bb20a-112">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bb20a-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="bb20a-113">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="bb20a-113">Required.</span></span> <span data-ttu-id="bb20a-114">Список границ для всех измерений переопределенного массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb20a-115">Комментарии</span><span class="sxs-lookup"><span data-stu-id="bb20a-115">Remarks</span></span>  
 <span data-ttu-id="bb20a-116">Для изменения размера одного или нескольких из уже объявленных измерений массива можно использовать оператор `ReDim`.</span><span class="sxs-lookup"><span data-stu-id="bb20a-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="bb20a-117">Если у вас есть большой массив и некоторые из входящих в него элементов больше не требуются, `ReDim` позволяет освободить память, уменьшив размер массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="bb20a-118">Если же массив требует дополнительных элементов, `ReDim` может их добавить.</span><span class="sxs-lookup"><span data-stu-id="bb20a-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="bb20a-119">Оператор `ReDim` предназначен только для массивов.</span><span class="sxs-lookup"><span data-stu-id="bb20a-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="bb20a-120">Он не подходит для скалярных величин (переменных, содержащих единственное значение), коллекций или структур.</span><span class="sxs-lookup"><span data-stu-id="bb20a-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="bb20a-121">Обратите внимание, что при объявлении переменной типа `Array` у оператора `ReDim` не будет достаточной информации о типе для создания нового массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="bb20a-122">Оператор `ReDim` можно использовать только на уровне процедуры.</span><span class="sxs-lookup"><span data-stu-id="bb20a-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="bb20a-123">В связи с этим контекст объявления для переменной должен быть процедурой; он не может быть исходным файлом, пространством имен, интерфейсом, классом, структурой, модулем или блоком.</span><span class="sxs-lookup"><span data-stu-id="bb20a-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="bb20a-124">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bb20a-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bb20a-125">Правила</span><span class="sxs-lookup"><span data-stu-id="bb20a-125">Rules</span></span>  
  
- <span data-ttu-id="bb20a-126">**Множество переменных.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-126">**Multiple Variables.**</span></span> <span data-ttu-id="bb20a-127">Можно изменить размер нескольких переменных массива в одном операторе объявления и указать `name` `boundlist` части и для каждой переменной.</span><span class="sxs-lookup"><span data-stu-id="bb20a-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="bb20a-128">Переменные разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="bb20a-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="bb20a-129">**Границы массива.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-129">**Array Bounds.**</span></span> <span data-ttu-id="bb20a-130">Каждая запись в `boundlist` может указывать нижнюю и верхнюю границы этого измерения.</span><span class="sxs-lookup"><span data-stu-id="bb20a-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="bb20a-131">Нижняя граница всегда 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="bb20a-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="bb20a-132">Верхняя граница представляет собой наибольшее возможное значение индекса для этого измерения, но не длину измерения (она равна верхней границе плюс один).</span><span class="sxs-lookup"><span data-stu-id="bb20a-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="bb20a-133">Индекс для каждого измерения может варьироваться от 0 до значения верхней границы.</span><span class="sxs-lookup"><span data-stu-id="bb20a-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="bb20a-134">Число измерений в `boundlist` должно совпадать с исходным числом измерений (рангом) массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="bb20a-135">**Типы данных.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-135">**Data Types.**</span></span> <span data-ttu-id="bb20a-136">`ReDim`Инструкция не может изменить тип данных переменной массива или ее элементов.</span><span class="sxs-lookup"><span data-stu-id="bb20a-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="bb20a-137">**Инициализации.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-137">**Initialization.**</span></span> <span data-ttu-id="bb20a-138">`ReDim`Инструкция не может предоставлять новые значения инициализации для элементов массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="bb20a-139">**Рейтинг.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-139">**Rank.**</span></span> <span data-ttu-id="bb20a-140">`ReDim`Оператор не может изменить ранг (число измерений) массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="bb20a-141">**Изменение размера с помощью оператора Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="bb20a-142">При использовании `Preserve` можно изменить размер только последнего измерения массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="bb20a-143">Для всех остальных измерений необходимо указывать привязку существующего массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="bb20a-144">Например, в одномерных массивах можно изменить это измерение и в то же время сохранить все содержимое массива, поскольку изменяется только одно, последнее, измерение.</span><span class="sxs-lookup"><span data-stu-id="bb20a-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="bb20a-145">Если же массив имеет два или больше измерений, то с помощью оператора Preserve можно изменить только последнее измерение массива.`Preserve`</span><span class="sxs-lookup"><span data-stu-id="bb20a-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="bb20a-146">**Свойства.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-146">**Properties.**</span></span> <span data-ttu-id="bb20a-147">Можно использовать `ReDim` для свойства, содержащего массив значений.</span><span class="sxs-lookup"><span data-stu-id="bb20a-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bb20a-148">Поведение</span><span class="sxs-lookup"><span data-stu-id="bb20a-148">Behavior</span></span>  
  
- <span data-ttu-id="bb20a-149">**Замена массива.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-149">**Array Replacement.**</span></span> <span data-ttu-id="bb20a-150">`ReDim`Освобождает существующий массив и создает новый массив с тем же рангом.</span><span class="sxs-lookup"><span data-stu-id="bb20a-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="bb20a-151">Новый массив заменяет освобожденный массив в переменной массива.</span><span class="sxs-lookup"><span data-stu-id="bb20a-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="bb20a-152">**Инициализация без использования оператора Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="bb20a-153">Если не указать `Preserve` , `ReDim` инициализирует элементы нового массива, используя значение по умолчанию для их типа данных.</span><span class="sxs-lookup"><span data-stu-id="bb20a-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="bb20a-154">**Инициализация с использованием оператора Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bb20a-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="bb20a-155">Если указано `Preserve` , Visual Basic копирует элементы из существующего массива в новый массив.</span><span class="sxs-lookup"><span data-stu-id="bb20a-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb20a-156">Пример</span><span class="sxs-lookup"><span data-stu-id="bb20a-156">Example</span></span>  
 <span data-ttu-id="bb20a-157">В приведенном ниже примере производится увеличение размера последнего измерения динамического массива без потери существующих данных, а затем уменьшение размера массива с частичной потерей данных.</span><span class="sxs-lookup"><span data-stu-id="bb20a-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="bb20a-158">Кроме того, размер массива уменьшается до исходного значения и все элементы массива инициализируются повторно.</span><span class="sxs-lookup"><span data-stu-id="bb20a-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="bb20a-159">Оператор `Dim` создает новый массив с тремя измерениями.</span><span class="sxs-lookup"><span data-stu-id="bb20a-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="bb20a-160">Каждое измерение объявляется с границей 10, поэтому индекс массива для каждого измерения может варьироваться в диапазоне от 0 до 10.</span><span class="sxs-lookup"><span data-stu-id="bb20a-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="bb20a-161">В приведенном ниже описании эти три измерения называются слоем, строкой и столбцом.</span><span class="sxs-lookup"><span data-stu-id="bb20a-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="bb20a-162">Первый оператор `ReDim` создает новый массив, который заменяет существующий массив в переменной `intArray`.</span><span class="sxs-lookup"><span data-stu-id="bb20a-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="bb20a-163">Оператор `ReDim` копирует все элементы из существующего массива в новый массив.</span><span class="sxs-lookup"><span data-stu-id="bb20a-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="bb20a-164">Кроме того, он добавляет по десять столбцов в конец каждой строки каждого слоя и инициализирует элементы в этих новых столбцах со значением 0 (значение параметра `Integer`, который является типом элемента массива, по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bb20a-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="bb20a-165">Второй оператор `ReDim` создает еще один массив и копирует в него все подходящие элементы.</span><span class="sxs-lookup"><span data-stu-id="bb20a-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="bb20a-166">При этом в каждой строке каждого слоя теряются пять последних столбцов.</span><span class="sxs-lookup"><span data-stu-id="bb20a-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="bb20a-167">Это не проблема, если данные столбцы вам больше не нужны.</span><span class="sxs-lookup"><span data-stu-id="bb20a-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="bb20a-168">Уменьшение размера большого массива позволяет освободить память, которая больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="bb20a-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="bb20a-169">Третий оператор `ReDim` создает еще один массив и удаляет еще пять столбцов в конце каждой строки каждого слоя.</span><span class="sxs-lookup"><span data-stu-id="bb20a-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="bb20a-170">В данном случае он не копирует существующие элементы.</span><span class="sxs-lookup"><span data-stu-id="bb20a-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="bb20a-171">Этот оператор возвращает массиву первоначальный размер.</span><span class="sxs-lookup"><span data-stu-id="bb20a-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="bb20a-172">Поскольку оператор не включает модификатор `Preserve`, он приводит все элементы массива к исходным значениям по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bb20a-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="bb20a-173">Дополнительные примеры см. в разделе [массивы](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb20a-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb20a-174">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bb20a-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="bb20a-175">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="bb20a-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="bb20a-176">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="bb20a-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="bb20a-177">Оператор Erase</span><span class="sxs-lookup"><span data-stu-id="bb20a-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="bb20a-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="bb20a-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="bb20a-179">Массивы</span><span class="sxs-lookup"><span data-stu-id="bb20a-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
