---
title: Оператор Resume (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583278"
---
# <a name="resume-statement"></a><span data-ttu-id="de70b-102">Оператор Resume</span><span class="sxs-lookup"><span data-stu-id="de70b-102">Resume Statement</span></span>
<span data-ttu-id="de70b-103">Возобновляет выполнение по завершении подпрограммы обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="de70b-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="de70b-104">Мы рекомендуем использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и инструкций `On Error` и `Resume`.</span><span class="sxs-lookup"><span data-stu-id="de70b-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="de70b-105">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de70b-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de70b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de70b-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="de70b-107">Части</span><span class="sxs-lookup"><span data-stu-id="de70b-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="de70b-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="de70b-108">Required.</span></span> <span data-ttu-id="de70b-109">Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="de70b-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="de70b-110">Если ошибка произошла в вызванной процедуре, выполнение возобновляется с оператора, который последний раз вызывался из процедуры, содержащей подпрограмму обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="de70b-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="de70b-111">Необязательный.</span><span class="sxs-lookup"><span data-stu-id="de70b-111">Optional.</span></span> <span data-ttu-id="de70b-112">Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, следующей за инструкцией, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="de70b-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="de70b-113">Если ошибка произошла в вызываемой процедуре, выполнение возобновляется с помощью инструкции, следующей за инструкцией, которая была вызвана из процедуры, содержащей подпрограмму обработки ошибок (или инструкцию `On Error Resume Next`).</span><span class="sxs-lookup"><span data-stu-id="de70b-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="de70b-114">Необязательный.</span><span class="sxs-lookup"><span data-stu-id="de70b-114">Optional.</span></span> <span data-ttu-id="de70b-115">Выполнение возобновляется в строке, указанной в аргументе Required `line`.</span><span class="sxs-lookup"><span data-stu-id="de70b-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="de70b-116">Аргумент `line` является меткой или номером строки и должен находиться в той же процедуре, что и обработчик ошибок.</span><span class="sxs-lookup"><span data-stu-id="de70b-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de70b-117">Заметки</span><span class="sxs-lookup"><span data-stu-id="de70b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de70b-118">Рекомендуется использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и инструкций `On Error` и `Resume`.</span><span class="sxs-lookup"><span data-stu-id="de70b-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="de70b-119">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de70b-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="de70b-120">При использовании оператора `Resume` в любом месте, кроме в подпрограммы обработки ошибок, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="de70b-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="de70b-121">Инструкцию `Resume` нельзя использовать в любой процедуре, содержащей инструкцию `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="de70b-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de70b-122">Пример</span><span class="sxs-lookup"><span data-stu-id="de70b-122">Example</span></span>  
 <span data-ttu-id="de70b-123">В этом примере оператор `Resume` используется для завершения обработки ошибок в процедуре и возобновления выполнения с инструкцией, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="de70b-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="de70b-124">Для иллюстрации использования оператора `Resume` создается ошибка с номером 55.</span><span class="sxs-lookup"><span data-stu-id="de70b-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="de70b-125">Требования</span><span class="sxs-lookup"><span data-stu-id="de70b-125">Requirements</span></span>  
 <span data-ttu-id="de70b-126">**Пространство имен:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="de70b-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="de70b-127">**Сборка:** Библиотека времени выполнения Visual Basic (в Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="de70b-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de70b-128">См. также</span><span class="sxs-lookup"><span data-stu-id="de70b-128">See also</span></span>

- [<span data-ttu-id="de70b-129">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="de70b-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="de70b-130">Оператор Error</span><span class="sxs-lookup"><span data-stu-id="de70b-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="de70b-131">Оператор On Error</span><span class="sxs-lookup"><span data-stu-id="de70b-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
