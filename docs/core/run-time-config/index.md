---
title: Параметры конфигурация во время выполнения
description: Узнайте, как настроить приложения .NET Core с помощью параметров конфигурации среды выполнения.
ms.date: 01/21/2020
ms.openlocfilehash: 5e9f292476cf953c3e63bb8e89268f7cc06b3bfc
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757854"
---
# <a name="net-core-run-time-configuration-settings"></a>Параметры конфигурации среды выполнения .NET Core

.NET Core поддерживает использование файлов конфигурации и переменных среды для настройки поведения приложений .NET Core во время выполнения. Конфигурация среды выполнения является удобным вариантом в следующих случаях:

- Вы не владеете исходным кодом приложения или не можете управлять им, поэтому вы не можете задать соответствующие настройки программным способом.

- Вы одновременно запускаете несколько экземпляров приложения в одной системе и хотите настроить оптимальную производительность для каждого экземпляра.

> [!NOTE]
> Работа над этой документацией продолжается. Если вы заметили, что приведенные здесь сведения являются неполными или неточными, [создайте сообщение о проблеме](https://github.com/dotnet/docs/issues), чтобы оповестить нас об этом, или [отправьте запрос на вытягивание](https://github.com/dotnet/docs/pulls) для этой проблемы. Сведения о том, как отправлять запросы на вытягивание для репозитория dotnet/docs, см. в [руководстве участника](/contribute/dotnet/dotnet-contribute).

.NET Core предоставляет следующие механизмы для настройки поведения приложений во время выполнения:

- [Файл runtimeconfig.json](#runtimeconfigjson)

- [Свойства MSBuild](#msbuild-properties)

- [Переменные среды](#environment-variables)

> [!TIP]
> При настройке параметра времени выполнения с помощью переменной среды этот параметр будет применяться ко всем приложениям .NET Core. При настройке параметра времени выполнения в *runtimeconfig.json* или в файле проекта параметр будет действовать только для конкретного приложения.

Значения некоторых параметров конфигурации также можно задать программным способом, вызвав метод <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

Статьи в этом разделе документации упорядочены по категориям, например, [отладка](debugging-profiling.md) и [сборка мусора](garbage-collector.md). В соответствующих случаях параметры конфигурации отображаются для файлов *runtimeconfig.json*, свойств MSBuild, переменных среды и, для перекрестных ссылок, файлов *app.config* для проектов .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Если проект [собран](../tools/dotnet-build.md), в выходном каталоге создается файл *[имя_приложения].runtimeconfig.json*. Если файл *runtimeconfig.template.json* находится в той же папке, что и файл проекта, все параметры конфигурации, которые он содержит, добавляются в файл *[имя_приложения].runtimeconfig.json*. Если вы самостоятельно создаете приложение, разместите все параметры конфигурации в файле *runtimeconfig.template.json*. Если вы только запускаете приложение, вставьте их непосредственно в файл *[имя_приложения].runtimeconfig.json*.

> [!NOTE]
> Файл *[имя_приложения].runtimeconfig.json* будет перезаписан при последующих сборках.

Укажите параметры конфигурации среды выполнения в разделе **configProperties** файлов *runtimeconfig.json*. Этот раздел имеет следующий вид:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Пример файла [имя_приложения].runtimeconfig.json

Если вы помещаете параметры в выходной JSON-файл, вложите их в свойство `runtimeOptions`.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Пример файла runtimeconfig.template.json

Если вы помещаете параметры в шаблон JSON-файла, опустите свойство `runtimeOptions`.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>свойства MSBuild

Некоторые параметры конфигурации времени выполнения можно задать с помощью свойств MSBuild в файле *CSPROJ* или *VBPROJ* в проектах .NET Core типа SDK. Свойства MSBuild имеют приоритет над параметрами, заданными в файле *runtimeconfig.template.json*.

Ниже приведен пример файла проекта в стиле пакета SDK со свойствами MSBuild для настройки поведения во время выполнения:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

Свойства MSBuild для настройки поведения во время выполнения указаны в отдельных статьях для каждой области, например [сборка мусора](garbage-collector.md). Они также перечислены в разделе [Свойства конфигурации среды выполнения](../project-sdk/msbuild-props.md#run-time-configuration-properties) в справочнике по свойствам MSBuild для проектов с SDK.

## <a name="environment-variables"></a>Переменные среды

Переменные среды можно использовать для предоставления некоторых сведений о конфигурации среды выполнения. При настройке параметра времени выполнения с помощью переменной среды этот параметр будет применяться ко всем приложениям .NET Core. Элементы конфигурации, указанные в качестве переменных среды, обычно имеют префикс **COMPlus_** .

Переменные среды можно определить с помощью панели управления Windows, в командной строке или программным способом, вызвав метод <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> в Windows и системах на основе Unix.

В следующих примерах показано, как задать переменную среды в командной строке:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
