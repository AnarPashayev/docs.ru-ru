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
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a>Практическое руководство. определение полного имени сборки
Чтобы получить полное имя сборки в глобальном кэше сборок, используйте средство глобального кэша сборок ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). См. практическое руководство по [ Просмотр содержимого глобального кэша сборок](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Получить полное имя сборки, которая отсутствует в глобальном кэше сборок, можно несколькими способами: использовать код для вывода данных в консоль или в переменную либо применить [дизассемблер IL Ildasm.exe](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) для просмотра метаданных сборки, которые содержат полное имя.  
  
-   Если сборка уже загружена приложением, то для получения полного имени можно извлечь значение свойства <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>. Этот подход можно использовать независимо от того, находится ли сборка в глобальном кэше сборок. Иллюстрация приведена в примере.  
  
-   Если вы знаете путь к файлу сборки в системе, то вы можете вызвать статический метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> (`Shared` в Visual Basic), чтобы получить полное имя сборки. Ниже приведен простой пример.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Вы можете воспользоваться [дизассемблером IL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md), чтобы просмотреть метаданные сборки, которые содержат ее полное имя.  
  
 Подробнее о задании атрибутов сборки, таких как версия, язык и региональные параметры и имя сборки, см. в разделе [Настройка атрибутов сборки](../../../docs/framework/app-domains/set-assembly-attributes.md). Подробнее о присвоении сборке строгого имени см. в разделе [Создание и использование сборок со строгими именами](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Пример  
 В примере кода ниже показано, как просмотреть полное имя сборки, содержащей указанный класс, в консоли. Так как в нем извлекается имя сборки, которую приложение уже загрузило, не имеет значения, находится ли сборка в глобальном кэше сборок.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>См. также

- [Имена сборок](../../../docs/framework/app-domains/assembly-names.md)
- [Создание сборок](../../../docs/framework/app-domains/create-assemblies.md)
- [Создание и использование сборок со строгими именами](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [глобальный кэш сборок](../../../docs/framework/app-domains/gac.md)
- [Обнаружение сборок в среде выполнения](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Программирование с использованием сборок](../../../docs/framework/app-domains/programming-with-assemblies.md)
