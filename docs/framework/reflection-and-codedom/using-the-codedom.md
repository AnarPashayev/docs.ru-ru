---
title: Использование CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56b0b76e8dc137cbb9346f97604c2d53435c1fe6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045744"
---
# <a name="using-the-codedom"></a><span data-ttu-id="6b248-102">Использование CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b248-102">Using the CodeDOM</span></span>
<span data-ttu-id="6b248-103">CodeDOM содержит типы, представляющие многие общие типы элементов исходного кода.</span><span class="sxs-lookup"><span data-stu-id="6b248-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="6b248-104">Вы можете разработать программу, которая будет строить модель исходного кода, используя элементы CodeDOM для создания графа объектов.</span><span class="sxs-lookup"><span data-stu-id="6b248-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="6b248-105">Этот граф объектов может быть воспроизведен в виде исходного кода с помощью генератора кода CodeDOM для поддерживаемого языка программирования.</span><span class="sxs-lookup"><span data-stu-id="6b248-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="6b248-106">CodeDOM можно также использовать для компиляции исходного кода в двоичную сборку.</span><span class="sxs-lookup"><span data-stu-id="6b248-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="6b248-107">Ниже приведены некоторые примеры применения CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="6b248-107">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="6b248-108">Формирование кода по шаблонам: формирование кода для ASP.NET, клиентских прокси для веб-служб XML, мастеров кода, конструкторов или других механизмов порождения кода.</span><span class="sxs-lookup"><span data-stu-id="6b248-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="6b248-109">Динамическая компиляция: поддержка компиляции кода на одном языке или нескольких языках программирования.</span><span class="sxs-lookup"><span data-stu-id="6b248-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="6b248-110">Построение графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b248-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="6b248-111">Пространство имен <xref:System.CodeDom> предоставляет классы для представления логической структуры исходного кода, независимой от синтаксиса языка.</span><span class="sxs-lookup"><span data-stu-id="6b248-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="6b248-112">Структура графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b248-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="6b248-113">Структура графа CodeDOM представляет собой дерево контейнеров.</span><span class="sxs-lookup"><span data-stu-id="6b248-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="6b248-114">Самым верхним (корневым) контейнером каждого графа CodeDOM, доступного для компиляции, является <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="6b248-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="6b248-115">Каждый элемент модели исходного кода должен быть связан с графом посредством свойства <xref:System.CodeDom.CodeObject> в графе.</span><span class="sxs-lookup"><span data-stu-id="6b248-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="6b248-116">Построение модели исходного кода для образца программы "Hello, World"</span><span class="sxs-lookup"><span data-stu-id="6b248-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="6b248-117">Ниже приведено пошаговое руководство по построению графа объектов CodeDOM, представляющего код для простого приложения "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="6b248-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="6b248-118">Полный исходный код для этого примера см. в разделе <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b248-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="6b248-119">Создание модуля компиляции</span><span class="sxs-lookup"><span data-stu-id="6b248-119">Creating a compile unit</span></span>  
 <span data-ttu-id="6b248-120">CodeDOM определяет объект с именем <xref:System.CodeDom.CodeCompileUnit>, который может ссылаться на граф объектов CodeDOM, моделирующий компилируемый исходный код.</span><span class="sxs-lookup"><span data-stu-id="6b248-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="6b248-121">В свойствах объекта **CodeCompileUnit** могут храниться ссылки на атрибуты, пространства имен и сборки.</span><span class="sxs-lookup"><span data-stu-id="6b248-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="6b248-122">Поставщики CodeDom, производные от класса <xref:System.CodeDom.Compiler.CodeDomProvider>, содержат методы, которые обрабатывают граф объектов, на который ссылается **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b248-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="6b248-123">Чтобы создать граф объектов для простого приложения, необходимо собрать модель исходного кода и сослаться на нее из **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b248-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="6b248-124">В следующем примере приведен синтаксис для создания модуля компиляции.</span><span class="sxs-lookup"><span data-stu-id="6b248-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="6b248-125"><xref:System.CodeDom.CodeSnippetCompileUnit> может содержать раздел исходного кода, который уже написан на целевом языке, но не может быть преобразован в другой язык.</span><span class="sxs-lookup"><span data-stu-id="6b248-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="6b248-126">Определение пространства имен</span><span class="sxs-lookup"><span data-stu-id="6b248-126">Defining a namespace</span></span>  
 <span data-ttu-id="6b248-127">Чтобы определить пространство имен, необходимо создать объект <xref:System.CodeDom.CodeNamespace>, а затем присвоить ему имя, используя подходящий конструктор или установив значение свойства **Name**.</span><span class="sxs-lookup"><span data-stu-id="6b248-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="6b248-128">Импорт пространства имен</span><span class="sxs-lookup"><span data-stu-id="6b248-128">Importing a namespace</span></span>  
 <span data-ttu-id="6b248-129">Чтобы добавить в пространство имен директиву импорта пространства имен, добавьте <xref:System.CodeDom.CodeNamespaceImport>, который указывает пространство имен, которое следует импортировать в коллекцию **CodeNamespace.Imports**.</span><span class="sxs-lookup"><span data-stu-id="6b248-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="6b248-130">В следующем фрагменте кода пространство имен **System** импортируется в коллекцию **Imports** объекта **CodeNamespace** с именем `samples`:</span><span class="sxs-lookup"><span data-stu-id="6b248-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="6b248-131">Связывание элементов кода с графом объектов</span><span class="sxs-lookup"><span data-stu-id="6b248-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="6b248-132">Все элементы кода, образующие граф CodeDOM, должны быть связаны с объектом <xref:System.CodeDom.CodeCompileUnit>, являющимся корневым элементом дерева, последовательностью ссылок между элементами, на которые имеются прямые ссылки из свойств корневого объекта графа.</span><span class="sxs-lookup"><span data-stu-id="6b248-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="6b248-133">Чтобы задать ссылку из объекта-контейнера, необходимо присвоить объект свойству объекта-контейнера.</span><span class="sxs-lookup"><span data-stu-id="6b248-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="6b248-134">Приведенный ниже оператор добавляет `samples` **CodeNamespace** в свойство коллекции **Namespaces** корневого объекта **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b248-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="6b248-135">Определение типа</span><span class="sxs-lookup"><span data-stu-id="6b248-135">Defining a type</span></span>  
 <span data-ttu-id="6b248-136">Чтобы объявить класс, структуру, интерфейс или перечисление с помощью CodeDOM, создайте объявление <xref:System.CodeDom.CodeTypeDeclaration> и присвойте ему имя.</span><span class="sxs-lookup"><span data-stu-id="6b248-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="6b248-137">В приведенном ниже примере демонстрируется использование перегрузки конструктора для задания значения свойства **Name**.</span><span class="sxs-lookup"><span data-stu-id="6b248-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="6b248-138">Чтобы добавить тип в пространство имен, добавьте объект <xref:System.CodeDom.CodeTypeDeclaration>, представляющий тип, который следует добавить в коллекцию **Types** пространства имен **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="6b248-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="6b248-139">В следующем примере демонстрируется добавление класса `class1` в пространство имен **CodeNamespace** с именем `samples`:</span><span class="sxs-lookup"><span data-stu-id="6b248-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="6b248-140">Добавление в класс членов класса</span><span class="sxs-lookup"><span data-stu-id="6b248-140">Adding class members to a class</span></span>  
 <span data-ttu-id="6b248-141">Пространство имен <xref:System.CodeDom> предоставляет различные элементы, которые можно использовать для представления членов класса.</span><span class="sxs-lookup"><span data-stu-id="6b248-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="6b248-142">Каждый элемент класса может быть добавлен в коллекцию **Members** объекта <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="6b248-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="6b248-143">Определение метода, являющегося точкой входа в код исполняемого файла</span><span class="sxs-lookup"><span data-stu-id="6b248-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="6b248-144">В случае сборки кода исполняемой программы необходимо указать точку входа в программу, создав объект <xref:System.CodeDom.CodeEntryPointMethod> для представления метода, с которого должно начинаться выполнение программы.</span><span class="sxs-lookup"><span data-stu-id="6b248-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="6b248-145">В следующем примере показано, как определить метод точки входа, который содержит объект <xref:System.CodeDom.CodeMethodInvokeExpression>, вызывающий **System.Console.WriteLine** для вывода текста "Hello World!":</span><span class="sxs-lookup"><span data-stu-id="6b248-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="6b248-146">Приведенный ниже оператор добавляет метод точки входа `Start` в коллекцию **Members** класса `class1`.</span><span class="sxs-lookup"><span data-stu-id="6b248-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="6b248-147">Теперь объект <xref:System.CodeDom.CodeCompileUnit> с именем `compileUnit` содержит граф CodeDOM для простой программы "Hello World".</span><span class="sxs-lookup"><span data-stu-id="6b248-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="6b248-148">Сведения о создании и компиляции кода на основе графа CodeDOM см. в разделе [Создание исходного кода и компиляция программы из графа CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="6b248-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="6b248-149">Дополнительные сведения о построении графа CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b248-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="6b248-150">CodeDOM поддерживает многие общие типы элементов кода, которые встречаются в языках программирования, поддерживающих среду CLR.</span><span class="sxs-lookup"><span data-stu-id="6b248-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="6b248-151">Но CodeDOM не предусматривает предоставление элементов для представления всех возможных функций языков программирования.</span><span class="sxs-lookup"><span data-stu-id="6b248-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="6b248-152">Код, который не может быть без труда представлен элементами CodeDOM, можно инкапсулировать в объекты <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember> или <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="6b248-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="6b248-153">Но фрагменты кода невозможно автоматически переводить с помощью CodeDOM на другие языки.</span><span class="sxs-lookup"><span data-stu-id="6b248-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="6b248-154">Сведения о каждом типе CodeDOM см. в справочной документации по пространству имен <xref:System.CodeDom>.</span><span class="sxs-lookup"><span data-stu-id="6b248-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="6b248-155">Быстро найти элемент CodeDOM, представляющий определенный тип элемента кода, можно в разделе [Краткий справочник по CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6b248-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
