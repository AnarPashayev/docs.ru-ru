---
title: -main (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 7d3cfce474023907eda0bc40b692e4bbb65ffb96
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802832"
---
# <a name="-main-c-compiler-options"></a>-main (параметры компилятора C#)
Этот параметр определяет класс, который содержит точку входа в программу, если метод **Main** содержит сразу несколько классов.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Аргументы  
 `class`  
 Тип, содержащий метод **Main**.  
 Указанное имя класса должно быть полным; оно должно включать полное пространство имен, содержащее ключевое слово class, за которым следует имя класса. Например, если метод `Main` находится в классе `Program` в пространстве имен `MyApplication.Core`, необходимо указать параметр компилятора `-main:MyApplication.Core.Program`.
  
## <a name="remarks"></a>Примечания  
 Если в компиляцию входят несколько типов с методом [Main](../../programming-guide/main-and-command-args/index.md), можно указать, какой из них содержит метод **Main**, который нужно использовать как точку входа в программу.  
  
 Этот параметр предназначен для использования при компиляции файлов EXE.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1. Откройте страницу **Свойства** проекта.  
  
2. Перейдите на страницу свойств **Приложение**.  
  
3. Измените свойство **Автоматически запускаемый объект**.  
  
     Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Настройка параметра компилятора вручную путем редактирования файла. csproj
  
Этот параметр можно настроить, отредактировав файл .csproj и добавив элемент `StartupObject` в раздел `PropertyGroup`. Пример:

```
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Пример  
 Скомпилируйте `t2.cs` и `t3.cs`, указав, что метод **Main** будет находиться в `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>См. также

- [Параметры компилятора C# ](./index.md)
- [Управление свойствами проектов и решений](/visualstudio/ide/managing-project-and-solution-properties)
