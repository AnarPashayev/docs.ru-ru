---
description: -target:appcontainerexe (параметры компилятора C#)
title: -target:appcontainerexe (параметры компилятора C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8c3b85c2f5a20788bd311e9bf3b300c32967da77
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128586"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (параметры компилятора C#)
Если используется параметр компилятора **-target:appcontainerexe**, компилятор создает исполняемый файл Windows (EXE-файл), который должен запускаться в контейнере приложения. Этот параметр аналогичен [-target:winexe](./target-winexe-compiler-option.md), но предназначен для приложений Магазина Windows 8.x.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Remarks  
 Этот параметр устанавливает бит в [переносимом исполняемом](/windows/desktop/Debug/pe-format) файле (PE), чтобы обеспечить запуск приложения в контейнере. Если он установлен, при попытке запустить исполняемый файл вне контейнера приложения методом CreateProcess будет возникать ошибка.  
  
 Выходной файл получает имя входного файла, содержащего метод [Main](../../programming-guide/main-and-command-args/index.md), если только с помощью параметра [-out](./out-compiler-option.md) не указано иное.  
  
 Если этот параметр указан в командной строке, все файлы до следующего параметра **-out** или **-target** будут использоваться для создания исполняемого файла.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Установка данного параметра компилятора в интегрированной среде разработки  
  
1. В **обозревателе решений** откройте контекстное меню своего проекта и выберите пункт **Свойства**.  
  
2. На вкладке **Приложение** в списке **Тип выходных данных** выберите **Приложение для Магазина Windows**.  
  
     Этот параметр доступен только для шаблонов приложений Магазина Windows 8.x.  
  
 Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Пример  
 Следующая команда компилирует `filename.cs` в исполняемый файл Windows, который может быть запущен только в контейнере приложения.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>См. также раздел

- [-target (параметры компилятора C#)](./target-compiler-option.md)
- [-target:winexe (параметры компилятора C#)](./target-winexe-compiler-option.md)
- [Параметры компилятора C# ](./index.md)
