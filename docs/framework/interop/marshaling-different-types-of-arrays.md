---
title: Маршалинг различных типов массивов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fadccdf35429babce6e101d336c9ea1de150b276
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648595"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="da1e1-102">Маршалинг различных типов массивов</span><span class="sxs-lookup"><span data-stu-id="da1e1-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="da1e1-103">Массив является ссылочным типом в управляемом коде, содержащим один или несколько элементов одного и того же типа.</span><span class="sxs-lookup"><span data-stu-id="da1e1-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="da1e1-104">Несмотря на то, что массивы являются ссылочными типами, они передаются в неуправляемые функции в виде параметров In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="da1e1-105">Это поведение не согласуется со способом передачи управляемых массивов в управляемые объекты в виде параметров In/Out.</span><span class="sxs-lookup"><span data-stu-id="da1e1-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="da1e1-106">Подробнее см. в разделе [Копирование и закрепление](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="da1e1-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="da1e1-107">В таблице ниже перечислены параметры маршалинга для массивов и описывается их использование.</span><span class="sxs-lookup"><span data-stu-id="da1e1-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="da1e1-108">Массив</span><span class="sxs-lookup"><span data-stu-id="da1e1-108">Array</span></span>|<span data-ttu-id="da1e1-109">Описание</span><span class="sxs-lookup"><span data-stu-id="da1e1-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="da1e1-110">Целые числа по значению.</span><span class="sxs-lookup"><span data-stu-id="da1e1-110">Of integers by value.</span></span>|<span data-ttu-id="da1e1-111">Передает массив целых чисел в виде параметра In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="da1e1-112">Целые числа по ссылке.</span><span class="sxs-lookup"><span data-stu-id="da1e1-112">Of integers by reference.</span></span>|<span data-ttu-id="da1e1-113">Передает массив целых чисел в виде параметра In/Out.</span><span class="sxs-lookup"><span data-stu-id="da1e1-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="da1e1-114">Целые числа по значению (двухмерный массив).</span><span class="sxs-lookup"><span data-stu-id="da1e1-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="da1e1-115">Передает матрицу целых чисел в виде параметра In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="da1e1-116">Строки по значению.</span><span class="sxs-lookup"><span data-stu-id="da1e1-116">Of strings by value.</span></span>|<span data-ttu-id="da1e1-117">Передает массив строк в виде параметра In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="da1e1-118">Структуры с целыми числами.</span><span class="sxs-lookup"><span data-stu-id="da1e1-118">Of structures with integers.</span></span>|<span data-ttu-id="da1e1-119">Передает массив структур, содержащих целые числа, в виде параметра In/Out.</span><span class="sxs-lookup"><span data-stu-id="da1e1-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="da1e1-120">Структуры со строками.</span><span class="sxs-lookup"><span data-stu-id="da1e1-120">Of structures with strings.</span></span>|<span data-ttu-id="da1e1-121">Передает массив структур, содержащих только строки, в виде параметра In или Out.</span><span class="sxs-lookup"><span data-stu-id="da1e1-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="da1e1-122">Элементы массива можно изменять.</span><span class="sxs-lookup"><span data-stu-id="da1e1-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da1e1-123">Пример</span><span class="sxs-lookup"><span data-stu-id="da1e1-123">Example</span></span>  
 <span data-ttu-id="da1e1-124">В этом примере показаны способы передачи массивов следующих типов:</span><span class="sxs-lookup"><span data-stu-id="da1e1-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="da1e1-125">массив целых чисел по значению;</span><span class="sxs-lookup"><span data-stu-id="da1e1-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="da1e1-126">массив целых чисел, размер которого может быть изменен, по ссылке;</span><span class="sxs-lookup"><span data-stu-id="da1e1-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="da1e1-127">многомерный массив (матрица) целых чисел по значению;</span><span class="sxs-lookup"><span data-stu-id="da1e1-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="da1e1-128">массив строк по значению;</span><span class="sxs-lookup"><span data-stu-id="da1e1-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="da1e1-129">массив структур с целыми числами;</span><span class="sxs-lookup"><span data-stu-id="da1e1-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="da1e1-130">массив структур со строками.</span><span class="sxs-lookup"><span data-stu-id="da1e1-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="da1e1-131">Если маршалинг массива по ссылке не выполняется явным образом, то по умолчанию он осуществляется в виде параметра In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="da1e1-132">Это поведение можно изменить, применив явным образом атрибуты <xref:System.Runtime.InteropServices.InAttribute> и <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="da1e1-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="da1e1-133">В этом примере используются перечисленные ниже неуправляемые функции, показанные со своими исходными объявлениями.</span><span class="sxs-lookup"><span data-stu-id="da1e1-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="da1e1-134">Функция**TestArrayOfInts** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="da1e1-135">Функция**TestRefArrayOfInts** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="da1e1-136">Функция**TestMatrixOfInts** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="da1e1-137">Функция**TestArrayOfStrings** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="da1e1-138">Функция**TestArrayOfStructs** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="da1e1-139">Функция**TestArrayOfStructs2** , экспортированная из PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="da1e1-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="da1e1-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) — это пользовательская неуправляемая библиотека, содержащая реализации ранее описанных функций и две переменные структуры: **MYPOINT** и **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="da1e1-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="da1e1-141">Структуры содержат следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="da1e1-141">The structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 <span data-ttu-id="da1e1-142">В этом примере структуры `MyPoint` и `MyPerson` содержат внедренные типы.</span><span class="sxs-lookup"><span data-stu-id="da1e1-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="da1e1-143">Чтобы гарантировать последовательное размещение членов в памяти в порядке их появления, применяется атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="da1e1-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="da1e1-144">Класс `LibWrap` содержит набор методов, вызываемых классом `App` .</span><span class="sxs-lookup"><span data-stu-id="da1e1-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="da1e1-145">Конкретные сведения о передаче массивов см. в комментариях к приведенному ниже примеру.</span><span class="sxs-lookup"><span data-stu-id="da1e1-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="da1e1-146">Массив, который является ссылочным типом, по умолчанию передается в виде параметра In.</span><span class="sxs-lookup"><span data-stu-id="da1e1-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="da1e1-147">Чтобы вызывающий объект мог получать результаты, необходимо явным образом применить атрибуты **InAttribute** и **OutAttribute** к аргументу, содержащему массив.</span><span class="sxs-lookup"><span data-stu-id="da1e1-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="da1e1-148">Объявление прототипов</span><span class="sxs-lookup"><span data-stu-id="da1e1-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="da1e1-149">Вызов функций</span><span class="sxs-lookup"><span data-stu-id="da1e1-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="da1e1-150">См. также</span><span class="sxs-lookup"><span data-stu-id="da1e1-150">See also</span></span>

- [<span data-ttu-id="da1e1-151">Типы данных в вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="da1e1-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="da1e1-152">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="da1e1-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
