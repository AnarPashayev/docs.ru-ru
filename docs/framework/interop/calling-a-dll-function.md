---
title: Вызов функции DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051886"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="63f0f-102">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="63f0f-102">Calling a DLL Function</span></span>
<span data-ttu-id="63f0f-103">Хотя вызов неуправляемых функций DLL почти идентичен вызову другого управляемого кода, все же существуют отличия, которые поначалу могут вызвать некоторые сложности в освоении функций DLL.</span><span class="sxs-lookup"><span data-stu-id="63f0f-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="63f0f-104">В этом разделе представлены статьи, касающиеся некоторых особенностей вызовов.</span><span class="sxs-lookup"><span data-stu-id="63f0f-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="63f0f-105">Структуры, возвращаемые из вызовов неуправляемого кода, должны быть типами данных, имеющими одинаковые представления в управляемом и неуправляемом коде.</span><span class="sxs-lookup"><span data-stu-id="63f0f-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="63f0f-106">Такие типы называются *непреобразуемыми типами*, так как они не требуют преобразования (см. раздел [Непреобразуемые и преобразуемые типы](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="63f0f-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="63f0f-107">Чтобы вызвать функцию с преобразуемой структурой в качестве ее возвращаемого типа, можно определить непреобразуемый вспомогательный тип того же размера, что и преобразуемый тип, и преобразовать данные после возвращения функции.</span><span class="sxs-lookup"><span data-stu-id="63f0f-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63f0f-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="63f0f-108">In This Section</span></span>  
 [<span data-ttu-id="63f0f-109">Передача структур</span><span class="sxs-lookup"><span data-stu-id="63f0f-109">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="63f0f-110">Описываются вопросы передачи структур данных с предопределенной компоновкой.</span><span class="sxs-lookup"><span data-stu-id="63f0f-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="63f0f-111">Функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="63f0f-111">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="63f0f-112">Основные сведения о функциях обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="63f0f-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="63f0f-113">Практическое руководство. Реализация функций обратного вызова</span><span class="sxs-lookup"><span data-stu-id="63f0f-113">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="63f0f-114">Описывается реализация функций обратного вызова в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="63f0f-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="63f0f-115">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="63f0f-115">Related Sections</span></span>  
 [<span data-ttu-id="63f0f-116">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="63f0f-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="63f0f-117">Описывает способ вызова неуправляемых функций DLL с помощью вызова платформы.</span><span class="sxs-lookup"><span data-stu-id="63f0f-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="63f0f-118">Маршалинг данных при вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="63f0f-118">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="63f0f-119">Описывается способ объявления параметров метода и передачи аргументов в функции, экспортируемые неуправляемыми библиотеками.</span><span class="sxs-lookup"><span data-stu-id="63f0f-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
