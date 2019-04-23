---
title: Отладка деревьев выражений в Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330416"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="2c20f-102">Отладка деревьев выражений в Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="2c20f-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="2c20f-103">При отладке приложений можно анализировать структуру и содержимое деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="2c20f-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="2c20f-104">Чтобы получить краткий обзор структуры дерева выражения, можно использовать свойство `DebugView`, которое доступно только в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="2c20f-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="2c20f-105">Дополнительные сведения об отладке см. в разделе [Отладка в Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2c20f-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="2c20f-106">Для оптимизации представления содержимого деревьев выражений свойство `DebugView` использует визуализаторы Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c20f-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="2c20f-107">Дополнительные сведения см. в статье, посвященной [созданию пользовательских визуализаторов](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="2c20f-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="2c20f-108">Открытие визуализатора дерева выражения</span><span class="sxs-lookup"><span data-stu-id="2c20f-108">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="2c20f-109">Щелкните значок лупы рядом с именем свойства `DebugView` дерева выражения в окне **Советы**, **Контрольные значения**, **Видимые** или **Локальные**.</span><span class="sxs-lookup"><span data-stu-id="2c20f-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="2c20f-110">Откроется список визуализаторов.</span><span class="sxs-lookup"><span data-stu-id="2c20f-110">A list of visualizers is displayed.</span></span>  
  
2. <span data-ttu-id="2c20f-111">Щелкните визуализатор, который необходимо использовать.</span><span class="sxs-lookup"><span data-stu-id="2c20f-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="2c20f-112">Каждый тип выражения отображается в визуализаторе, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="2c20f-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="2c20f-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="2c20f-113">ParameterExpressions</span></span>  
 <span data-ttu-id="2c20f-114">В начале имен переменных <xref:System.Linq.Expressions.ParameterExpression> отображается символ "$".</span><span class="sxs-lookup"><span data-stu-id="2c20f-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="2c20f-115">Если параметр не имеет имени, оно назначается автоматически, например `$var1` или `$var2`.</span><span class="sxs-lookup"><span data-stu-id="2c20f-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="2c20f-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-116">Examples</span></span>  
  
|<span data-ttu-id="2c20f-117">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-117">Expression</span></span>|<span data-ttu-id="2c20f-118">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="2c20f-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="2c20f-119">ConstantExpressions</span></span>  
 <span data-ttu-id="2c20f-120">Для объектов <xref:System.Linq.Expressions.ConstantExpression>, представляющих целочисленные значения, строки и `null`, отображается значение константы.</span><span class="sxs-lookup"><span data-stu-id="2c20f-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="2c20f-121">Для числовых типов, имеющих стандартные суффиксы, такие как литералы C#, суффикс добавляется к значению.</span><span class="sxs-lookup"><span data-stu-id="2c20f-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="2c20f-122">В следующей таблице показаны суффиксы для различных числовых типов.</span><span class="sxs-lookup"><span data-stu-id="2c20f-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="2c20f-123">Тип</span><span class="sxs-lookup"><span data-stu-id="2c20f-123">Type</span></span>|<span data-ttu-id="2c20f-124">Суффикс</span><span class="sxs-lookup"><span data-stu-id="2c20f-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="2c20f-125">U</span><span class="sxs-lookup"><span data-stu-id="2c20f-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="2c20f-126">L</span><span class="sxs-lookup"><span data-stu-id="2c20f-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="2c20f-127">UL</span><span class="sxs-lookup"><span data-stu-id="2c20f-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="2c20f-128">D</span><span class="sxs-lookup"><span data-stu-id="2c20f-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="2c20f-129">C</span><span class="sxs-lookup"><span data-stu-id="2c20f-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="2c20f-130">M</span><span class="sxs-lookup"><span data-stu-id="2c20f-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="2c20f-131">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-131">Examples</span></span>  
  
|<span data-ttu-id="2c20f-132">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-132">Expression</span></span>|<span data-ttu-id="2c20f-133">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="2c20f-134">10</span><span class="sxs-lookup"><span data-stu-id="2c20f-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="2c20f-135">10D</span><span class="sxs-lookup"><span data-stu-id="2c20f-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="2c20f-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="2c20f-136">BlockExpression</span></span>  
 <span data-ttu-id="2c20f-137">Если тип объекта <xref:System.Linq.Expressions.BlockExpression> отличается от типа последнего выражения в блоке, то тип отображается в свойстве `DebugInfo` в угловых скобках (\< и >).</span><span class="sxs-lookup"><span data-stu-id="2c20f-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="2c20f-138">В противном случае тип объекта <xref:System.Linq.Expressions.BlockExpression> не отображается.</span><span class="sxs-lookup"><span data-stu-id="2c20f-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="2c20f-139">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-139">Examples</span></span>  
  
|<span data-ttu-id="2c20f-140">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-140">Expression</span></span>|<span data-ttu-id="2c20f-141">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="2c20f-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="2c20f-142">LambdaExpression</span></span>  
 <span data-ttu-id="2c20f-143">Объекты <xref:System.Linq.Expressions.LambdaExpression> отображаются вместе со своими типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="2c20f-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="2c20f-144">Если лямбда-выражение не имеет имени, оно назначается автоматически, например `#Lambda1` или `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="2c20f-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="2c20f-145">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-145">Examples</span></span>  
  
|<span data-ttu-id="2c20f-146">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-146">Expression</span></span>|<span data-ttu-id="2c20f-147">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="2c20f-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="2c20f-148">LabelExpression</span></span>  
 <span data-ttu-id="2c20f-149">Если указать значение по умолчанию для объекта <xref:System.Linq.Expressions.LabelExpression>, оно будет отображаться перед объектом <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="2c20f-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="2c20f-150">Маркер `.Label` указывает начало метки.</span><span class="sxs-lookup"><span data-stu-id="2c20f-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="2c20f-151">Маркер `.LabelTarget` задает конечную цель перехода для целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="2c20f-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="2c20f-152">Если метка не имеет имени, оно назначается автоматически, например `#Label1` или `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="2c20f-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="2c20f-153">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-153">Examples</span></span>  
  
|<span data-ttu-id="2c20f-154">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-154">Expression</span></span>|<span data-ttu-id="2c20f-155">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="2c20f-156">Проверяемые операторы</span><span class="sxs-lookup"><span data-stu-id="2c20f-156">Checked Operators</span></span>  
 <span data-ttu-id="2c20f-157">Проверяемые операторы отображаются с символом # перед оператором.</span><span class="sxs-lookup"><span data-stu-id="2c20f-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="2c20f-158">Например, проверяемый оператор сложения отображается как `#+`.</span><span class="sxs-lookup"><span data-stu-id="2c20f-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="2c20f-159">Примеры</span><span class="sxs-lookup"><span data-stu-id="2c20f-159">Examples</span></span>  
  
|<span data-ttu-id="2c20f-160">Выражение</span><span class="sxs-lookup"><span data-stu-id="2c20f-160">Expression</span></span>|<span data-ttu-id="2c20f-161">Свойство`DebugView` </span><span class="sxs-lookup"><span data-stu-id="2c20f-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="2c20f-162">См. также</span><span class="sxs-lookup"><span data-stu-id="2c20f-162">See also</span></span>

- <span data-ttu-id="2c20f-163">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) (Деревья выражений (C#))</span><span class="sxs-lookup"><span data-stu-id="2c20f-163">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)</span></span>
- [<span data-ttu-id="2c20f-164">Отладка в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c20f-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="2c20f-165">Создание настраиваемых визуализаторов</span><span class="sxs-lookup"><span data-stu-id="2c20f-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
