---
title: Создание класса, содержащего функции DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b204eacd43db2c562fbe6d519b5fa91df3466cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626414"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="f3835-102">Создание класса, содержащего функции DLL</span><span class="sxs-lookup"><span data-stu-id="f3835-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="f3835-103">Упаковка часто используемых функций DLL в управляемый класс позволяет эффективно инкапсулировать функциональные возможности платформы.</span><span class="sxs-lookup"><span data-stu-id="f3835-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="f3835-104">Делать это в каждом случае необязательно, однако использование оболочки класса удобно, поскольку определение функций DLL может быть затруднительно и нередко приводит к ошибкам.</span><span class="sxs-lookup"><span data-stu-id="f3835-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="f3835-105">При программировании на языке Visual Basic или C# необходимо объявлять функции DLL в классе или модуле Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3835-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="f3835-106">В классе определяется статический метод для каждой функции DLL, которую требуется вызывать.</span><span class="sxs-lookup"><span data-stu-id="f3835-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="f3835-107">Определение может включать дополнительные сведения, в том числе кодировку или соглашение о вызовах, используемые при передаче аргументов метода. Если эти сведения не указаны, используются параметры по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f3835-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="f3835-108">Полный список параметров объявления и их значений по умолчанию см. в разделе [Создание прототипов в управляемом коде](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3835-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="f3835-109">После упаковки вы можете вызывать методы для этого класса так же, как и статические методы для любого другого класса.</span><span class="sxs-lookup"><span data-stu-id="f3835-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="f3835-110">При вызове неуправляемого кода базовая экспортированная функция обрабатывается автоматически.</span><span class="sxs-lookup"><span data-stu-id="f3835-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="f3835-111">При разработке управляемого класса для вызова неуправляемого кода следует учитывать отношения между классами и функциями DLL.</span><span class="sxs-lookup"><span data-stu-id="f3835-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="f3835-112">Например, с их помощью можно выполнять следующее.</span><span class="sxs-lookup"><span data-stu-id="f3835-112">For example, you can:</span></span>  
  
- <span data-ttu-id="f3835-113">Объявлять функции DLL в существующем классе.</span><span class="sxs-lookup"><span data-stu-id="f3835-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="f3835-114">Создавать отдельный класс для каждой функции DLL, обеспечивая изоляцию и удобство поиска функций.</span><span class="sxs-lookup"><span data-stu-id="f3835-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="f3835-115">Создавать один класс для набора связанных функций DLL, что позволяет упорядочивать их по логическим группам и снизить затраты на ресурсы.</span><span class="sxs-lookup"><span data-stu-id="f3835-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="f3835-116">Имена класса и его методов могут быть произвольными.</span><span class="sxs-lookup"><span data-stu-id="f3835-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="f3835-117">Примеры, демонстрирующие создание объявлений на основе .NET, которые используются с вызовом неуправляемого кода, см. в разделе [Маршалинг данных при вызове неуправляемого кода](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f3835-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3835-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f3835-118">See also</span></span>

- [<span data-ttu-id="f3835-119">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="f3835-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="f3835-120">Идентификация функций в библиотеках DLL</span><span class="sxs-lookup"><span data-stu-id="f3835-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="f3835-121">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="f3835-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f3835-122">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="f3835-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
