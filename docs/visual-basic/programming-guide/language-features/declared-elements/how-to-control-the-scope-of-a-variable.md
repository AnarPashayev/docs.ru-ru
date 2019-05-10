---
title: Практическое руководство. Управление областью действия переменной (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 7f1d671f6657c7810ec605533493a340baac39c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610341"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="008ff-102">Практическое руководство. Управление областью действия переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="008ff-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="008ff-103">Как правило, переменная находится в *область*, или доступна для ссылки на протяжении всего региона, в котором она объявлена.</span><span class="sxs-lookup"><span data-stu-id="008ff-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="008ff-104">В некоторых случаях переменная элемента *уровень доступа* может влиять на ее область действия.</span><span class="sxs-lookup"><span data-stu-id="008ff-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="008ff-105">Для получения дополнительной информации см. [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="008ff-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="008ff-106">Область действия на уровне блока или процедуры</span><span class="sxs-lookup"><span data-stu-id="008ff-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="008ff-107">Чтобы сделать переменную видимой только внутри блока</span><span class="sxs-lookup"><span data-stu-id="008ff-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="008ff-108">Место [оператор Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) для переменной между начальными и конечными операторы объявления блока, например между `For` и `Next` констатация `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="008ff-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="008ff-109">Можно ссылаться только из переменной в блоке.</span><span class="sxs-lookup"><span data-stu-id="008ff-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="008ff-110">Чтобы сделать переменную видимой только внутри процедуры</span><span class="sxs-lookup"><span data-stu-id="008ff-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="008ff-111">Место `Dim` инструкцию для переменной внутри процедуры, но вне любого блока (такие как `With`... `End With` блок).</span><span class="sxs-lookup"><span data-stu-id="008ff-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="008ff-112">Можно ссылаться только из переменной внутри процедуры, в том числе внутри любого блока, содержащегося в процедуре.</span><span class="sxs-lookup"><span data-stu-id="008ff-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="008ff-113">Область на модуль или пространство имен</span><span class="sxs-lookup"><span data-stu-id="008ff-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="008ff-114">Для удобства один термин *уровне модуля* применяется одинаково для модулей, классов и структур.</span><span class="sxs-lookup"><span data-stu-id="008ff-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="008ff-115">Уровень доступа к переменной уровня модуля определяет ее область действия.</span><span class="sxs-lookup"><span data-stu-id="008ff-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="008ff-116">Эту область также влияет на пространство имен, содержащее модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="008ff-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="008ff-117">Чтобы сделать переменную видимой во всей модуля, класса или структуры</span><span class="sxs-lookup"><span data-stu-id="008ff-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="008ff-118">Место `Dim` инструкцию для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="008ff-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="008ff-119">Включить [частного](../../../../visual-basic/language-reference/modifiers/private.md) ключевое слово в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="008ff-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="008ff-120">Можно ссылаться на значение переменной из любого места внутри модуля, класса или структуры, но не из за его пределами.</span><span class="sxs-lookup"><span data-stu-id="008ff-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="008ff-121">Чтобы сделать переменную видимой во всей пространства имен</span><span class="sxs-lookup"><span data-stu-id="008ff-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="008ff-122">Место `Dim` инструкцию для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="008ff-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="008ff-123">Включить [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) или [открытый](../../../../visual-basic/language-reference/modifiers/public.md) ключевое слово в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="008ff-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="008ff-124">В переменную можно ссылаться из любого места в пространство имен, содержащее модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="008ff-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="008ff-125">Пример</span><span class="sxs-lookup"><span data-stu-id="008ff-125">Example</span></span>  
 <span data-ttu-id="008ff-126">В следующем примере объявляется переменная на уровне модуля и ограничивает видимость для кода в модуле.</span><span class="sxs-lookup"><span data-stu-id="008ff-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="008ff-127">В приведенном выше примере все процедуры, определенные в модуле `demonstrateScope` могут ссылаться на `String` переменной `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="008ff-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="008ff-128">Когда `usePrivateVariable` процедура вызывается, он отображает содержимое переменной строки `strMsg` в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="008ff-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="008ff-129">Со следующими изменениями в предыдущем примере строковая переменная `strMsg` можно обращаться к любым кодом в ее объявлении пространства имен.</span><span class="sxs-lookup"><span data-stu-id="008ff-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="008ff-130">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="008ff-130">Robust Programming</span></span>  
 <span data-ttu-id="008ff-131">Чем короче область переменной, тем меньше возможностей, которыми обладает пользователь случайно обращения к нему вместо другую переменную с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="008ff-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="008ff-132">Также можно свести к минимуму проблемы с соответствием ссылки.</span><span class="sxs-lookup"><span data-stu-id="008ff-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="008ff-133">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="008ff-133">.NET Framework Security</span></span>  
 <span data-ttu-id="008ff-134">Более узкой областью действия переменной, тем меньше вероятность того, что вредоносный код может использовать неправильной его использовать.</span><span class="sxs-lookup"><span data-stu-id="008ff-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008ff-135">См. также</span><span class="sxs-lookup"><span data-stu-id="008ff-135">See also</span></span>

- [<span data-ttu-id="008ff-136">Область, в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="008ff-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="008ff-137">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="008ff-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="008ff-138">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="008ff-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="008ff-139">Переменные</span><span class="sxs-lookup"><span data-stu-id="008ff-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="008ff-140">Объявление переменных</span><span class="sxs-lookup"><span data-stu-id="008ff-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="008ff-141">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="008ff-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
