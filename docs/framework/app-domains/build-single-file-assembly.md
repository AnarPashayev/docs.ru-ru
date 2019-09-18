---
title: Практическое руководство. Создание однофайловой сборки .NET Framework
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991247"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Практическое руководство. Создание однофайловой сборки .NET Framework

Однофайловая сборка, являясь простейшим типом сборки, содержит данные о типе и реализации, а также [манифест сборки](../../standard/assembly/manifest.md). Для создания однофайловой сборки, ориентированной на .NET Framework, можно использовать компиляторы командной строки или Visual Studio. По умолчанию компилятор создает файл сборки с расширением *EXE*.

> [!NOTE]
> Visual Studio для C# и Visual Basic можно использовать только для создания однофайловых сборок. Чтобы создать многофайловую сборку, необходимо использовать компиляторы командной строки или Visual C++.

В следующих процедурах показано создани6 однофайловых сборок с помощью компиляторов, работающих в режиме командной строки.

## <a name="create-an-assembly-with-an-exe-extension"></a>Создание сборки с расширением EXE

В командной строке введите следующую команду:

\<*команда компилятора*> \<*имя модуля*>

В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.

В следующем примере создается сборка с именем *myCode.exe* из модуля кода с именем `myCode`.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Создание сборки с расширением EXE и указание имени выходного файла

В командной строке введите следующую команду:

\<*команда компилятора*>  **/out:** \<*имя файла*> \<*имя модуля*>

В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, *имя файла* — имя выходного файла, а *имя модуля* — имя компилируемого в сборку модуля кода.

В следующем примере создается сборка с именем *myAssembly.exe* из модуля кода с именем `myCode`.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Создание библиотечных сборок
 Библиотечная сборка аналогична библиотеке классов. Библиотечная сборка аналогична библиотеке классов. Она содержит типы, на которые имеются ссылки в других сборках, но не имеет точки входа, с которой начинается выполнение.

Чтобы создать библиотечную сборку, в командной строке введите следующую команду:

\<*команда компилятора*>  **/t:library** \<*имя модуля*>

В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода. Можно также использовать другие параметры компилятора, такие как **-out:** .

В следующем примере создается библиотечная сборка с именем *myCodeAssembly.dll* из модуля кода с именем `myCode`.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>См. также

- [Создание сборок](../../standard/assembly/create.md)
- [Многофайловые сборки](multifile-assemblies.md)
- [Практическое руководство. Создание многофайловой сборки](build-multifile-assembly.md)
- [Программирование с использованием сборок](../../standard/assembly/program.md)
