---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e42501a002d808f31dc3d599dc030e96c573a22f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380323"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Указывает минимальную версию подсистемы, в которой может выполняться созданный исполняемый файл, то есть определяет версии Windows, в которых может работать исполняемый файл. Чаще всего этот параметр предоставляет исполняемому файлу возможность использовать определенные возможности безопасности, недоступные в прежних версиях Windows.

> [!NOTE]
> Чтобы задать саму подсистему, используйте параметр компилятора [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).

## <a name="syntax"></a>Синтаксис

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Параметры

`major.minor`

Минимальная требуемая версия подсистемы, через точку записывается основная и дополнительная версии. Например, можно указать, что приложение не может выполняться в операционной системе старше Windows 7, если задать для этого параметра значение 6.01, как указано в таблице ниже в этом разделе. Необходимо указать значения для параметра `major` и `minor` в виде целых чисел.

Нули в начале версии `minor` не изменяют версию, нули в конце — изменяют. Например, 6.1 и 6.01 — одна версия, а 6.10 — другая. Рекомендуется указывать дополнительный номер версии двумя цифрами, чтобы избежать путаницы.

## <a name="remarks"></a>Примечания

В следующей таблице перечислены распространенные версии подсистем Windows.

|Версия Windows|Версия подсистемы|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|

## <a name="default-values"></a>Значения по умолчанию

Значение по умолчанию параметра компилятора **-subsystemversion** зависит от условий в следующем списке:

- Значение по умолчанию — 6.02, если задан любой параметр компилятора из следующего списка.

  - [/target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)

  - [/target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)

- Значение по умолчанию — 6.00, если вы используете MSBuild, целевой платформой является .NET Framework 4.5 и вы не задали параметры компилятора, которые были заданы ранее в этом списке.

- Если ни одно из предыдущих условий не верно, значение по умолчанию — 4.00.

## <a name="setting-this-option"></a>Задание этого параметра

Чтобы задать **- subsystemversion** параметр компилятора в Visual Studio, необходимо открыть VBPROJ-файл и указать значение для `SubsystemVersion` свойство в MSBuild XML. Этот параметр невозможно задать в интегрированной среде разработки Visual Studio. Дополнительные сведения см. выше в подразделе "Значения по умолчанию" или в разделе [Общие свойства проектов MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)

- [Свойства MSBuild](/visualstudio/msbuild/msbuild-properties)
