---
title: Маршалинг с помощью COM- взаимодействия
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16f94e8b85a1bedb8b7791c2b7fcaf6d154ba1b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833524"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="fd7a7-102">Маршалинг с помощью COM- взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fd7a7-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="fd7a7-103">COM-взаимодействие обеспечивает поддержку как для использования COM-объектов из управляемого кода, так и для предоставления доступа к управляемым объектам для COM.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="fd7a7-104">Поддержка маршалинга данных в COM и обратно достаточно полная и почти всегда обеспечивает правильное поведение маршалинга.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="fd7a7-105">Пакет средств разработки программного обеспечения для Windows включает следующие средства COM-взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="fd7a7-105">The Windows Software Development Kit (SDK) includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="fd7a7-106">[Средство импорта библиотек типов (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), которое преобразует библиотеку типов COM в сборку взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="fd7a7-107">Эта сборка используется службой маршалинга взаимодействия для создания оболочек, маршалирующих данные между управляемой и неуправляемой памятью.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="fd7a7-108">[Средство экспорта библиотек типов (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), которое создает библиотеку типов COM из сборки и формирует оболочку, которая выполняет маршалинг при вызовах методов.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="fd7a7-109">Следующие разделы посвящены процессам настройки оболочек взаимодействий для случаев, когда можно (или необходимо) предоставить упаковщику дополнительную информацию о типах.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd7a7-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="fd7a7-110">In This Section</span></span>  
<span data-ttu-id="fd7a7-111">[Практическое руководство. Создание оболочек вручную](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="fd7a7-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="fd7a7-112">Сведения о том, как вручную создать программу-оболочку COM в управляемом исходном коде.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="fd7a7-113">Практическое руководство. Миграция DCOM с управляемым кодом в WCF</span><span class="sxs-lookup"><span data-stu-id="fd7a7-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="fd7a7-114">Сведения о переносе управляемого кода DCOM в WCF для получения наиболее безопасного решения.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fd7a7-115">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="fd7a7-115">Related Sections</span></span>  
 <span data-ttu-id="fd7a7-116">[Типы данных COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-117">Содержит описание соответствующих управляемых и неуправляемых типов данных.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="fd7a7-118">[Настройка вызываемых оболочек COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-119">В этой статье описан способ явного маршалинга типов данных с использованием атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute> во время разработки.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="fd7a7-120">[Настройка вызываемых оболочек времени выполнения](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-121">Описаны способы настройки связанного с маршалингом поведения типов в сборке взаимодействия и определения типов COM вручную.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="fd7a7-122">[Расширенное COM-взаимодействие](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-123">Приводятся ссылки на дополнительные сведения о включении COM-компонентов в разрабатываемое приложение .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="fd7a7-124">[Общие сведения о преобразовании сборки в библиотеку типов](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-125">Описывается процесс преобразования при экспорте сборки в библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="fd7a7-126">[Общие сведения о преобразовании библиотеки типов в сборку](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-127">Описывается процесс преобразования при экспорте библиотеки типов в сборку.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="fd7a7-128">[Взаимодействие с помощью универсальных типов](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd7a7-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="fd7a7-129">Описываются действия, поддерживаемые при использовании универсальных типов для взаимодействия COM.</span><span class="sxs-lookup"><span data-stu-id="fd7a7-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
