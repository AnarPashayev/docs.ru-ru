---
title: -addmodule (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: f2fae0be3ba958dc9776ed253c178933e4f76024
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69607045"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (параметры компилятора C#)
Установка этого параметра приводит к добавлению модуля, созданного с помощью параметра target:module для текущей компиляции.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Аргументы  
 `file`, `file2`  
 Выходной файл, содержащий метаданные. В данный файл не может входить манифест сборки. Чтобы импортировать несколько файлов, разделите их имена запятыми или точками с запятой.  
  
## <a name="remarks"></a>Примечания  
 Все модули, добавленные с помощью **-addmodule**, во время выполнения должны находиться в том же каталоге, что и выходной файл. То есть во время компиляции можно указать модуль в любом каталоге, но во время выполнения он должен находиться в каталоге приложения. Если во время выполнения модуль отсутствует в каталоге приложения, возникнет <xref:System.TypeLoadException>.  
  
 `file` не может содержать сборку. Например, если выходной файл был создан с помощью [-target:module](./target-module-compiler-option.md), для импорта его метаданных можно использовать **-addmodule**.  
  
 Если выходной файл был создан с помощью параметра **-target**, отличного от **-target:module**, для импорта его метаданных запрещено использовать **-addmodule**, но можно [-reference](./reference-compiler-option.md).  
  
 Этот параметр компилятора недоступен в Visual Studio; проект не может ссылаться на модуль. Кроме того, этот параметр компилятора нельзя изменить программным способом.  
  
## <a name="example"></a>Пример  
 Скомпилируйте исходный файл `input.cs` и добавьте метаданные из `metad1.netmodule` и `metad2.netmodule`, чтобы создать `out.exe`.  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>См. также

- [Параметры компилятора C# ](./index.md)
- [Управление свойствами проектов и решений](/visualstudio/ide/managing-project-and-solution-properties)
- [Многофайловые сборки](../../../framework/app-domains/multifile-assemblies.md)
- [Практическое руководство. Создание многофайловой сборки](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
