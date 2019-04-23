---
title: -subsystemversion (параметры компилятора C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: af753b25750c6ef98b4df12eec03c355501a278e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481162"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (параметры компилятора C#)

Указывает минимальную версию подсистемы, в которой может выполняться созданный исполняемый файл, то есть определяет версии Windows, в которых может работать исполняемый файл. Чаще всего этот параметр предоставляет исполняемому файлу возможность использовать определенные возможности безопасности, недоступные в прежних версиях Windows.

> [!NOTE]
>  Чтобы задать саму подсистему, используйте параметр компилятора [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).

## <a name="syntax"></a>Синтаксис

```console
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

  - [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)

  - [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)

  - [-platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)

- Значение по умолчанию — 6.00, если используется средство MSBuild, приложение предназначено для [!INCLUDE[net_v45](~/includes/net-v45-md.md)], и не установлены параметры компилятора, определенные ранее в этом списке.

- Если ни одно из предыдущих условий не верно, значение по умолчанию — 4.00.

## <a name="setting-this-option"></a>Задание этого параметра

Чтобы задать параметр компилятора **-subsystemversion** в Visual Studio, нужно открыть CSPROJ-файл и указать значение для свойства `SubsystemVersion` в XML MSBuild. Этот параметр невозможно задать в интегрированной среде разработки Visual Studio. Дополнительные сведения см. выше в подразделе "Значения по умолчанию" или в разделе [Общие свойства проектов MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>См. также

- [Параметры компилятора C# ](../../../csharp/language-reference/compiler-options/index.md)
