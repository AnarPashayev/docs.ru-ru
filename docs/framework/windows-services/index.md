---
title: Разработка служебных приложений Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
ms.openlocfilehash: 32aa2c1c4cd31e4591c9fa30c05ebe61058f94c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008711"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="76d64-102">Разработка приложений службы Windows</span><span class="sxs-lookup"><span data-stu-id="76d64-102">Develop Windows service apps</span></span>

<span data-ttu-id="76d64-103">С помощью Visual Studio или пакета SDK для .NET Framework можно легко создавать службы. Просто создайте приложение, которое устанавливается как служба.</span><span class="sxs-lookup"><span data-stu-id="76d64-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="76d64-104">Такие приложения называются службами Windows.</span><span class="sxs-lookup"><span data-stu-id="76d64-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="76d64-105">Используя компоненты платформы, можно создавать, устанавливать, запускать, останавливать и администрировать службы.</span><span class="sxs-lookup"><span data-stu-id="76d64-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="76d64-106">В Visual Studio можно создать службы с помощью управляемого кода на Visual C# или Visual Basic, который при необходимости может взаимодействовать с существующим кодом C++.</span><span class="sxs-lookup"><span data-stu-id="76d64-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="76d64-107">Или можно создать службу Windows на машинном языке C++ с помощью [мастера проектов ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="76d64-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="76d64-108">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="76d64-108">In this section</span></span>

[<span data-ttu-id="76d64-109">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="76d64-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

<span data-ttu-id="76d64-110">Сведения о приложениях служб Windows, времени существования служб и отличиях приложений служб от распространенных типов проектов.</span><span class="sxs-lookup"><span data-stu-id="76d64-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="76d64-111">Пошаговое руководство: Создание приложения служб Windows в конструкторе компонентов</span><span class="sxs-lookup"><span data-stu-id="76d64-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="76d64-112">Пример создания службы на Visual Basic и Visual C#.</span><span class="sxs-lookup"><span data-stu-id="76d64-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="76d64-113">Программная архитектура приложений служб</span><span class="sxs-lookup"><span data-stu-id="76d64-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)

<span data-ttu-id="76d64-114">Описание элементов языка, используемых при создании служб.</span><span class="sxs-lookup"><span data-stu-id="76d64-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="76d64-115">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="76d64-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

<span data-ttu-id="76d64-116">Создание и настройка служб Windows с помощью шаблона проекта службы Windows.</span><span class="sxs-lookup"><span data-stu-id="76d64-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="76d64-117">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="76d64-117">Related sections</span></span>

<span data-ttu-id="76d64-118"><xref:System.ServiceProcess.ServiceBase> — описываются основные характеристики класса <xref:System.ServiceProcess.ServiceBase>, который используется для создания служб.</span><span class="sxs-lookup"><span data-stu-id="76d64-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="76d64-119"><xref:System.ServiceProcess.ServiceProcessInstaller> — описываются возможности класса <xref:System.ServiceProcess.ServiceProcessInstaller>, который используется вместе с классом <xref:System.ServiceProcess.ServiceInstaller> для установки и удаления службы.</span><span class="sxs-lookup"><span data-stu-id="76d64-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="76d64-120"><xref:System.ServiceProcess.ServiceInstaller> — описываются возможности класса <xref:System.ServiceProcess.ServiceInstaller>, который используется вместе с классом <xref:System.ServiceProcess.ServiceProcessInstaller> для установки и удаления службы.</span><span class="sxs-lookup"><span data-stu-id="76d64-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="76d64-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) (Создание проектов на основе шаблонов) — описываются типы проектов, которые используются в этом разделе, и способ их выбора.</span><span class="sxs-lookup"><span data-stu-id="76d64-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
