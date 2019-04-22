---
title: Практическое руководство. Сортировка массива в Visual Basic
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838083"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="6043e-102">Практическое руководство. Сортировка массива в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6043e-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="6043e-103">В этом примере объявляется массив `String` объектов с именем `zooAnimals`, заполняет его и сортировка по алфавиту.</span><span class="sxs-lookup"><span data-stu-id="6043e-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6043e-104">Пример</span><span class="sxs-lookup"><span data-stu-id="6043e-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6043e-105">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="6043e-105">Compiling the Code</span></span>  
 <span data-ttu-id="6043e-106">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="6043e-106">This example requires:</span></span>  
  
-   <span data-ttu-id="6043e-107">Доступ к библиотеке Mscorlib.dll и <xref:System> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="6043e-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6043e-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="6043e-108">Robust Programming</span></span>  
 <span data-ttu-id="6043e-109">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="6043e-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6043e-110">Массив пуст (<xref:System.ArgumentNullException> класса)</span><span class="sxs-lookup"><span data-stu-id="6043e-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="6043e-111">Массив является многомерным (<xref:System.RankException> класса)</span><span class="sxs-lookup"><span data-stu-id="6043e-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="6043e-112">Один или несколько элементов массива не реализуют <xref:System.IComparable> интерфейс (<xref:System.InvalidOperationException> класса)</span><span class="sxs-lookup"><span data-stu-id="6043e-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6043e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="6043e-113">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6043e-114">Массивы</span><span class="sxs-lookup"><span data-stu-id="6043e-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="6043e-115">Устранение неполадок, связанных с массивами</span><span class="sxs-lookup"><span data-stu-id="6043e-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="6043e-116">Коллекции</span><span class="sxs-lookup"><span data-stu-id="6043e-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="6043e-117">Оператор For Each...Next</span><span class="sxs-lookup"><span data-stu-id="6043e-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
