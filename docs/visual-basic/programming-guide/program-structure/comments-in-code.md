---
title: Комментарии в коде
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 9f9174896181e427c73936a1bb91fa13235e70be
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550993"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="f23b5-102">Комментарии в коде (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23b5-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="f23b5-103">В примерах кодов часто встречается символ начала комментария (`'`).</span><span class="sxs-lookup"><span data-stu-id="f23b5-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="f23b5-104">Этот символ указывает компилятору Visual Basic игнорировать текст, следующий за ним, или *Комментарий*.</span><span class="sxs-lookup"><span data-stu-id="f23b5-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="f23b5-105">Комментарии — это краткие заметки, внесенные в код, чтобы сделать чтение кода более легким.</span><span class="sxs-lookup"><span data-stu-id="f23b5-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="f23b5-106">Хорошим стилем программирования считается начинать все процедуры с краткого комментария, описывающего функциональные характеристики процедуры (то, что она делает).</span><span class="sxs-lookup"><span data-stu-id="f23b5-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="f23b5-107">Это необходимо для вашего собственного удобства и удобства того, кто читает этот код.</span><span class="sxs-lookup"><span data-stu-id="f23b5-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="f23b5-108">Следует отличать детали реализации (как процедура работает) от комментариев, описывающих функциональные характеристики.</span><span class="sxs-lookup"><span data-stu-id="f23b5-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="f23b5-109">Если в комментарий включены детали реализации, их следует обновлять при редактировании кода.</span><span class="sxs-lookup"><span data-stu-id="f23b5-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="f23b5-110">Комментарии могут располагаться в конце той же строки, где содержится оператор, или занимать отдельную строку.</span><span class="sxs-lookup"><span data-stu-id="f23b5-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="f23b5-111">Оба способа представлены в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="f23b5-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="f23b5-112">Если комментарий занимает более одной строки, каждая строка должна начинаться с символа начала комментария, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f23b5-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="f23b5-113">Правила комментирования</span><span class="sxs-lookup"><span data-stu-id="f23b5-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="f23b5-114">В следующей таблице приведены общие рекомендации по тому, какие типы комментариев могут предшествовать разделу кода.</span><span class="sxs-lookup"><span data-stu-id="f23b5-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="f23b5-115">Это предложения; Visual Basic не применяет правила для добавления комментариев.</span><span class="sxs-lookup"><span data-stu-id="f23b5-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="f23b5-116">В комментарий по желанию автора кода может быть включена любая информация.</span><span class="sxs-lookup"><span data-stu-id="f23b5-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="f23b5-117">Тип комментария</span><span class="sxs-lookup"><span data-stu-id="f23b5-117">Comment type</span></span>|<span data-ttu-id="f23b5-118">Описание комментария</span><span class="sxs-lookup"><span data-stu-id="f23b5-118">Comment description</span></span>|  
|<span data-ttu-id="f23b5-119">Назначение</span><span class="sxs-lookup"><span data-stu-id="f23b5-119">Purpose</span></span>|<span data-ttu-id="f23b5-120">Описание действий, совершаемых процедурой (но не того, каким образом совершаются эти действия)</span><span class="sxs-lookup"><span data-stu-id="f23b5-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="f23b5-121">Предположения</span><span class="sxs-lookup"><span data-stu-id="f23b5-121">Assumptions</span></span>|<span data-ttu-id="f23b5-122">Список всех внешних переменных, элементов управления, открытых файлов, к которым осуществляется доступ из процедуры </span><span class="sxs-lookup"><span data-stu-id="f23b5-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="f23b5-123">Произведенный эффект</span><span class="sxs-lookup"><span data-stu-id="f23b5-123">Effects</span></span>|<span data-ttu-id="f23b5-124">Список внешних переменных, элементов управления или файлов, на которые влияет данная процедура (если это влияние не очевидно)</span><span class="sxs-lookup"><span data-stu-id="f23b5-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="f23b5-125">Входные данные</span><span class="sxs-lookup"><span data-stu-id="f23b5-125">Inputs</span></span>|<span data-ttu-id="f23b5-126">Описание назначения аргументов</span><span class="sxs-lookup"><span data-stu-id="f23b5-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="f23b5-127">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f23b5-127">Returns</span></span>|<span data-ttu-id="f23b5-128">Описание значений, возвращаемых процедурой</span><span class="sxs-lookup"><span data-stu-id="f23b5-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="f23b5-129">Также рекомендуется принять во внимание следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="f23b5-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="f23b5-130">Объявление каждой важной переменной должно предшествовать комментарию, описывающему ее назначение.</span><span class="sxs-lookup"><span data-stu-id="f23b5-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="f23b5-131">Имена переменных, элементов управления и процедур должны быть функционально понятными, чтобы комментарии требовались только в случае особо сложных деталей реализации.</span><span class="sxs-lookup"><span data-stu-id="f23b5-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="f23b5-132">Комментарии не могут располагаться за последовательностью продолжения строки в той же строке.</span><span class="sxs-lookup"><span data-stu-id="f23b5-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="f23b5-133">Можно добавить или удалить символы комментария для блока кода, выбрав одну или несколько строк кода и выбрав **Комментарий** ( ![ кнопка комментария Visual Basic в Visual Studio. ](./media/comments-in-code/visual-basic-comment-button.gif) ) и **раскомментировать** ( ![ кнопка Visual Basic отмена комментария в Visual Studio. ](./media/comments-in-code/visual-basic-uncomment-button.gif) ) на панели инструментов **изменить** .</span><span class="sxs-lookup"><span data-stu-id="f23b5-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f23b5-134">Кроме того, можно добавить в код комментарии, поставив в начале текста ключевое слово `REM`.</span><span class="sxs-lookup"><span data-stu-id="f23b5-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="f23b5-135">Однако кнопки " `'` символ" и " **комментарий к комментарию**" / **Uncomment** проще в использовании и занимают меньше пространства и памяти.</span><span class="sxs-lookup"><span data-stu-id="f23b5-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23b5-136">См. также</span><span class="sxs-lookup"><span data-stu-id="f23b5-136">See also</span></span>

- [<span data-ttu-id="f23b5-137">Базовый инстинкты — документирование кода с помощью XML-комментариев</span><span class="sxs-lookup"><span data-stu-id="f23b5-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="f23b5-138">Практическое руководство. Создание XML-документации</span><span class="sxs-lookup"><span data-stu-id="f23b5-138">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="f23b5-139">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="f23b5-139">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="f23b5-140">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="f23b5-140">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="f23b5-141">Оператор REM</span><span class="sxs-lookup"><span data-stu-id="f23b5-141">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
