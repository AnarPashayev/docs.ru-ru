---
title: сборки и параллельное выполнение
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa44090e589e7a2a70b8fb7dbd8d5e6967c1ed19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126647"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="f26bf-102">сборки и параллельное выполнение</span><span class="sxs-lookup"><span data-stu-id="f26bf-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="f26bf-103">Под параллельным выполнением понимается возможность сохранения и выполнения нескольких версий приложения или компонента на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="f26bf-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="f26bf-104">Это означает, что одновременно на одном и том же компьютере в одно и то же время можно иметь несколько версий среды выполнения и несколько версий приложений и компонентов, использующих среду выполнения данной версии.</span><span class="sxs-lookup"><span data-stu-id="f26bf-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="f26bf-105">Параллельное выполнение предоставляет дополнительные возможности выбора версий компонента, с которым связано приложение, а также дополнительные возможности выбора используемой приложением версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f26bf-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="f26bf-106">Поддержка параллельного хранения и выполнения различных версий одной и той же сборки является неотъемлемой частью использования строгих имен. Эта поддержка встроена в инфраструктуру среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f26bf-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="f26bf-107">Поскольку номер версии сборки со строгим именем является частью ее удостоверения, среда выполнения позволяет хранить несколько версий одной и той же сборки в глобальном кэше сборок и загружать эти сборки на этапе выполнения.</span><span class="sxs-lookup"><span data-stu-id="f26bf-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="f26bf-108">Хотя среда выполнения предоставляет возможность создавать параллельные приложения, параллельное выполнение не реализуется автоматически.</span><span class="sxs-lookup"><span data-stu-id="f26bf-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="f26bf-109">Дополнительные сведения о создании приложений для параллельного выполнения см. в разделе [Рекомендации по созданию компонентов для параллельного выполнения](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="f26bf-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26bf-110">См. также</span><span class="sxs-lookup"><span data-stu-id="f26bf-110">See also</span></span>

- [<span data-ttu-id="f26bf-111">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="f26bf-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="f26bf-112">Сборки в среде CLR</span><span class="sxs-lookup"><span data-stu-id="f26bf-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
