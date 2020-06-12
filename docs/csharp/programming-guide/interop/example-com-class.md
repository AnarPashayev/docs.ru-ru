---
title: Руководство по программированию на C#. Пример COM-класса
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6051ff91d13a3cb3ca6229d813db34dd6a9f3af6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241855"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="14070-102">Пример COM-класса (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="14070-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="14070-103">Далее приведен пример класса, который можно предоставить в качестве COM-объекта.</span><span class="sxs-lookup"><span data-stu-id="14070-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="14070-104">После помещения этого кода в CS-файл и добавления в проект свойства **Регистрация для COM-взаимодействия** необходимо присвоить значение **Истина**.</span><span class="sxs-lookup"><span data-stu-id="14070-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="14070-105">Дополнительные сведения см. в разделе [Практическое руководство. Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)) (Практическое руководство. Регистрация компонента для COM-взаимодействия).</span><span class="sxs-lookup"><span data-stu-id="14070-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="14070-106">Предоставление объектов Visual C# для COM требует объявления интерфейса класса, интерфейса событий (если необходимо) и самого класса.</span><span class="sxs-lookup"><span data-stu-id="14070-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="14070-107">Члены класса должны соответствовать указанным ниже правилам, чтобы стать доступными для COM.</span><span class="sxs-lookup"><span data-stu-id="14070-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="14070-108">Класс должен быть открытым.</span><span class="sxs-lookup"><span data-stu-id="14070-108">The class must be public.</span></span>  
  
- <span data-ttu-id="14070-109">Свойства, методы и события должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="14070-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="14070-110">Свойства и методы должны быть объявлены в интерфейсе класса.</span><span class="sxs-lookup"><span data-stu-id="14070-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="14070-111">События должны быть объявлены в интерфейсе событий.</span><span class="sxs-lookup"><span data-stu-id="14070-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="14070-112">Другие открытые элементы в классе, которые не объявлены в этих интерфейсах, не будут доступны для COM, но будут доступны другим объектам .NET.</span><span class="sxs-lookup"><span data-stu-id="14070-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="14070-113">Чтобы предоставить свойства и методы COM, их необходимо объявить в интерфейсе класса, пометить атрибутом `DispId` и реализовать в классе.</span><span class="sxs-lookup"><span data-stu-id="14070-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="14070-114">Порядок объявления членов в интерфейсе — это порядок, используемый для виртуальной таблицы COM.</span><span class="sxs-lookup"><span data-stu-id="14070-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="14070-115">Чтобы предоставить события из класса, их необходимо объявить в интерфейсе событий и пометить атрибутом `DispId`.</span><span class="sxs-lookup"><span data-stu-id="14070-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="14070-116">Класс не должен реализовывать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="14070-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="14070-117">Класс реализует интерфейс класса; он может реализовывать несколько интерфейсов, но первой реализацией будет интерфейс класса по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="14070-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="14070-118">Реализуйте методы и свойства, доступные модели COM здесь.</span><span class="sxs-lookup"><span data-stu-id="14070-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="14070-119">Они должны быть помечены как открытые и соответствовать объявлениям в интерфейсе класса.</span><span class="sxs-lookup"><span data-stu-id="14070-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="14070-120">Кроме того, объявите здесь события, инициируемые классом.</span><span class="sxs-lookup"><span data-stu-id="14070-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="14070-121">Они должны быть помечены как открытые и соответствовать объявлениям в интерфейсе событий.</span><span class="sxs-lookup"><span data-stu-id="14070-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14070-122">Пример</span><span class="sxs-lookup"><span data-stu-id="14070-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="14070-123">См. также</span><span class="sxs-lookup"><span data-stu-id="14070-123">See also</span></span>

- [<span data-ttu-id="14070-124">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="14070-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="14070-125">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="14070-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="14070-126">Страница "Сборка" в конструкторе проектов (C#)</span><span class="sxs-lookup"><span data-stu-id="14070-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
