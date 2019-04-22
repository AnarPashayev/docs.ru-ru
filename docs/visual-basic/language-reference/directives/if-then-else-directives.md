---
title: '#If... Then... #Else директивы (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823393"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="782f6-102">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="782f6-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="782f6-103">Условно компилирует выбранные блоки кода Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="782f6-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782f6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="782f6-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="782f6-105">Части</span><span class="sxs-lookup"><span data-stu-id="782f6-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="782f6-106">Требуется для `#If` и `#ElseIf` операторов в другом месте.</span><span class="sxs-lookup"><span data-stu-id="782f6-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="782f6-107">Любое выражение, состоящий только из одного или нескольких константы условной компиляции, литералы и операторы, которые принимает значение `True` или `False`.</span><span class="sxs-lookup"><span data-stu-id="782f6-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="782f6-108">Требуется для `#If` инструкции блока, необязательно в другом месте.</span><span class="sxs-lookup"><span data-stu-id="782f6-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="782f6-109">Строки кода Visual Basic или директивы компилятора, которые компилируются, если связанное выражение, результатом которого является `True`.</span><span class="sxs-lookup"><span data-stu-id="782f6-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="782f6-110">Завершает `#If` блока инструкций.</span><span class="sxs-lookup"><span data-stu-id="782f6-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="782f6-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="782f6-111">Remarks</span></span>  
 <span data-ttu-id="782f6-112">В рабочей области, поведение `#If...Then...#Else` директивы отображается одинаково как для `If...Then...Else` инструкций.</span><span class="sxs-lookup"><span data-stu-id="782f6-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="782f6-113">Тем не менее `#If...Then...#Else` директивы оперируют компилятором, тогда как `If...Then...Else` инструкций оценки условий во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="782f6-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="782f6-114">Условная компиляция обычно используется для компиляции той же программе для разных платформ.</span><span class="sxs-lookup"><span data-stu-id="782f6-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="782f6-115">Он также используется для предотвращения появления в исполняемом файле отладочного кода.</span><span class="sxs-lookup"><span data-stu-id="782f6-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="782f6-116">Код, исключаемый при условной компиляции полностью исключается из итоговый исполняемый файл, поэтому он не влияет на производительность или размер.</span><span class="sxs-lookup"><span data-stu-id="782f6-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="782f6-117">Независимо от результата все вычисления, все выражения вычисляются с помощью `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="782f6-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="782f6-118">`Option Compare` Инструкции не влияет на выражения в `#If` и `#ElseIf` инструкций.</span><span class="sxs-lookup"><span data-stu-id="782f6-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="782f6-119">Не однострочный форма `#If`, `#Else`, `#ElseIf`, и `#End If` существует директивы.</span><span class="sxs-lookup"><span data-stu-id="782f6-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="782f6-120">Никакой другой код могут отображаться на одной строке с любой из директив.</span><span class="sxs-lookup"><span data-stu-id="782f6-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="782f6-121">Операторы в блоке условной компиляции необходимо полных логических операторов.</span><span class="sxs-lookup"><span data-stu-id="782f6-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="782f6-122">Например нельзя условной компиляции только атрибуты функции, но можно условно объявить функцию и ее атрибуты:</span><span class="sxs-lookup"><span data-stu-id="782f6-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="782f6-123">Пример</span><span class="sxs-lookup"><span data-stu-id="782f6-123">Example</span></span>
 <span data-ttu-id="782f6-124">В этом примере используется `#If...Then...#Else` для определения, следует ли компилировать определенных операторов.</span><span class="sxs-lookup"><span data-stu-id="782f6-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="782f6-125">См. также</span><span class="sxs-lookup"><span data-stu-id="782f6-125">See also</span></span>

- [<span data-ttu-id="782f6-126">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="782f6-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="782f6-127">Оператор If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="782f6-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="782f6-128">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="782f6-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
