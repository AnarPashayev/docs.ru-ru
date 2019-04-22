---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829034"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="2254a-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2254a-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="2254a-103">Указывает, что свойство можно осуществлять запись, но не читать.</span><span class="sxs-lookup"><span data-stu-id="2254a-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2254a-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="2254a-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2254a-105">Правила</span><span class="sxs-lookup"><span data-stu-id="2254a-105">Rules</span></span>  
 <span data-ttu-id="2254a-106">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="2254a-106">**Declaration Context.**</span></span> <span data-ttu-id="2254a-107">`WriteOnly` можно использовать только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="2254a-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="2254a-108">Это означает, что контекст объявления для `WriteOnly` свойство должно быть класса, структуры или модуля и не может быть исходный файл, пространство имен или процедуры.</span><span class="sxs-lookup"><span data-stu-id="2254a-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="2254a-109">Можно объявить свойство как `WriteOnly`, но не переменной.</span><span class="sxs-lookup"><span data-stu-id="2254a-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="2254a-110">Когда следует использовать WriteOnly</span><span class="sxs-lookup"><span data-stu-id="2254a-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="2254a-111">Иногда требуется много кода, чтобы иметь возможность установить значение, но не открывал его.</span><span class="sxs-lookup"><span data-stu-id="2254a-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="2254a-112">Например конфиденциальных данных, таких как социальные регистрационный код или пароль, необходимо быть защищены от доступа из любой компонент, который не устанавливал их.</span><span class="sxs-lookup"><span data-stu-id="2254a-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="2254a-113">В таких случаях можно использовать `WriteOnly` свойство для задания значения.</span><span class="sxs-lookup"><span data-stu-id="2254a-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2254a-114">Если вы определяете и использовать `WriteOnly` свойства, рассмотрим следующие дополнительные защитные меры:</span><span class="sxs-lookup"><span data-stu-id="2254a-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="2254a-115">**Переопределение.**</span><span class="sxs-lookup"><span data-stu-id="2254a-115">**Overriding.**</span></span> <span data-ttu-id="2254a-116">Если свойство является членом класса, по умолчанию; чтобы разрешить [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), а не объявляйте `Overridable` или `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="2254a-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="2254a-117">Это предотвращает нежелательный доступ с помощью переопределения в производном классе.</span><span class="sxs-lookup"><span data-stu-id="2254a-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="2254a-118">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="2254a-118">**Access Level.**</span></span> <span data-ttu-id="2254a-119">Если вы держите свойства конфиденциальные данные в одну или несколько переменных, объявите их [частного](../../../visual-basic/language-reference/modifiers/private.md) таким образом, чтобы никакой другой код доступа к ним.</span><span class="sxs-lookup"><span data-stu-id="2254a-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="2254a-120">**Шифрование.**</span><span class="sxs-lookup"><span data-stu-id="2254a-120">**Encryption.**</span></span> <span data-ttu-id="2254a-121">Store все конфиденциальные данные в зашифрованном виде, а не в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="2254a-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="2254a-122">Если вредоносный код каким-либо образом получает доступ к этой области памяти, это сложнее использовать данные.</span><span class="sxs-lookup"><span data-stu-id="2254a-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="2254a-123">Шифрование также полезен, если это необходимо для сериализации конфиденциальных данных.</span><span class="sxs-lookup"><span data-stu-id="2254a-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="2254a-124">**Сброс.**</span><span class="sxs-lookup"><span data-stu-id="2254a-124">**Resetting.**</span></span> <span data-ttu-id="2254a-125">Когда класс, структура или модуль, определяющего свойство прерывается, конфиденциальных данных для сброса значения по умолчанию или другие смысла значения.</span><span class="sxs-lookup"><span data-stu-id="2254a-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="2254a-126">Это дает дополнительную защиту при освобождении этой области памяти для общего доступа.</span><span class="sxs-lookup"><span data-stu-id="2254a-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="2254a-127">**Сохраняемость.**</span><span class="sxs-lookup"><span data-stu-id="2254a-127">**Persistence.**</span></span> <span data-ttu-id="2254a-128">Если этого можно избежать конфиденциальных данных, например на диске, не сохраняются.</span><span class="sxs-lookup"><span data-stu-id="2254a-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="2254a-129">Кроме того не записывайте конфиденциальные данные в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="2254a-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="2254a-130">`WriteOnly` Модификатор может использоваться в этом контексте:</span><span class="sxs-lookup"><span data-stu-id="2254a-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2254a-131">Оператор Property</span><span class="sxs-lookup"><span data-stu-id="2254a-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2254a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="2254a-132">See also</span></span>

- [<span data-ttu-id="2254a-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="2254a-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="2254a-134">Закрытые</span><span class="sxs-lookup"><span data-stu-id="2254a-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="2254a-135">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="2254a-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
