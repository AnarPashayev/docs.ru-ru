---
title: Ссылки и оператор Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: f3396eb3e758dc456d86de80246de24349680f2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967756"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="b3efc-102">Ссылки и оператор Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3efc-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="b3efc-103">Вы внешние объекты можно сделать доступными в проект, выбрав **добавить ссылку** команды **проекта** меню.</span><span class="sxs-lookup"><span data-stu-id="b3efc-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="b3efc-104">Ссылки в Visual Basic могут указывать на сборки, которые подобны библиотек типов, но содержат больше сведений.</span><span class="sxs-lookup"><span data-stu-id="b3efc-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="b3efc-105">Оператор Imports</span><span class="sxs-lookup"><span data-stu-id="b3efc-105">The Imports Statement</span></span>  
 <span data-ttu-id="b3efc-106">Сборки содержат один или несколько пространств имен.</span><span class="sxs-lookup"><span data-stu-id="b3efc-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="b3efc-107">При добавлении ссылки на сборку, можно также добавить `Imports` инструкции модулю, который управляет видимостью пространств имен в модуль этой сборки.</span><span class="sxs-lookup"><span data-stu-id="b3efc-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="b3efc-108">`Imports` Инструкция предоставляет контекст области видимости, которая позволяет использовать только часть пространства имен, необходимые для предоставления уникальной ссылки.</span><span class="sxs-lookup"><span data-stu-id="b3efc-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="b3efc-109">`Imports` Инструкция имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="b3efc-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="b3efc-110">`Aliasname` ссылается на короткое имя, которое можно использовать в коде для ссылки на импортированное пространство имен.</span><span class="sxs-lookup"><span data-stu-id="b3efc-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="b3efc-111">`Namespace` — Это пространство имен, доступное через ссылку на проект, через определение в проект, или с помощью предыдущего `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="b3efc-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="b3efc-112">Модуль может содержать любое количество `Imports` инструкций.</span><span class="sxs-lookup"><span data-stu-id="b3efc-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="b3efc-113">Они должны располагаться после `Option` инструкций, если он присутствует, но перед любым другим кодом.</span><span class="sxs-lookup"><span data-stu-id="b3efc-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3efc-114">Не следует путать ссылки на проекты с `Imports` инструкции или `Declare` инструкции.</span><span class="sxs-lookup"><span data-stu-id="b3efc-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="b3efc-115">Ссылки на проекты делают внешние объекты, такие как объекты в сборках, доступные для проектов Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3efc-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="b3efc-116">`Imports` Инструкция используется для упрощения доступа перекрестные ссылки между проектами, но не предоставляет доступ к этим объектам.</span><span class="sxs-lookup"><span data-stu-id="b3efc-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="b3efc-117">`Declare` Оператор используется для объявления ссылки на внешнюю процедуру в библиотеке динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="b3efc-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="b3efc-118">Использование псевдонимов с оператор Imports</span><span class="sxs-lookup"><span data-stu-id="b3efc-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="b3efc-119">`Imports` Инструкции облегчает доступ к методам классов, устраняя необходимость явно вводить полные имена ссылок.</span><span class="sxs-lookup"><span data-stu-id="b3efc-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="b3efc-120">Псевдонимы позволяют назначить более понятные имена только на одну часть пространства имен.</span><span class="sxs-lookup"><span data-stu-id="b3efc-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="b3efc-121">Например, возврат каретки и перевод строки последовательность, которая вызывает одну часть текста, отображаемого на нескольких строках является частью <xref:Microsoft.VisualBasic.ControlChars> модуля в <xref:Microsoft.VisualBasic?displayProperty=nameWithType> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="b3efc-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b3efc-122">Для использования этой константы в программе без псевдонима, потребовалось бы введите следующий код:</span><span class="sxs-lookup"><span data-stu-id="b3efc-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="b3efc-123">`Imports` операторы всегда должны сразу же после первых строк `Option` инструкции в модуле.</span><span class="sxs-lookup"><span data-stu-id="b3efc-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="b3efc-124">В следующем фрагменте кода показано, как импортировать и присваивать псевдоним <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> модуля:</span><span class="sxs-lookup"><span data-stu-id="b3efc-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b3efc-125">Будущие ссылки на это пространство имен может быть значительно меньше:</span><span class="sxs-lookup"><span data-stu-id="b3efc-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="b3efc-126">Если `Imports` инструкция не включает имя псевдонима, элементы, определенные в импортированном пространстве имен, которые могут использоваться в модуле без указания полного имени.</span><span class="sxs-lookup"><span data-stu-id="b3efc-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="b3efc-127">Если указано имя псевдонима, он должен использоваться как квалификатор для имен, содержащихся в этом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="b3efc-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3efc-128">См. также</span><span class="sxs-lookup"><span data-stu-id="b3efc-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="b3efc-129">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3efc-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="b3efc-130">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="b3efc-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="b3efc-131">Практическое руководство. Создание и использование сборок с помощью командной строки</span><span class="sxs-lookup"><span data-stu-id="b3efc-131">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [<span data-ttu-id="b3efc-132">Оператор Imports (пространство имен и тип .NET)</span><span class="sxs-lookup"><span data-stu-id="b3efc-132">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
