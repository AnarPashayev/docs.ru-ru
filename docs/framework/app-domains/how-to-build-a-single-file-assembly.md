---
title: Как выполнить Построение однофайловой сборки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304003"
---
# <a name="how-to-build-a-single-file-assembly"></a>Как выполнить Построение однофайловой сборки

Однофайловая сборка, являясь простейшим типом сборки, содержит данные о типе и реализации, а также [манифест сборки](../../../docs/framework/app-domains/assembly-manifest.md). Для создания однофайловой сборки можно использовать компиляторы командной строки или Visual Studio. По умолчанию компилятор создает файл сборки с расширением .exe.

> [!NOTE]
> Visual Studio для C# и Visual Basic можно использовать только для создания однофайловых сборок. Чтобы создать многофайловую сборку, необходимо использовать компиляторы командной строки или Visual C++.

В следующих процедурах показано создани6 однофайловых сборок с помощью компиляторов, работающих в режиме командной строки.

## <a name="to-create-an-assembly-with-an-exe-extension"></a>Создание сборки с расширением .exe

1. В командной строке введите следующую команду:

     \<*команда компилятора*> \<*имя модуля*>

     В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.

 В следующем примере создается сборка с именем `myCode.exe` из модуля кода с именем `myCode`.

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Создание сборки с расширением .exe и указание имени выходного файла

1. В командной строке введите следующую команду:

     \<*команда компилятора*> **/out:**\<*имя файла*> \<*имя модуля*>

     В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, *имя файла* — имя выходного файла, а *имя модуля* — имя компилируемого в сборку модуля кода.

 В следующем примере создается сборка с именем `myAssembly.exe` из модуля кода с именем `myCode`.

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>Создание библиотечных сборок
 Библиотечная сборка аналогична библиотеке классов. Библиотечная сборка аналогична библиотеке классов. Она содержит типы, на которые имеются ссылки в других сборках, но не имеет точки входа, с которой начинается выполнение.

### <a name="to-create-a-library-assembly"></a>Создание библиотечной сборки

1. В командной строке введите следующую команду:

     \<*команда компилятора*> **/t:library** \<*имя модуля*>

     В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода. Можно также использовать другие параметры компилятора, такие как **-out:**.

 В следующем примере создается библиотечная сборка с именем `myCodeAssembly.dll` из модуля кода с именем `myCode`.

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>См. также

- [Создание сборок](../../../docs/framework/app-domains/create-assemblies.md)
- [Многофайловые сборки](../../../docs/framework/app-domains/multifile-assemblies.md)
- [Практическое руководство. Создание многофайловой сборки](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Программирование с использованием сборок](../../../docs/framework/app-domains/programming-with-assemblies.md)