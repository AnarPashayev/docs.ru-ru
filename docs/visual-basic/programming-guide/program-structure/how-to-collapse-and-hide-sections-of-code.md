---
title: Практическое руководство. Сворачивание и скрытие частей кода (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 367527fd638f6855077caf8ff5911edb333dfcbf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648770"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="1513e-102">Практическое руководство. Сворачивание и скрытие частей кода (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1513e-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="1513e-103">`#Region` Директива позволяет сворачивать и скрывать разделы кода в файлах Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1513e-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="1513e-104">`#Region` Директива позволяет указать блок кода, который можно разворачивать и сворачивать при использовании в редакторе кода Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1513e-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="1513e-105">Возможность выборочно скрыть код делает файлы стала более управляемой и более удобными для чтения.</span><span class="sxs-lookup"><span data-stu-id="1513e-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="1513e-106">Дополнительные сведения см. в разделе [Структура](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="1513e-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="1513e-107">`#Region` директивы поддерживают семантики блока кода, такие как `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="1513e-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="1513e-108">Это означает, что они не может начинаться в одном блоке и заканчиваться в другом; Начало и конец должны быть в одном блоке.</span><span class="sxs-lookup"><span data-stu-id="1513e-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="1513e-109">`#Region` директивы не поддерживаются в функциях.</span><span class="sxs-lookup"><span data-stu-id="1513e-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="1513e-110">Чтобы свернуть и скрыть часть кода</span><span class="sxs-lookup"><span data-stu-id="1513e-110">To collapse and hide a section of code</span></span>  
  
- <span data-ttu-id="1513e-111">Поместите раздел кода между `#Region` и `#End Region` инструкции, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="1513e-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="1513e-112">`#Region` Блок может использоваться несколько раз в файле кода; таким образом, пользователи могут определять свои собственные блоки процедур и классов, которые в свою очередь, может быть свернута.</span><span class="sxs-lookup"><span data-stu-id="1513e-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="1513e-113">`#Region` блоки также могут быть вложены в другие `#Region` блоков.</span><span class="sxs-lookup"><span data-stu-id="1513e-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1513e-114">Скрытие кода не препятствует его компиляции и не влияет на `#If...#End If` инструкций.</span><span class="sxs-lookup"><span data-stu-id="1513e-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1513e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1513e-115">See also</span></span>

- [<span data-ttu-id="1513e-116">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="1513e-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="1513e-117">Директива #Region</span><span class="sxs-lookup"><span data-stu-id="1513e-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="1513e-118">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="1513e-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="1513e-119">Структура</span><span class="sxs-lookup"><span data-stu-id="1513e-119">Outlining</span></span>](/visualstudio/ide/outlining)
