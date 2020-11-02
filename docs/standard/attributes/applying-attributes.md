---
title: Применение атрибутов
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 24fe58ddf48e40b422652baa4c5bba86eea6b84f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889235"
---
# <a name="apply-attributes"></a><span data-ttu-id="556de-102">Применение атрибутов</span><span class="sxs-lookup"><span data-stu-id="556de-102">Apply attributes</span></span>

<span data-ttu-id="556de-103">Чтобы применить атрибут к элементу кода, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="556de-103">Use the following process to apply an attribute to an element of your code.</span></span>

1. <span data-ttu-id="556de-104">Определите новый атрибут или используйте существующий атрибут .NET.</span><span class="sxs-lookup"><span data-stu-id="556de-104">Define a new attribute or use an existing .NET attribute.</span></span>

2. <span data-ttu-id="556de-105">Примените атрибут к элементу кода, поместив его непосредственно перед элементом.</span><span class="sxs-lookup"><span data-stu-id="556de-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>

     <span data-ttu-id="556de-106">Каждый язык имеет собственный синтаксис атрибутов.</span><span class="sxs-lookup"><span data-stu-id="556de-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="556de-107">В C++ и C# атрибут заключается в квадратные скобки и отделяется от элемента пробелами (к которым относится и разрыв строк).</span><span class="sxs-lookup"><span data-stu-id="556de-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="556de-108">В Visual Basic атрибут заключается в угловые скобки и должен находиться на той же логической строке; если строку необходимо разбить, можно использовать символ продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="556de-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>

3. <span data-ttu-id="556de-109">Укажите позиционные и именованные параметры атрибута.</span><span class="sxs-lookup"><span data-stu-id="556de-109">Specify positional parameters and named parameters for the attribute.</span></span>

     <span data-ttu-id="556de-110">*Позиционные* параметры обязательны и должны быть указаны перед именованными параметрами; они соответствуют параметрам одного из конструкторов атрибута.</span><span class="sxs-lookup"><span data-stu-id="556de-110">*Positional* parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="556de-111">*Именованные* параметры необязательны и соответствуют свойствам чтения и записи атрибута.</span><span class="sxs-lookup"><span data-stu-id="556de-111">*Named* parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="556de-112">В C++ и C# укажите `name=value` для каждого необязательного параметра, где `name` — это имя свойства.</span><span class="sxs-lookup"><span data-stu-id="556de-112">In C++, and C#, specify `name=value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="556de-113">В Visual Basic укажите `name:=value`.</span><span class="sxs-lookup"><span data-stu-id="556de-113">In Visual Basic, specify `name:=value`.</span></span>

 <span data-ttu-id="556de-114">При компиляции кода атрибут передается в метаданные и становится доступным для среды CLR, а также пользовательских средств и приложений через службы отражения среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="556de-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>

 <span data-ttu-id="556de-115">Как правило, все имена атрибутов заканчиваются словом Attribute.</span><span class="sxs-lookup"><span data-stu-id="556de-115">By convention, all attribute names end with "Attribute".</span></span> <span data-ttu-id="556de-116">В то же время несколько языков, предназначенных для среды выполнения, таких как Visual Basic и C#, не требуют указывать полное имя атрибута.</span><span class="sxs-lookup"><span data-stu-id="556de-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="556de-117">Например, если вам нужно инициализировать <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, достаточно указать имя **Obsolete** .</span><span class="sxs-lookup"><span data-stu-id="556de-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete** .</span></span>

## <a name="apply-an-attribute-to-a-method"></a><span data-ttu-id="556de-118">Применение атрибута к методу</span><span class="sxs-lookup"><span data-stu-id="556de-118">Apply an attribute to a method</span></span>

 <span data-ttu-id="556de-119">В следующем примере кода показано, как использовать атрибут **System.ObsoleteAttribute** , помечающий код как устаревший.</span><span class="sxs-lookup"><span data-stu-id="556de-119">The following code example shows how to use **System.ObsoleteAttribute** , which marks code as obsolete.</span></span> <span data-ttu-id="556de-120">Строка `"Will be removed in next version"` передается атрибуту.</span><span class="sxs-lookup"><span data-stu-id="556de-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="556de-121">Атрибут вызывает предупреждение компилятора, которое отображает переданную строку при вызове кода, описываемого этим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="556de-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a><span data-ttu-id="556de-122">Применение атрибутов на уровне сборки</span><span class="sxs-lookup"><span data-stu-id="556de-122">Apply attributes at the assembly level</span></span>

 <span data-ttu-id="556de-123">Если необходимо применять атрибут на уровне сборки, используйте ключевое слово `assembly` (`Assembly` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="556de-123">If you want to apply an attribute at the assembly level, use the `assembly` (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="556de-124">В следующем коде показан атрибут **AssemblyTitleAttribute** , применяемый на уровне сборки.</span><span class="sxs-lookup"><span data-stu-id="556de-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 <span data-ttu-id="556de-125">Если атрибут применяется, строка `"My Assembly"` помещается в манифест сборки в раздел метаданных файла.</span><span class="sxs-lookup"><span data-stu-id="556de-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="556de-126">Для просмотра атрибута можно воспользоваться [дизассемблером MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) или создать пользовательскую программу для извлечения атрибута.</span><span class="sxs-lookup"><span data-stu-id="556de-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="556de-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="556de-127">See also</span></span>

- [<span data-ttu-id="556de-128">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="556de-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="556de-129">Извлечение информации, сохраненной в атрибуте</span><span class="sxs-lookup"><span data-stu-id="556de-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="556de-130">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="556de-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="556de-131">Атрибуты (C#)</span><span class="sxs-lookup"><span data-stu-id="556de-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="556de-132">Общие сведения об атрибутах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="556de-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
