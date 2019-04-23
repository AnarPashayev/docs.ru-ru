---
ms.openlocfilehash: ffafb0c9e3982dd168f907d32a8f59f96e6040d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234850"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Построение EDMX Entity Framework с помощью Visual Studio 2013 может завершиться ошибкой MSB4062, если используются задачи EntityDeploySplit или EntityClean

|   |   |
|---|---|
|Подробные сведения|Инструменты MSBuild 12.0 (в составе Visual Studio 2013) изменили расположение файлов MSBuild, что привело к недействительности старых файлов целей построения Entity Framework. В результате задачи <code>EntityDeploySplit</code> и <code>EntityClean</code> завершаются ошибкой, так как они не могут найти <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Обратите внимание, что это нарушение возникает вследствие изменения набора инструментов (MSBuild и Visual Studio), а не из-за изменения платформы .NET Framework. Оно происходит только при обновлении средств разработчика, а не просто при обновлении .NET Framework.|
|Предложение|Начиная с .NET Framework 4.6 файлы целей построения Entity Framework предназначены для работы с новым макетом MSBuild. Проблема будет решена после обновления до этой версии. Кроме того, [это](https://stackoverflow.com/a/24249247/131944) решение можно использовать для исправления файлов целей построения напрямую.|
|Область|Значительно|
|Версия|4.5.1|
|Тип|Изменение целевой платформы|
