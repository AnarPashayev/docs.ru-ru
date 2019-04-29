---
title: ReDim не может изменять размерность
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b6bb78c3f1d7224e6e4b432fd3aef4589f2f1cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964896"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="17f24-102">ReDim не может изменять размерность</span><span class="sxs-lookup"><span data-stu-id="17f24-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="17f24-103">Предпринята попытка использования оператора `ReDim` для изменения ранга (размерности) массива.</span><span class="sxs-lookup"><span data-stu-id="17f24-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="17f24-104">Оператор`ReDim` может изменять размер одного или нескольких измерений массива, который уже был формально объявлен, но он не может изменить ранг массива.</span><span class="sxs-lookup"><span data-stu-id="17f24-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17f24-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="17f24-105">To correct this error</span></span>  
  
- <span data-ttu-id="17f24-106">Убедитесь, что требуется изменить ранг, а не размеры массива, и по возможности используйте `Dim` для объявления нового массива с нужным рангом.</span><span class="sxs-lookup"><span data-stu-id="17f24-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f24-107">См. также</span><span class="sxs-lookup"><span data-stu-id="17f24-107">See also</span></span>

- [<span data-ttu-id="17f24-108">Массивы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17f24-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="17f24-109">Размерности массивов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17f24-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="17f24-110">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="17f24-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="17f24-111">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="17f24-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
