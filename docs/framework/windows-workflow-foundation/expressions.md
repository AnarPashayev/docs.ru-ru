---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 047f0f5d0214926fde2fe21efd9a24c4b645ed8e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380168"
---
# <a name="expressions"></a><span data-ttu-id="77d7a-102">Выражения</span><span class="sxs-lookup"><span data-stu-id="77d7a-102">Expressions</span></span>
<span data-ttu-id="77d7a-103">Выражение Windows Workflow Foundation (WF) — любое действие, которое возвращает результат.</span><span class="sxs-lookup"><span data-stu-id="77d7a-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="77d7a-104">Все действия выражений косвенно наследуются от класса <xref:System.Activities.Activity%601>, который содержит свойство <xref:System.Activities.OutArgument> с именем <xref:System.Activities.Activity%601.Result%2A> в качестве значения, возвращаемого действием.</span><span class="sxs-lookup"><span data-stu-id="77d7a-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="77d7a-105">поставляется с множеством действий выражений от таких простых, как <xref:System.Activities.Expressions.VariableValue%601> и <xref:System.Activities.Expressions.VariableReference%601>, для доступа к одной переменной рабочего процесса с помощью действий оператора до таких сложных, как <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> и <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>, которые обеспечивают доступ ко всем возможностям языка Visual Basic для получения результата.</span><span class="sxs-lookup"><span data-stu-id="77d7a-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="77d7a-106">Дополнительные действия выражения можно создать путем наследования от <xref:System.Activities.CodeActivity%601> или <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="77d7a-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="77d7a-107">Использование выражений</span><span class="sxs-lookup"><span data-stu-id="77d7a-107">Using Expressions</span></span>  
 <span data-ttu-id="77d7a-108">Конструктор рабочих процессов использует <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> и <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> для всех выражений в проектах Visual Basic <xref:Microsoft.CSharp.Activities.CSharpValue%601> и <xref:Microsoft.CSharp.Activities.CSharpReference%601> для выражений C# в проектах рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="77d7a-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77d7a-109">Поддержка C# выражения в проекты рабочих процессов появилась в .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="77d7a-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="77d7a-110">Дополнительные сведения см. в разделе [ C# выражения](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="77d7a-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="77d7a-111">Рабочие процессы, которые создаются конструктором, сохраняются в XAML, в котором выражения отображаются в квадратных скобках, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="77d7a-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 <span data-ttu-id="77d7a-112">При определении рабочего процесса в коде можно использовать любое действие выражения.</span><span class="sxs-lookup"><span data-stu-id="77d7a-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="77d7a-113">В следующем примере показано использование способа создания действий оператора для сложения трех чисел.</span><span class="sxs-lookup"><span data-stu-id="77d7a-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 <span data-ttu-id="77d7a-114">Этот же рабочий процесс может быть выражен более компактно с помощью лямбда-выражений C#, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="77d7a-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="77d7a-115">Также рабочий процесс можно выразить с помощью действий выражений Visual Basic, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="77d7a-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="77d7a-116">Расширение доступных выражений с помощью настраиваемых действий выражения</span><span class="sxs-lookup"><span data-stu-id="77d7a-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="77d7a-117">Выражения в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] можно расширить, что позволит создавать дополнительные действия выражения.</span><span class="sxs-lookup"><span data-stu-id="77d7a-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="77d7a-118">В следующем примере показано действие, которое возвращает сумму трех целочисленных значений.</span><span class="sxs-lookup"><span data-stu-id="77d7a-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="77d7a-119">С помощью этого нового действия можно переписать предыдущий рабочий процесс, в котором складывались три значения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="77d7a-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 <span data-ttu-id="77d7a-120">Дополнительные сведения об использовании выражений в коде, см. в разделе [создание рабочих процессов, действий и выражений с помощью императивного кода](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="77d7a-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
