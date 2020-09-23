---
title: Соглашения о структуре программы и коде
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: ee61c676f3ff554267f6659453ec55e45df69aee
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072123"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="a71cf-102">Соглашения о структуре программы и коде (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a71cf-102">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="a71cf-103">В этом разделе представлен типичная структура программы Visual Basic, предусмотрена простая Visual Basicная программа, "Hello, World" и обсуждаются Visual Basic соглашения о коде.</span><span class="sxs-lookup"><span data-stu-id="a71cf-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="a71cf-104">Соглашения о коде — это рекомендации, которые касаются не логики программы, а ее физической структуры и внешнего вида.</span><span class="sxs-lookup"><span data-stu-id="a71cf-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="a71cf-105">После этого код упрощает чтение, понимание и обслуживание.</span><span class="sxs-lookup"><span data-stu-id="a71cf-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="a71cf-106">Соглашения о коде могут включать, среди прочего:</span><span class="sxs-lookup"><span data-stu-id="a71cf-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="a71cf-107">Стандартизированные форматы для добавления меток и комментирования кода.</span><span class="sxs-lookup"><span data-stu-id="a71cf-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="a71cf-108">Рекомендации по расстоянию, форматированию и отступу кода.</span><span class="sxs-lookup"><span data-stu-id="a71cf-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="a71cf-109">Соглашения об именовании для объектов, переменных и процедур.</span><span class="sxs-lookup"><span data-stu-id="a71cf-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="a71cf-110">В следующих разделах представлен набор руководств по программированию для Visual Basic программ, а также примеры хорошего использования.</span><span class="sxs-lookup"><span data-stu-id="a71cf-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a71cf-111">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="a71cf-111">In This Section</span></span>  

 [<span data-ttu-id="a71cf-112">Структура программы Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-112">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="a71cf-113">Содержит общие сведения об элементах, составляющих программу Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a71cf-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="a71cf-114">Процедура Main в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-114">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="a71cf-115">Описание процедуры, которая служит начальной точкой и общим элементом управления для приложения.</span><span class="sxs-lookup"><span data-stu-id="a71cf-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="a71cf-116">Ссылки и оператор Imports</span><span class="sxs-lookup"><span data-stu-id="a71cf-116">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="a71cf-117">Описывает, как ссылаться на объекты в других сборках.</span><span class="sxs-lookup"><span data-stu-id="a71cf-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="a71cf-118">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-118">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="a71cf-119">Описывает, как пространства имен упорядочивают объекты в сборках.</span><span class="sxs-lookup"><span data-stu-id="a71cf-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="a71cf-120">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-120">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="a71cf-121">Содержит общие рекомендации по именованию процедур, констант, переменных, аргументов и объектов.</span><span class="sxs-lookup"><span data-stu-id="a71cf-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="a71cf-122">Соглашения о написании кода в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-122">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="a71cf-123">Просматривает рекомендации, используемые при разработке примеров в этой документации.</span><span class="sxs-lookup"><span data-stu-id="a71cf-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="a71cf-124">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="a71cf-124">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="a71cf-125">Описывает, как можно выборочно компилировать определенные блоки кода, направляя компилятору возможность игнорировать другие.</span><span class="sxs-lookup"><span data-stu-id="a71cf-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="a71cf-126">Практическое руководство. Разбиение и объединение инструкций в коде</span><span class="sxs-lookup"><span data-stu-id="a71cf-126">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="a71cf-127">Показывает, как разделить длинные операторы на несколько строк и объединить короткие операторы в одной строке.</span><span class="sxs-lookup"><span data-stu-id="a71cf-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="a71cf-128">Практическое руководство. Сворачивание и скрытие частей кода</span><span class="sxs-lookup"><span data-stu-id="a71cf-128">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="a71cf-129">Показывает, как сворачивать и скрывать разделы кода в редакторе кода Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a71cf-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="a71cf-130">Практическое руководство. Операторы меток</span><span class="sxs-lookup"><span data-stu-id="a71cf-130">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="a71cf-131">Показывает, как пометить строку кода, чтобы она определялась для использования с такими операторами, как `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="a71cf-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="a71cf-132">Специальные символы в коде</span><span class="sxs-lookup"><span data-stu-id="a71cf-132">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="a71cf-133">Показывает, как и где следует использовать нечисловые и неалфавитные символы.</span><span class="sxs-lookup"><span data-stu-id="a71cf-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="a71cf-134">Комментарии в коде</span><span class="sxs-lookup"><span data-stu-id="a71cf-134">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="a71cf-135">Описывает, как добавлять описательные комментарии в код.</span><span class="sxs-lookup"><span data-stu-id="a71cf-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="a71cf-136">Ключевые слова как имена элементов в коде</span><span class="sxs-lookup"><span data-stu-id="a71cf-136">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="a71cf-137">Описывает использование квадратных скобок ( `[]` ) для разделения имен переменных, которые также Visual Basic ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="a71cf-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="a71cf-138">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="a71cf-138">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="a71cf-139">Описывает различные способы ссылки на элементы программы Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a71cf-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="a71cf-140">Ограничения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a71cf-140">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="a71cf-141">Обсуждается удаление известных ограничений на написание кода в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a71cf-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a71cf-142">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="a71cf-142">Related Sections</span></span>  

 [<span data-ttu-id="a71cf-143">Условные обозначения и соглашения о коде</span><span class="sxs-lookup"><span data-stu-id="a71cf-143">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="a71cf-144">Предоставляет стандартные соглашения о кодировании для Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a71cf-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="a71cf-145">Написание кода</span><span class="sxs-lookup"><span data-stu-id="a71cf-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="a71cf-146">Описание функций, упрощающих написание кода и управление им.</span><span class="sxs-lookup"><span data-stu-id="a71cf-146">Describes features that make it easier for you to write and manage your code.</span></span>
