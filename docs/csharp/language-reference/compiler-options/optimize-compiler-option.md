---
title: -optimize (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 25a9ee1b27836dfb00dcbc72712ed068639fa2fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320036"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (параметры компилятора C#)
Параметр **-optimize** включает или отключает оптимизацию кода компилятором, чтобы сделать код более быстрым, коротким и эффективным.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Примечания  
 Кроме того, параметр **-optimize** включает оптимизацию кода во время выполнения в общеязыковой среде выполнения (CLR).  
  
 По умолчанию оптимизация отключена. Чтобы включить оптимизацию, укажите **-optimize+**.  
  
 При создании модуля для сборки используйте те же настройки параметра **-optimize**, что и для сборки.  
  
 **-o** является краткой формой параметра **-optimize**.  
  
 Параметры **-optimize** и [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) можно объединять.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1. Откройте страницу **Свойства** проекта.  
  
2. Щелкните страницу свойств **Сборка**.  
  
3. Измените свойство **Оптимизировать код**.  
  
 Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Пример  
 Скомпилируйте `t2.cs` и включите выполняемую компилятором оптимизацию:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>См. также

- [Параметры компилятора C# ](../../../csharp/language-reference/compiler-options/index.md)
- [Управление свойствами проектов и решений](/visualstudio/ide/managing-project-and-solution-properties)
