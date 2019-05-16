---
title: Управление доступом
description: Узнайте, как управлять доступом к элементов программирования, таких как типы, методы и функции, в F# языка программирования.
ms.date: 05/16/2016
ms.openlocfilehash: a284d2fa4f98e444279276f58b70a15560537ca4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645600"
---
# <a name="access-control"></a><span data-ttu-id="8fbf9-103">Управление доступом</span><span class="sxs-lookup"><span data-stu-id="8fbf9-103">Access Control</span></span>

<span data-ttu-id="8fbf9-104">*Управление доступом* ссылается на объявления, какие клиенты могут использовать определенные элементы программы, такие как типы, методы и функции.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="8fbf9-105">Основы управления доступом</span><span class="sxs-lookup"><span data-stu-id="8fbf9-105">Basics of Access Control</span></span>

<span data-ttu-id="8fbf9-106">В F#, управления описатели доступа `public`, `internal`, и `private` могут применяться к модули, типы, методы, определения значения, функции, свойства и явные поля.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="8fbf9-107">`public` Указывает, что сущность может осуществляться все вызывающие объекты.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="8fbf9-108">`internal` Указывает, что сущность может осуществляться только из той же сборки.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="8fbf9-109">`private` Указывает, что сущность может осуществляться только из включающего типа или модуля.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="8fbf9-110">Спецификатор доступа `protected` не используется в F#, хотя это допустимо, если при использовании типов, созданных на языках, которые поддерживают `protected` доступа.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="8fbf9-111">Таким образом Если вы Переопределите защищенный метод, этот метод будет доступен только в пределах класса и его потомков.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="8fbf9-112">Как правило, описатель размещается перед именем сущности, за исключением случаев `mutable` или `inline` используется спецификатор, в которые записываются после описателя управления доступом.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="8fbf9-113">Если используется спецификатор доступа, по умолчанию используется `public`, за исключением `let` привязки в типе, которые всегда `private` к типу.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="8fbf9-114">Подписи в F# предоставить другой механизм для управления доступом к F# программным элементам.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="8fbf9-115">Подписи не являются обязательными для управления доступом.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-115">Signatures are not required for access control.</span></span> <span data-ttu-id="8fbf9-116">Дополнительные сведения см. в статье [Сигнатуры](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="8fbf9-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="8fbf9-117">Правила для контроля доступа</span><span class="sxs-lookup"><span data-stu-id="8fbf9-117">Rules for Access Control</span></span>

<span data-ttu-id="8fbf9-118">Управление доступом регулируется следующими правилами:</span><span class="sxs-lookup"><span data-stu-id="8fbf9-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="8fbf9-119">Объявления наследования (то есть использование `inherit` для указания базового класса для класса), объявления интерфейсов (Указание того, что класс реализует интерфейс) и абстрактные члены всегда имеют тот же уровень доступа, включающего типа.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="8fbf9-120">Таким образом спецификатора контроля доступа не может использоваться для этих конструкций.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="8fbf9-121">Специальные возможности для отдельных вариантов в размеченном объединении определяется само размеченное объединение со специальными возможностями.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="8fbf9-122">Конкретному варианту объединения составляет не менее доступен, чем само объединение.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="8fbf9-123">Специальные возможности для отдельных полей типа записи не определяется со специальными возможностями саму запись.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="8fbf9-124">Метка конкретной записи составляет не менее доступен, чем саму запись.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="8fbf9-125">Пример</span><span class="sxs-lookup"><span data-stu-id="8fbf9-125">Example</span></span>

<span data-ttu-id="8fbf9-126">Следующий код иллюстрирует использование описателей управления доступом.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="8fbf9-127">Существует два файла в проекте `Module1.fs` и `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="8fbf9-128">Каждый файл неявно представляет собой модуль.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-128">Each file is implicitly a module.</span></span> <span data-ttu-id="8fbf9-129">Таким образом, есть два модуля `Module1` и `Module2`.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="8fbf9-130">Закрытый тип и внутренний тип определяются в `Module1`.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="8fbf9-131">Закрытый тип не может быть организован `Module2`, но внутреннему типу.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="8fbf9-132">Следующий код проверяет доступность типов, созданных в `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="8fbf9-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="8fbf9-133">См. также</span><span class="sxs-lookup"><span data-stu-id="8fbf9-133">See also</span></span>

- [<span data-ttu-id="8fbf9-134">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="8fbf9-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8fbf9-135">Сигнатуры</span><span class="sxs-lookup"><span data-stu-id="8fbf9-135">Signatures</span></span>](signatures.md)
