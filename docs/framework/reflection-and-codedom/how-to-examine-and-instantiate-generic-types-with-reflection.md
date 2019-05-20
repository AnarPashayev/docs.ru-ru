---
title: Практическое руководство. Изучение универсальных типов и создание их экземпляров при помощи отражения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41070b5d51f0b613d7a6bbbc72b24a8c1793964d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586113"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="f846f-102">Практическое руководство. Изучение универсальных типов и создание их экземпляров при помощи отражения</span><span class="sxs-lookup"><span data-stu-id="f846f-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="f846f-103">Сведения об универсальных типах получаются аналогично сведениям о других типах: путем изучения объекта <xref:System.Type>, который представляет универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="f846f-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="f846f-104">Принципиальная разница заключается в том, что универсальный тип имеет список объектов <xref:System.Type>, представляющих его параметры универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="f846f-105">В первой процедуре данного раздела изучаются универсальные типы.</span><span class="sxs-lookup"><span data-stu-id="f846f-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="f846f-106">Можно создать объект <xref:System.Type>, представляющий сконструированный тип, путем привязки аргументов типа к параметрам типа определения универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="f846f-107">Это демонстрируется во второй процедуре.</span><span class="sxs-lookup"><span data-stu-id="f846f-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="f846f-108">Изучение универсального типа и его параметров типа</span><span class="sxs-lookup"><span data-stu-id="f846f-108">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="f846f-109">Получите экземпляр класса <xref:System.Type>, который представляет этот универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="f846f-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="f846f-110">В следующем коде этот тип получается с помощью оператора C# `typeof` (`GetType` в Visual Basic, `typeid` в Visual C++).</span><span class="sxs-lookup"><span data-stu-id="f846f-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="f846f-111">Другие способы получения объекта <xref:System.Type> см. в теме, посвященной объекту <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f846f-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="f846f-112">Обратите внимание, что в оставшейся части этой процедуры этот тип содержится в параметре метода с именем `t`.</span><span class="sxs-lookup"><span data-stu-id="f846f-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="f846f-113">Для определения того, является ли тип универсальным, используется свойство <xref:System.Type.IsGenericType%2A>, а для определения того, является ли тип определением универсального типа, свойство <xref:System.Type.IsGenericTypeDefinition%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="f846f-114">Получите массив, содержащий аргументы универсального типа, с использованием метода <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="f846f-115">Для каждого аргумента типа следует определить, является ли он параметром типа (например, в определении универсального типа) или типом, который был задан для параметра типа (например, в сконструированном типе) с использованием свойства <xref:System.Type.IsGenericParameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="f846f-116">В системе типов параметр универсального типа представлен экземпляром класса <xref:System.Type>, как обычные типы.</span><span class="sxs-lookup"><span data-stu-id="f846f-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="f846f-117">В следующем примере показано имя и расположение параметра для объекта <xref:System.Type>, который представляет параметр универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="f846f-118">В этом примере определить положение параметра не представляет труда; эти сведения более важны при изучении параметра типа, который используется в качестве аргумента типа для другого универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="f846f-119">Определите ограничение базового типа и ограничения интерфейса параметра универсального типа с использованием метода <xref:System.Type.GetGenericParameterConstraints%2A>, чтобы получить все ограничения в одном массиве.</span><span class="sxs-lookup"><span data-stu-id="f846f-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="f846f-120">Расположение ограничений в конкретном порядке не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="f846f-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="f846f-121">При помощи свойства <xref:System.Type.GenericParameterAttributes%2A> выявите особые ограничения для параметра типа, например требования, чтобы он являлся ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="f846f-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="f846f-122">Это свойство содержит значения, представляющие расхождение, которое можно замаскировать, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="f846f-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="f846f-123">Атрибуты особого ограничения являются флагами, флаг (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), который не представляет особые ограничения, также не представляет ковариацию или контрвариацию.</span><span class="sxs-lookup"><span data-stu-id="f846f-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="f846f-124">Таким образом, для проверки любого из этих условий необходимо использовать подходящую маску.</span><span class="sxs-lookup"><span data-stu-id="f846f-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="f846f-125">В этом случае следует использовать свойство <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> для изоляции флагов особых ограничений.</span><span class="sxs-lookup"><span data-stu-id="f846f-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="f846f-126">Конструирование экземпляра универсального типа</span><span class="sxs-lookup"><span data-stu-id="f846f-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="f846f-127">Универсальный тип напоминает шаблон.</span><span class="sxs-lookup"><span data-stu-id="f846f-127">A generic type is like a template.</span></span> <span data-ttu-id="f846f-128">Нельзя создать его экземпляры, если не указаны фактические типы для его параметров универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="f846f-129">Чтобы сделать это во время выполнения с использованием отражения, необходимо использовать метод <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="f846f-130">Конструирование экземпляра универсального типа</span><span class="sxs-lookup"><span data-stu-id="f846f-130">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="f846f-131">Получите объект <xref:System.Type>, который представляет универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="f846f-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="f846f-132">В следующем примере получается универсальный тип <xref:System.Collections.Generic.Dictionary%602> двумя разными способами: с использованием перегруженной версии метода <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> со строкой, описывающей этот тип, а также путем вызова метода <xref:System.Type.GetGenericTypeDefinition%2A> для сконструированного типа `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f846f-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="f846f-133">Для метода <xref:System.Type.MakeGenericType%2A> требуется определение универсального типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="f846f-134">Создайте массив аргументов типа, на который будут заменены параметры типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="f846f-135">Этот массив должен содержать правильное количество объектов <xref:System.Type> в том же порядке, в котором они отображаются в списке параметров типа.</span><span class="sxs-lookup"><span data-stu-id="f846f-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="f846f-136">В этом случае ключ (первый параметр типа) имеет тип <xref:System.String>, а значения в словаре являются экземплярами класса с именем `Example`.</span><span class="sxs-lookup"><span data-stu-id="f846f-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="f846f-137">Вызовите метод <xref:System.Type.MakeGenericType%2A>, чтобы привязать аргументы типа к параметрам типа и сконструировать тип.</span><span class="sxs-lookup"><span data-stu-id="f846f-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="f846f-138">Для создания объекта сконструированного типа используется перегруженная версия метода <xref:System.Activator.CreateInstance%28System.Type%29>.</span><span class="sxs-lookup"><span data-stu-id="f846f-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="f846f-139">В следующем примере кода два экземпляра класса `Example` сохраняются в итоговом объекте `Dictionary<String, Example>`.</span><span class="sxs-lookup"><span data-stu-id="f846f-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="f846f-140">Пример</span><span class="sxs-lookup"><span data-stu-id="f846f-140">Example</span></span>  
 <span data-ttu-id="f846f-141">В следующем примере кода определяется метод `DisplayGenericType` для изучения определений универсальных типов и сконструированных типов, используемых в коде, и вывода сведений о них.</span><span class="sxs-lookup"><span data-stu-id="f846f-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="f846f-142">Метод `DisplayGenericType` показывает, как использовать свойства <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> и <xref:System.Type.GenericParameterPosition%2A>, а также метод <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="f846f-143">В этом примере также определяется метод `DisplayGenericParameter` для изучения параметра универсального типа и вывода его ограничений.</span><span class="sxs-lookup"><span data-stu-id="f846f-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="f846f-144">В этом примере кода определяется набор тестовых типов, включая универсальный тип, который иллюстрирует ограничения параметра типа, и демонстрируется, как вывести сведения об этих типах.</span><span class="sxs-lookup"><span data-stu-id="f846f-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="f846f-145">В примере создается тип на основе класса <xref:System.Collections.Generic.Dictionary%602> путем создания массива аргументов типа и вызова метода <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f846f-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="f846f-146">Программа сравнивает объект <xref:System.Type>, сконструированный с использованием метода <xref:System.Type.MakeGenericType%2A>, с объектом <xref:System.Type>, полученным с использованием оператора `typeof` (`GetType` в Visual Basic), показывая, что эти объекты одинаковы.</span><span class="sxs-lookup"><span data-stu-id="f846f-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="f846f-147">Аналогичным образом программа получает определение универсального типа для сконструированного типа при помощи метода <xref:System.Type.GetGenericTypeDefinition%2A> и сравнивает его с объектом <xref:System.Type>, представляющим класс <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="f846f-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f846f-148">См. также</span><span class="sxs-lookup"><span data-stu-id="f846f-148">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="f846f-149">Отражение и универсальные типы</span><span class="sxs-lookup"><span data-stu-id="f846f-149">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [<span data-ttu-id="f846f-150">Просмотр сведений о типах</span><span class="sxs-lookup"><span data-stu-id="f846f-150">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="f846f-151">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="f846f-151">Generics</span></span>](../../../docs/standard/generics/index.md)
