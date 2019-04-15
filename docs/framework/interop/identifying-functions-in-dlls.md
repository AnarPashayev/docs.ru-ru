---
title: Идентификация функций в библиотеках DLL
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca01234bf7adaca1337053bbc2bbba0731be3cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132045"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="c39f2-102">Идентификация функций в библиотеках DLL</span><span class="sxs-lookup"><span data-stu-id="c39f2-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="c39f2-103">Идентификатор функции DLL состоит из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="c39f2-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="c39f2-104">Имя функции или порядковый номер</span><span class="sxs-lookup"><span data-stu-id="c39f2-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="c39f2-105">Имя файла DLL, в котором находится реализация</span><span class="sxs-lookup"><span data-stu-id="c39f2-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="c39f2-106">Например, при указании функции **MessageBox** в библиотеке User32.dll определяется функция (**MessageBox**) и ее расположение (User32.dll, User32 или user32).</span><span class="sxs-lookup"><span data-stu-id="c39f2-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="c39f2-107">Программный интерфейс Microsoft Windows (API Windows) может содержать две версии для каждой функции, обрабатывающей символы и строки: версию ANSI для однобайтовых символов и версию Юникода для двухбайтовых символов.</span><span class="sxs-lookup"><span data-stu-id="c39f2-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="c39f2-108">Если кодировка не указана, она определяется полем <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> (по умолчанию ANSI).</span><span class="sxs-lookup"><span data-stu-id="c39f2-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="c39f2-109">Некоторые функции могут иметь более двух версий.</span><span class="sxs-lookup"><span data-stu-id="c39f2-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="c39f2-110">**MessageBoxA** — это точка входа ANSI для функции **MessageBox**; **MessageBoxW** — версия для Юникода.</span><span class="sxs-lookup"><span data-stu-id="c39f2-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="c39f2-111">Чтобы получить список имен функций в конкретной библиотеке DLL, например user32.dll, можно воспользоваться различными средствами командной строки.</span><span class="sxs-lookup"><span data-stu-id="c39f2-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="c39f2-112">Например, для получения имен функций можно воспользоваться `dumpbin /exports user32.dll` или `link /dump /exports user32.dll`.</span><span class="sxs-lookup"><span data-stu-id="c39f2-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="c39f2-113">Неуправляемую функцию в коде можно переименовать, при условии что новое имя функции соответствует исходной точке входа в библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="c39f2-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="c39f2-114">Инструкции по переименованию неуправляемой функции DLL в управляемом исходном коде см. в разделе [Указание точки входа](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="c39f2-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="c39f2-115">Вызов неуправляемого кода позволяет управлять значительной частью операционной системы с помощью вызова функций в API Windows и других библиотеках DLL.</span><span class="sxs-lookup"><span data-stu-id="c39f2-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="c39f2-116">Наряду с API Windows существует несколько других API и библиотек DLL, для которых доступен вызов неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="c39f2-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="c39f2-117">В следующей таблице описаны несколько распространенных библиотек DLL в API Windows.</span><span class="sxs-lookup"><span data-stu-id="c39f2-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="c39f2-118">DLL</span><span class="sxs-lookup"><span data-stu-id="c39f2-118">DLL</span></span>|<span data-ttu-id="c39f2-119">Описание содержимого</span><span class="sxs-lookup"><span data-stu-id="c39f2-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="c39f2-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="c39f2-120">GDI32.dll</span></span>|<span data-ttu-id="c39f2-121">Функции интерфейса графических устройств (GDI) для вывода информации на устройство, например функции для рисования и управления шрифтами.</span><span class="sxs-lookup"><span data-stu-id="c39f2-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="c39f2-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c39f2-122">Kernel32.dll</span></span>|<span data-ttu-id="c39f2-123">Низкоуровневые функции операционной системы для управления памятью и обработки ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c39f2-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="c39f2-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="c39f2-124">User32.dll</span></span>|<span data-ttu-id="c39f2-125">Функции управления Windows для обработки сообщений, таймеров, меню и обмена данными.</span><span class="sxs-lookup"><span data-stu-id="c39f2-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="c39f2-126">Полную документацию по API Windows см. в разделе "Пакет SDK платформы".</span><span class="sxs-lookup"><span data-stu-id="c39f2-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="c39f2-127">Примеры, демонстрирующие создание объявлений на основе .NET, которые используются с вызовом неуправляемого кода, см. в разделе [Маршалинг данных при вызове неуправляемого кода](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c39f2-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39f2-128">См. также</span><span class="sxs-lookup"><span data-stu-id="c39f2-128">See also</span></span>

- [<span data-ttu-id="c39f2-129">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="c39f2-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="c39f2-130">Задание точки входа</span><span class="sxs-lookup"><span data-stu-id="c39f2-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)
- [<span data-ttu-id="c39f2-131">Создание класса, содержащего функции DLL</span><span class="sxs-lookup"><span data-stu-id="c39f2-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="c39f2-132">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="c39f2-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="c39f2-133">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="c39f2-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
