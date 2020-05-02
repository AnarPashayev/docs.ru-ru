---
title: Ограничения асинхронного режима
ms.date: 12/13/2019
description: Описывает ограничения асинхронных API и некоторых альтернатив, которые можно использовать вместо них.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75450336"
---
# <a name="async-limitations"></a>Ограничения асинхронного режима

SQLite не поддерживает асинхронный ввод-вывод. Асинхронные методы ADO.NET будут выполняться синхронно в Microsoft.Data.Sqlite. Старайтесь не вызывать их.

Вместо этого используйте [упреждающее протоколирование](https://www.sqlite.org/wal.html) для повышения производительности и параллелизма.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> Упреждающее протоколирование включено по умолчанию для баз данных, созданных с помощью [Entity Framework Core](/ef/core/).
