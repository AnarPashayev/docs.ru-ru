---
title: Сериализация и десериализация JSON C# с помощью-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180157"
---
# <a name="json-serialization-in-net---overview"></a>Сериализация JSON в .NET — обзор

Пространство имен `System.Text.Json` предоставляет функции для сериализации и десериализации из нотация объектов JavaScript (JSON).

Структура библиотеки подчеркивает высокую производительность и низкое выделение памяти по расширенному набору функций. Встроенная поддержка UTF-8 оптимизирует процесс чтения и записи текста JSON, закодированного как UTF-8, который является наиболее распространенной кодировкой для данных в Интернете и файлах на диске.

Библиотека также предоставляет классы для работы с объектной моделью документов (DOM) в памяти. Эта функция обеспечивает произвольный доступ только для чтения элементов в JSON-файле или строке. 

## <a name="how-to-get-the-library"></a>Как получить библиотеку

* Библиотека встроена в состав общей платформы [.NET Core 3,0](https://aka.ms/netcore3download) .
* Для других целевых платформ установите пакет NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Пакет поддерживает:
  * .NET Standard 2,0 и более поздних версий
  * .NET Framework 4.6.1 и более поздних версий
  * .NET Core 2,0, 2,1 и 2,2

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Использование библиотеки](system-text-json-how-to.md)
* [Исходный код](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Справочник по API](xref:System.Text.Json)
* [Стратегия развития](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Проблемы GitHub в репозитории DotNet/corefx
  * [Обсуждение разработки System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Все проблемы System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Проблемы в System. Text. JSON с меткой JSON-функциональность-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
