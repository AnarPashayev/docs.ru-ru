---
title: Размещение сборок
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119956"
---
# <a name="assembly-placement"></a><span data-ttu-id="7f295-102">Размещение сборок</span><span class="sxs-lookup"><span data-stu-id="7f295-102">Assembly Placement</span></span>
<span data-ttu-id="7f295-103">Для большинства приложений .NET Framework сборки, составляющие приложение, располагаются в папке приложения, во вложенной папке этой папки или в глобальном кэше сборок (если сборка является совместно используемой).</span><span class="sxs-lookup"><span data-stu-id="7f295-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="7f295-104">С помощью [элемента \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) в файле конфигурации можно изменить место, где среда CLR будет искать сборки.</span><span class="sxs-lookup"><span data-stu-id="7f295-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="7f295-105">Если у сборки нет строгого имени, то расположение, которое указывается с помощью [элемента \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md), ограничивается папкой приложения или вложенной папкой этой папки.</span><span class="sxs-lookup"><span data-stu-id="7f295-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="7f295-106">Если у сборки есть строгое имя, то [элемент \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) может указывать любое расположение на компьютере или в сети.</span><span class="sxs-lookup"><span data-stu-id="7f295-106">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="7f295-107">Аналогичные правила применяются к расположению сборок при работе с неуправляемым кодом или с приложениями, реализующими COM-взаимодействие: если сборка совместно используется несколькими приложениями, то она должна устанавливаться в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="7f295-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="7f295-108">При использовании сборок с неуправляемым кодом их необходимо экспортировать в виде библиотеки типов и зарегистрировать.</span><span class="sxs-lookup"><span data-stu-id="7f295-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="7f295-109">Сборки, использующиеся для обеспечения COM-взаимодействия, должны регистрироваться в каталоге, хотя в некоторых случаях такая регистрация производится автоматически.</span><span class="sxs-lookup"><span data-stu-id="7f295-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f295-110">См. также</span><span class="sxs-lookup"><span data-stu-id="7f295-110">See also</span></span>

- [<span data-ttu-id="7f295-111">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="7f295-111">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7f295-112">Настройка приложений</span><span class="sxs-lookup"><span data-stu-id="7f295-112">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="7f295-113">Взаимодействие с неуправляемым кодом</span><span class="sxs-lookup"><span data-stu-id="7f295-113">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="7f295-114">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="7f295-114">Assemblies in .NET</span></span>](index.md)
