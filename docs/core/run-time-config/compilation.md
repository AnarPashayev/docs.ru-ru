---
title: Параметры конфигурации компиляции
description: Сведения о параметрах времени выполнения, определяющих, как JIT-компилятор работает для приложений .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: cfcf9b5fc8d11a4ae35ab9b152f32133cd6930bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762010"
---
# <a name="run-time-configuration-options-for-compilation"></a>Параметры конфигурации времени выполнения для компиляции

## <a name="tiered-compilation"></a>Многоуровневая компиляция

- Указывает, использует ли JIT-компилятор [многоуровневую компиляцию](../whats-new/dotnet-core-3-0.md#tiered-compilation). Многоуровневая компиляция обеспечивает переход методов по двум уровням.
  - Первый уровень создает код быстрее ([быстрая JIT-компиляция](#quick-jit)) или загружает предварительно скомпилированный код ([ReadyToRun](#readytorun)).
  - Второй уровень создает оптимизированный код в фоновом режиме (JIT-компиляция с оптимизацией).
- В .NET Core 3.0 и более поздних версий многоуровневая компиляция включена по умолчанию.
- В .NET Core 2.1 и 2.2 многоуровневая компиляция отключена по умолчанию.
- Дополнительные сведения см. в [руководстве по многоуровневой компиляции](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true` — включено<br/>`false` — отключено |
| **Свойство MSBuild** | `TieredCompilation` | `true` — включено<br/>`false` — отключено |
| **Переменная среды** | `COMPlus_TieredCompilation` | `1` — включено<br/>`0` — отключено |

### <a name="examples"></a>Примеры

Файл *runtimeconfig.json*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Файл проекта:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>Быстрая JIT-компиляция

- Указывает, использует ли JIT-компилятор *быструю JIT-компиляцию*. Для методов, которые не содержат циклы и для которых предварительно скомпилированный код недоступен, быстрая JIT-компиляция компилирует их быстрее, но без оптимизации.
- Включение быстрой JIT-компиляции сокращает время запуска, однако создаваемый код может обладать низкой производительностью. Например, код может использовать больше пространства стека, выделять больше памяти и работать медленнее.
- Если быстрая JIT-компиляция отключена, но включена [многоуровневая компиляция](#tiered-compilation), в многоуровневой компиляции участвует только предварительно скомпилированный код. Если метод не был предварительно скомпилирован с помощью [ReadyToRun](#readytorun), то поведение JIT будет таким же, как если бы [многоуровневая компиляция](#tiered-compilation) была отключена.
- В .NET Core 3.0 и более поздних версий быстрая JIT-компиляция включена по умолчанию.
- В .NET Core 2.1 и 2.2 быстрая JIT-компиляция отключена по умолчанию.

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true` — включено<br/>`false` — отключено |
| **Свойство MSBuild** | `TieredCompilationQuickJit` | `true` — включено<br/>`false` — отключено |
| **Переменная среды** | `COMPlus_TC_QuickJit` | `1` — включено<br/>`0` — отключено |

### <a name="examples"></a>Примеры

Файл *runtimeconfig.json*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Файл проекта:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>Быстрая JIT-компиляция для циклов

- Указывает, использует ли JIT-компилятор быструю JIT-компиляцию для методов, содержащих циклы.
- Включение быстрой JIT-компиляции для циклов может повысить производительность при запуске. Однако длительные циклы могут задерживаться на участках менее оптимизированного кода.
- Если [быстрая JIT-компиляция](#quick-jit) отключена, этот параметр не действует.
- Если этот параметр не задан, быстрая JIT-компиляция не используется для методов, содержащих циклы. Это эквивалентно присвоению значения `false`.

| | Имя параметра | Значения |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false` — отключено<br/>`true` — включено |
| **Свойство MSBuild** | `TieredCompilationQuickJitForLoops` | `false` — отключено<br/>`true` — включено |
| **Переменная среды** | `COMPlus_TC_QuickJitForLoops` | `0` — отключено<br/>`1` — включено |

### <a name="examples"></a>Примеры

Файл *runtimeconfig.json*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Файл проекта:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Указывает, использует ли среда выполнения .NET Core предварительно скомпилированный код для образов с доступными данными ReadyToRun. При отключении этого параметра среда выполнения будет принудительно выполнять JIT-компиляцию платформенного кода.
- Дополнительные сведения см. в разделе о [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Если этот параметр не задан, .NET использует данные ReadyToRun, когда они доступны. Это эквивалентно присвоению значения `1`.

| | Имя параметра | Значения |
| - | - | - |
| **Переменная среды** | `COMPlus_ReadyToRun` | `1` — включено<br/>`0` — отключено |
