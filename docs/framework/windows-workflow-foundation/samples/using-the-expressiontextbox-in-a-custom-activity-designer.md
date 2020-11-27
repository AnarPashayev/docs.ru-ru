---
title: Использование ExpressionTextBox в пользовательском конструкторе действия
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: dfb53096be59abd9924a024880d4125ca774d4b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267498"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="2e4e2-102">Использование ExpressionTextBox в пользовательском конструкторе действия</span><span class="sxs-lookup"><span data-stu-id="2e4e2-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>

<span data-ttu-id="2e4e2-103">В этом образце показано, как использовать <xref:System.Activities.Presentation.View.ExpressionTextBox> в настраиваемом конструкторе действий.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="2e4e2-104">Пользовательское действие `MultiAssign` присваивает два строковых значения двум строковым переменным.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="2e4e2-105">Некоторые элементы управления <xref:System.Activities.Presentation.View.ExpressionTextBox> привязываются к аргументу <xref:System.Activities.InArgument>, а некоторые - к аргументу <xref:System.Activities.OutArgument>.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2e4e2-106">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="2e4e2-106">Sample details</span></span>

 <span data-ttu-id="2e4e2-107">`ArgumentToExpressionConverter` - это преобразователь типов, используемый для привязки выражений к аргументам.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="2e4e2-108">Параметр `ConverterParameter` необходимо установить в соответствующее значение `In` или `Out`.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="2e4e2-109">Тип `InOut` не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="2e4e2-110">`UseLocationExpression`Атрибут используется в параметре `OutArgument` s, чтобы указать, что выражение должно быть выражением L-value ("левое значение" или "значение расположения").</span><span class="sxs-lookup"><span data-stu-id="2e4e2-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="2e4e2-111">В большинстве случаев левостороннее выражение является допустимым идентификатором Visual Basic, используемым для указания того, что возвращаемый аргумент `OutArgument` является переменной или именем аргумента.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="2e4e2-112">В этом примере для атрибута `MaxLines` установлено значение 1, а значение атрибута `MinLines` не задано.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="2e4e2-113">Это указывает, что текстовое поле <xref:System.Activities.Presentation.View.ExpressionTextBox> имеет фиксированный размер в одну строку независимо от объема текста, введенного пользователем.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="2e4e2-114">Чтобы разрешить изменение размера текстового поля <xref:System.Activities.Presentation.View.ExpressionTextBox> в соответствии с объемом вводимых пользователем данных, задайте значение `MaxLines`, которое больше значения `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="2e4e2-115">Текстовое поле ExpressionTextBox может быть привязано только к аргументам и не может быть привязано к свойствам CLR.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="2e4e2-116">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="2e4e2-116">To use this sample</span></span>

1. <span data-ttu-id="2e4e2-117">С помощью Visual Studio 2010 откройте файл Експрессионтекстбокссампле. sln.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="2e4e2-118">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="2e4e2-119">Запуск образца</span><span class="sxs-lookup"><span data-stu-id="2e4e2-119">To run this sample</span></span>

1. <span data-ttu-id="2e4e2-120">Добавьте в решение новое консольное приложение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="2e4e2-121">Добавьте ссылку на проект **експрессионтекстбокссампле** из нового проекта консольного приложения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="2e4e2-122">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-122">Build the solution.</span></span>

4. <span data-ttu-id="2e4e2-123">Перетащите действие " **Многоназначение** " из области элементов в рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e4e2-124">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e4e2-125">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2e4e2-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2e4e2-126">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e4e2-127">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="2e4e2-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="2e4e2-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2e4e2-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="2e4e2-129">Разработка приложений с помощью конструктора рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="2e4e2-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
