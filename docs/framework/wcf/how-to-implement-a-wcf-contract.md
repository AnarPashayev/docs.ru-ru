---
title: Учебник. Реализация контракта службы Windows Communication Foundation
description: Узнайте, как добавить код для реализации интерфейса службы WCF в составе серии статей, которые помогут приступить к созданию приложения WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244651"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="bea5d-103">Учебник. Реализация контракта службы Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bea5d-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="bea5d-104">В этом руководстве описывается вторая из пяти задач, необходимых для создания приложения Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bea5d-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="bea5d-105">Общие сведения о учебниках см. в разделе [учебник. Начало работы с Windows Communication Foundation приложениями](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="bea5d-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="bea5d-106">Следующим шагом для создания приложения WCF является добавление кода для реализации интерфейса службы WCF, созданного на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="bea5d-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="bea5d-107">На этом шаге вы создадите класс с именем `CalculatorService` , который реализует определяемый пользователем `ICalculator` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="bea5d-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="bea5d-108">Каждый метод в следующем коде вызывает операцию калькулятора и выводит текст на консоль для его тестирования.</span><span class="sxs-lookup"><span data-stu-id="bea5d-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="bea5d-109">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="bea5d-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bea5d-110">Добавьте код для реализации контракта службы WCF.</span><span class="sxs-lookup"><span data-stu-id="bea5d-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="bea5d-111">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="bea5d-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="bea5d-112">Добавление кода для реализации контракта службы WCF</span><span class="sxs-lookup"><span data-stu-id="bea5d-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="bea5d-113">В **жеттингстартедлиб**откройте файл **Service1.CS** или **Service1. vb** и замените его код следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="bea5d-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a><span data-ttu-id="bea5d-114">Изменить App.config</span><span class="sxs-lookup"><span data-stu-id="bea5d-114">Edit App.config</span></span>

<span data-ttu-id="bea5d-115">Измените **App.config** в **жеттингстартедлиб** , чтобы отразить изменения, внесенные в код.</span><span class="sxs-lookup"><span data-stu-id="bea5d-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="bea5d-116">Для проектов Visual C#:</span><span class="sxs-lookup"><span data-stu-id="bea5d-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="bea5d-117">Измените строку 14 на`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="bea5d-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="bea5d-118">Изменить строку 17 на`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="bea5d-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="bea5d-119">Измените строку 22 на`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="bea5d-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="bea5d-120">Для проектов Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="bea5d-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="bea5d-121">Измените строку 14 на`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="bea5d-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="bea5d-122">Изменить строку 17 на`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="bea5d-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="bea5d-123">Измените строку 22 на`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="bea5d-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="bea5d-124">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="bea5d-124">Compile the code</span></span>

<span data-ttu-id="bea5d-125">Постройте решение, чтобы убедиться в отсутствии ошибок компиляции.</span><span class="sxs-lookup"><span data-stu-id="bea5d-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="bea5d-126">Если вы используете Visual Studio, в меню **Сборка** выберите пункт **построить решение** (или нажмите клавиши **CTRL** + **SHIFT** + **B**).</span><span class="sxs-lookup"><span data-stu-id="bea5d-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bea5d-127">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="bea5d-127">Next steps</span></span>

<span data-ttu-id="bea5d-128">В этом руководстве вы узнали, как выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="bea5d-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bea5d-129">Добавьте код для реализации контракта службы WCF.</span><span class="sxs-lookup"><span data-stu-id="bea5d-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="bea5d-130">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="bea5d-130">Build the solution.</span></span>

<span data-ttu-id="bea5d-131">Перейдите к следующему руководству, чтобы узнать, как запустить службу WCF.</span><span class="sxs-lookup"><span data-stu-id="bea5d-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bea5d-132">Учебник. размещение и запуск базовой службы WCF</span><span class="sxs-lookup"><span data-stu-id="bea5d-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
