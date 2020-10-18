---
title: <expression> нельзя использовать в качестве ограничения типа
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 6e55bfdc175f285b335512e64f4c2407bdb0e8c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163094"
---
# <a name="bc32061-expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="e472d-102">BC32061: " \<expression> " не может использоваться как ограничение типа</span><span class="sxs-lookup"><span data-stu-id="e472d-102">BC32061: '\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="e472d-103">Список ограничений включает выражение, которое не представляет допустимое ограничение для параметра типа.</span><span class="sxs-lookup"><span data-stu-id="e472d-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>

 <span data-ttu-id="e472d-104">Список ограничений налагает требования на аргумент типа, передаваемый в параметр типа.</span><span class="sxs-lookup"><span data-stu-id="e472d-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="e472d-105">Вы можете указать приведенные ниже требования в любой комбинации.</span><span class="sxs-lookup"><span data-stu-id="e472d-105">You can specify the following requirements in any combination:</span></span>

- <span data-ttu-id="e472d-106">Аргумент типа должен реализовывать один или несколько интерфейсов</span><span class="sxs-lookup"><span data-stu-id="e472d-106">The type argument must implement one or more interfaces</span></span>

- <span data-ttu-id="e472d-107">Аргумент типа должен наследовать не более чем от одного класса.</span><span class="sxs-lookup"><span data-stu-id="e472d-107">The type argument must inherit from at most one class</span></span>

- <span data-ttu-id="e472d-108">Аргумент типа должен предоставлять конструктор без параметров, к которому создающий код может получить доступ (включая ограничение `New` ).</span><span class="sxs-lookup"><span data-stu-id="e472d-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>

 <span data-ttu-id="e472d-109">Если не включать определенный класс или интерфейс в список ограничений, то можно наложить более общее требование, указав одно из приведенных ниже ограничений.</span><span class="sxs-lookup"><span data-stu-id="e472d-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>

- <span data-ttu-id="e472d-110">Аргумент типа должен быть типом значения (включая ограничение `Structure` ).</span><span class="sxs-lookup"><span data-stu-id="e472d-110">The type argument must be a value type (include the `Structure` constraint)</span></span>

- <span data-ttu-id="e472d-111">Аргумент типа должен быть ссылочным типом (включая ограничение `Class` ).</span><span class="sxs-lookup"><span data-stu-id="e472d-111">The type argument must be a reference type (include the `Class` constraint)</span></span>

 <span data-ttu-id="e472d-112">Нельзя указывать оба ограничения, `Structure` и `Class` , для одного и того же параметра типа, а также указывать какой-либо из них более одного раза.</span><span class="sxs-lookup"><span data-stu-id="e472d-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>

 <span data-ttu-id="e472d-113">**Идентификатор ошибки:** BC32061</span><span class="sxs-lookup"><span data-stu-id="e472d-113">**Error ID:** BC32061</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e472d-114">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="e472d-114">To correct this error</span></span>

- <span data-ttu-id="e472d-115">Проверьте правильность написания выражения и его элементов.</span><span class="sxs-lookup"><span data-stu-id="e472d-115">Verify that the expression and its elements are spelled correctly.</span></span>

- <span data-ttu-id="e472d-116">Если выражение не соответствует требованиям предыдущего списка, удалите его из списка ограничений.</span><span class="sxs-lookup"><span data-stu-id="e472d-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>

- <span data-ttu-id="e472d-117">Если выражение ссылается на интерфейс или класс, убедитесь, что у компилятора есть доступ к этому интерфейсу или классу.</span><span class="sxs-lookup"><span data-stu-id="e472d-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="e472d-118">Возможно, вам потребуется проверить его имя и добавить ссылку в проект.</span><span class="sxs-lookup"><span data-stu-id="e472d-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="e472d-119">Дополнительные сведения см. в разделе "ссылки на проекты" статьи [ссылки на объявленные элементы](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="e472d-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e472d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e472d-120">See also</span></span>

- [<span data-ttu-id="e472d-121">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e472d-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e472d-122">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="e472d-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="e472d-123">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="e472d-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
