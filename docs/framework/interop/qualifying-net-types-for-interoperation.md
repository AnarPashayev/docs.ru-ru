---
title: Уточнение типов .NET для взаимодействия
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363980"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="a7481-102">Уточнение типов .NET для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7481-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="a7481-103">Если вы планируете предоставлять типы в сборке COM-приложениям, во время разработки необходимо учитывать требования COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a7481-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="a7481-104">Управляемые типы (класс, интерфейс, структура и перечисление) легко интегрируются с COM-типами, если следовать приведенным ниже рекомендациям:</span><span class="sxs-lookup"><span data-stu-id="a7481-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="a7481-105">Классы должны явным образом реализовывать интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="a7481-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="a7481-106">Несмотря на то, что COM-взаимодействие предоставляет механизм для автоматического создания интерфейса, содержащего все члены класса и члены его базового класса, гораздо эффективнее предоставлять явные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="a7481-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="a7481-107">Автоматически создаваемый интерфейс называется интерфейсом класса.</span><span class="sxs-lookup"><span data-stu-id="a7481-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="a7481-108">См. рекомендации в разделе [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса).</span><span class="sxs-lookup"><span data-stu-id="a7481-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="a7481-109">В Visual Basic, C# и C++ можно внедрять определения интерфейса в код вместо использования языка IDL или его эквивалента.</span><span class="sxs-lookup"><span data-stu-id="a7481-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="a7481-110">Дополнительные сведения о синтаксисе см. в документации по соответствующему языку.</span><span class="sxs-lookup"><span data-stu-id="a7481-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="a7481-111">Управляемые типы должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="a7481-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="a7481-112">Регистрация и экспорт в библиотеку типов поддерживаются только для открытых типов.</span><span class="sxs-lookup"><span data-stu-id="a7481-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="a7481-113">В результате видимыми для модели COM являются только открытые типы.</span><span class="sxs-lookup"><span data-stu-id="a7481-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="a7481-114">Управляемые типы предоставляют функциональные возможности другому управляемому коду, который может быть недоступен для модели COM.</span><span class="sxs-lookup"><span data-stu-id="a7481-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="a7481-115">Например, COM-клиентам не предоставляются параметризованные конструкторы, статические методы и поля констант.</span><span class="sxs-lookup"><span data-stu-id="a7481-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="a7481-116">Кроме того, поскольку среда выполнения выполняет маршалинг данных из типа и обратно, данные могут копироваться и преобразовываться.</span><span class="sxs-lookup"><span data-stu-id="a7481-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="a7481-117">Методы, свойства, поля и события должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="a7481-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="a7481-118">Члены открытых типов, которые должны быть видимыми для модели COM, также должны быть открытыми.</span><span class="sxs-lookup"><span data-stu-id="a7481-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="a7481-119">Видимость сборки, открытого типа или открытых членов открытого типа можно ограничить с помощью атрибута <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a7481-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="a7481-120">По умолчанию все открытые типы и члены являются видимыми.</span><span class="sxs-lookup"><span data-stu-id="a7481-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="a7481-121">Для активации из модели COM типы должны иметь открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="a7481-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="a7481-122">Таким образом, видимыми для модели COM являются только управляемые открытые типы.</span><span class="sxs-lookup"><span data-stu-id="a7481-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="a7481-123">При этом без открытого конструктора без параметров (конструктор без аргументов) COM-клиенты не смогут создавать этот тип.</span><span class="sxs-lookup"><span data-stu-id="a7481-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="a7481-124">COM-клиенты могут использовать такой тип, если он активирован другими способами.</span><span class="sxs-lookup"><span data-stu-id="a7481-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="a7481-125">Типы не могут быть абстрактными.</span><span class="sxs-lookup"><span data-stu-id="a7481-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="a7481-126">Ни COM-клиенты, ни клиенты .NET не могут создавать абстрактные типы.</span><span class="sxs-lookup"><span data-stu-id="a7481-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="a7481-127">При экспорте в модель COM иерархия наследования управляемого типа преобразуется в плоскую структуру.</span><span class="sxs-lookup"><span data-stu-id="a7481-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="a7481-128">Кроме того, в управляемой и неуправляемой средах существуют различия в управлении версиями.</span><span class="sxs-lookup"><span data-stu-id="a7481-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="a7481-129">Типы, предоставляемые модели COM, имеют характеристики управления версиями, отличные от других управляемых типов.</span><span class="sxs-lookup"><span data-stu-id="a7481-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7481-130">См. также</span><span class="sxs-lookup"><span data-stu-id="a7481-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="a7481-131">Предоставление компонентов .NET Framework клиентам COM</span><span class="sxs-lookup"><span data-stu-id="a7481-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- <span data-ttu-id="a7481-132">[Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса)</span><span class="sxs-lookup"><span data-stu-id="a7481-132">[Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface)</span></span>
- [<span data-ttu-id="a7481-133">Применение атрибутов взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a7481-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="a7481-134">Упаковка сборки для модели COM</span><span class="sxs-lookup"><span data-stu-id="a7481-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
