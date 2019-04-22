---
title: Ожидается объявление
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 64ee75c93615f57b15fea29f06fff500a395ba0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834183"
---
# <a name="declaration-expected"></a><span data-ttu-id="ec8f5-102">Ожидается объявление</span><span class="sxs-lookup"><span data-stu-id="ec8f5-102">Declaration expected</span></span>
<span data-ttu-id="ec8f5-103">Недекларативный оператор, например оператор присваивания или цикла, находится вне процедуры.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="ec8f5-104">Только объявления разрешены вне процедур.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="ec8f5-105">Кроме того, программный элемент объявлен без ключевого слова объявления таких как `Dim` или `Const`.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="ec8f5-106">**Идентификатор ошибки:** BC30188</span><span class="sxs-lookup"><span data-stu-id="ec8f5-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec8f5-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ec8f5-107">To correct this error</span></span>  
  
-   <span data-ttu-id="ec8f5-108">Переместите оператор недекларативный в тело процедуры.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="ec8f5-109">В начале объявления соответствующее ключевое слово объявления.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="ec8f5-110">Убедитесь, что ключевое слово объявления является его имя указано верно.</span><span class="sxs-lookup"><span data-stu-id="ec8f5-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8f5-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ec8f5-111">See also</span></span>

- [<span data-ttu-id="ec8f5-112">Процедуры</span><span class="sxs-lookup"><span data-stu-id="ec8f5-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ec8f5-113">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="ec8f5-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
