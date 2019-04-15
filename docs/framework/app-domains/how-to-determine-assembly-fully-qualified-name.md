---
title: Практическое руководство. определение полного имени сборки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097542"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a><span data-ttu-id="ee8e4-102">Практическое руководство. определение полного имени сборки</span><span class="sxs-lookup"><span data-stu-id="ee8e4-102">How to: Determine an Assembly's Fully Qualified Name</span></span>
<span data-ttu-id="ee8e4-103">Чтобы получить полное имя сборки в глобальном кэше сборок, используйте средство глобального кэша сборок ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="ee8e4-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="ee8e4-104">См. практическое руководство по [ Просмотр содержимого глобального кэша сборок](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="ee8e4-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="ee8e4-105">Получить полное имя сборки, которая отсутствует в глобальном кэше сборок, можно несколькими способами: использовать код для вывода данных в консоль или в переменную либо применить [дизассемблер IL Ildasm.exe](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) для просмотра метаданных сборки, которые содержат полное имя.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="ee8e4-106">Если сборка уже загружена приложением, то для получения полного имени можно извлечь значение свойства <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="ee8e4-107">Этот подход можно использовать независимо от того, находится ли сборка в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="ee8e4-108">Иллюстрация приведена в примере.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="ee8e4-109">Если вы знаете путь к файлу сборки в системе, то вы можете вызвать статический метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> (`Shared` в Visual Basic), чтобы получить полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="ee8e4-110">Ниже приведен простой пример.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="ee8e4-111">Вы можете воспользоваться [дизассемблером IL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md), чтобы просмотреть метаданные сборки, которые содержат ее полное имя.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="ee8e4-112">Подробнее о задании атрибутов сборки, таких как версия, язык и региональные параметры и имя сборки, см. в разделе [Настройка атрибутов сборки](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ee8e4-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="ee8e4-113">Подробнее о присвоении сборке строгого имени см. в разделе [Создание и использование сборок со строгими именами](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ee8e4-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee8e4-114">Пример</span><span class="sxs-lookup"><span data-stu-id="ee8e4-114">Example</span></span>  
 <span data-ttu-id="ee8e4-115">В примере кода ниже показано, как просмотреть полное имя сборки, содержащей указанный класс, в консоли.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="ee8e4-116">Так как в нем извлекается имя сборки, которую приложение уже загрузило, не имеет значения, находится ли сборка в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="ee8e4-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ee8e4-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ee8e4-117">See also</span></span>

- [<span data-ttu-id="ee8e4-118">Имена сборок</span><span class="sxs-lookup"><span data-stu-id="ee8e4-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)
- [<span data-ttu-id="ee8e4-119">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="ee8e4-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="ee8e4-120">Создание и использование сборок со строгими именами</span><span class="sxs-lookup"><span data-stu-id="ee8e4-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="ee8e4-121">глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="ee8e4-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="ee8e4-122">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="ee8e4-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ee8e4-123">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="ee8e4-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
