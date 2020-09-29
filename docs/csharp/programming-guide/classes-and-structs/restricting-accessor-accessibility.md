---
title: Руководство по программированию на C#. Ограничение доступности методов доступа
description: Методы доступа get и set свойства в C# по умолчанию имеют такие же уровни видимости или доступа, что и свойство, которому они принадлежат. Доступ можно ограничить.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: be7be4fc67a9a6f62a71f8473d6daa1fac49e842
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199033"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="3f915-104">Ограничение доступности методов доступа (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="3f915-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>

<span data-ttu-id="3f915-105">Выражения [get](../../language-reference/keywords/get.md) и [set](../../language-reference/keywords/set.md) свойства или индексатора называются *методами доступа*.</span><span class="sxs-lookup"><span data-stu-id="3f915-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="3f915-106">По умолчанию они имеют такие же уровни видимости или доступа, что и свойство или индексатор, которым они принадлежат.</span><span class="sxs-lookup"><span data-stu-id="3f915-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="3f915-107">Дополнительные сведения см. в разделе [Уровни доступа](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3f915-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="3f915-108">Тем не менее в некоторых случаях рекомендуется ограничить уровни доступа для этих методов.</span><span class="sxs-lookup"><span data-stu-id="3f915-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="3f915-109">Как правило, в этом случае ограничивается уровень доступа для метода `set`, тогда как метод `get` остается общедоступным.</span><span class="sxs-lookup"><span data-stu-id="3f915-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="3f915-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="3f915-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="3f915-111">В этом примере свойство `Name` определяет методы доступа `get` и `set`.</span><span class="sxs-lookup"><span data-stu-id="3f915-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="3f915-112">Метод доступа `get` получает уровень доступа самого свойства (в этом случае `public`), а к методу `set` явным образом применяется модификатор доступа [protected](../../language-reference/keywords/protected.md).</span><span class="sxs-lookup"><span data-stu-id="3f915-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="3f915-113">Ограничения модификаторов доступа для методов доступа</span><span class="sxs-lookup"><span data-stu-id="3f915-113">Restrictions on Access Modifiers on Accessors</span></span>  

 <span data-ttu-id="3f915-114">При использовании модификаторов доступа для свойств или индексаторов необходимо соблюдать следующие ограничения:</span><span class="sxs-lookup"><span data-stu-id="3f915-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="3f915-115">Модификаторы доступа нельзя использовать в интерфейсе или явной реализации элемента [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="3f915-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="3f915-116">Модификаторы доступа можно использовать только в том случае, если для свойства или индексатора определены одновременно методы доступа `set` и `get`.</span><span class="sxs-lookup"><span data-stu-id="3f915-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="3f915-117">В этом случае модификатор может применяться только к одному из двух методов доступа.</span><span class="sxs-lookup"><span data-stu-id="3f915-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="3f915-118">Если свойству или индексатору назначен модификатор [override](../../language-reference/keywords/override.md), модификатор доступа должен соответствовать методу доступа для переопределенного метода доступа, если такой существует.</span><span class="sxs-lookup"><span data-stu-id="3f915-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="3f915-119">Уровень доступности для метода доступа должен быть более строгим по сравнению с уровнем доступа самого свойства или идентификатора.</span><span class="sxs-lookup"><span data-stu-id="3f915-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="3f915-120">Модификаторы доступа при переопределении методов доступа</span><span class="sxs-lookup"><span data-stu-id="3f915-120">Access Modifiers on Overriding Accessors</span></span>  

 <span data-ttu-id="3f915-121">При переопределении свойства или индексатора переопределенные методы доступа должны быть доступны коду переопределения.</span><span class="sxs-lookup"><span data-stu-id="3f915-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="3f915-122">Кроме того, уровни доступа свойства или индексатора и их методов доступа должны совпадать с уровнями переопределенных свойства или индексатора и их методов доступа.</span><span class="sxs-lookup"><span data-stu-id="3f915-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="3f915-123">Пример:</span><span class="sxs-lookup"><span data-stu-id="3f915-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="3f915-124">Реализация интерфейсов</span><span class="sxs-lookup"><span data-stu-id="3f915-124">Implementing Interfaces</span></span>  

 <span data-ttu-id="3f915-125">Методы доступа, которые используются для реализации интерфейса, не могут иметь модификаторы доступа.</span><span class="sxs-lookup"><span data-stu-id="3f915-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="3f915-126">Тем не менее при реализации интерфейса с использованием одного метода доступа (например, `get`) другой метод доступа может иметь модификатор доступа, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="3f915-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="3f915-127">Домен доступности для метода доступа</span><span class="sxs-lookup"><span data-stu-id="3f915-127">Accessor Accessibility Domain</span></span>  

 <span data-ttu-id="3f915-128">При использовании модификатора доступа для метода доступа этот модификатор определяет [домен доступности](../../language-reference/keywords/accessibility-domain.md) для такого метода.</span><span class="sxs-lookup"><span data-stu-id="3f915-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="3f915-129">Если к методу доступа не применяется модификатор доступа, домен доступности этого метода определяется уровнем доступности свойства или индексатора.</span><span class="sxs-lookup"><span data-stu-id="3f915-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f915-130">Пример</span><span class="sxs-lookup"><span data-stu-id="3f915-130">Example</span></span>  

 <span data-ttu-id="3f915-131">В следующем примере определяются три класса: `BaseClass`, `DerivedClass` и `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="3f915-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="3f915-132">В классе `BaseClass` для обоих классов определены свойства `Name` и `Id`.</span><span class="sxs-lookup"><span data-stu-id="3f915-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="3f915-133">В этом примере демонстрируется, как свойство `Id` класса `DerivedClass` может быть скрыто свойством `Id` класса `BaseClass` при использовании ограничивающего модификатора доступа, такого как [protected](../../language-reference/keywords/protected.md) или [private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="3f915-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="3f915-134">Таким образом, при присвоении значений этому свойству вместо него вызывается свойство класса `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="3f915-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="3f915-135">Чтобы сделать это свойство доступным, необходимо заменить модификатор доступа на [public](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="3f915-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="3f915-136">В этом примере также демонстрируется, что ограничивающий модификатор доступа (`private` или `protected`) для метода доступа `set` свойства `Name` в классе `DerivedClass` запрещает доступ к этому методу и при попытке присвоить ему значение возвращает ошибку.</span><span class="sxs-lookup"><span data-stu-id="3f915-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="3f915-137">Комментарии</span><span class="sxs-lookup"><span data-stu-id="3f915-137">Comments</span></span>  

 <span data-ttu-id="3f915-138">Обратите внимание, что если заменить объявление `new private string Id` на `new public string Id`, будут получены следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="3f915-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="3f915-139">См. также</span><span class="sxs-lookup"><span data-stu-id="3f915-139">See also</span></span>

- [<span data-ttu-id="3f915-140">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="3f915-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f915-141">Свойства</span><span class="sxs-lookup"><span data-stu-id="3f915-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="3f915-142">Индексаторы</span><span class="sxs-lookup"><span data-stu-id="3f915-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="3f915-143">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="3f915-143">Access Modifiers</span></span>](./access-modifiers.md)
