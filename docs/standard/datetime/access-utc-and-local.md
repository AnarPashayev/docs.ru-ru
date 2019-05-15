---
title: Практическое руководство. Доступ к предварительно определенным объектам UTC и объектам местных часовых поясов
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586428"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Практическое руководство. Доступ к предварительно определенным объектам UTC и объектам местных часовых поясов

<xref:System.TimeZoneInfo> Класс предоставляет два свойства <xref:System.TimeZoneInfo.Utc%2A> и <xref:System.TimeZoneInfo.Local%2A>, обеспечивающие доступ к объектам предопределенный часовой пояс. В этом разделе рассматривается порядок работы с объектами <xref:System.TimeZoneInfo>, возвращаемыми этими свойствами.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Получение объекта TimeZoneInfo времени UTC

1. Используйте `static` (`Shared` в Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> свойство для доступа к в формате UTC.

2. Вместо того чтобы <xref:System.TimeZoneInfo> объекты, возвращаемые свойством объектной переменной, по-прежнему получить доступ к времени через <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> свойство.

### <a name="to-access-the-local-time-zone"></a>Получение местного часового пояса

1. Используйте `static` (`Shared` в Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойство для доступа к часового пояса локальной системы.

2. Вместо того чтобы <xref:System.TimeZoneInfo> объекты, возвращаемые свойством объектной переменной, по-прежнему получить доступ к местным часовым поясом <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойство.

## <a name="example"></a>Пример

В следующем коде свойства <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> и <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> используются для преобразования времени из восточного стандартного часового пояса США и Канады, а также для вывода названия часового пояса на консоль.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Следует всегда обращаться к местным часовым поясом <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойства, а не местный часовой пояс в <xref:System.TimeZoneInfo> переменной объекта. Аналогичным образом, следует всегда обращаться к временем через <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> свойство, вместо назначения UTC часовой пояс <xref:System.TimeZoneInfo> переменной объекта. Это предотвращает <xref:System.TimeZoneInfo> переменной объекта путем вызова <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> метод.

## <a name="compiling-the-code"></a>Компиляция кода

Для этого примера требуются:

* Что <xref:System> импорт пространства имен с помощью `using` инструкции (обязательно в коде C#).

## <a name="see-also"></a>См. также

- [Даты, время и часовые пояса](../../../docs/standard/datetime/index.md)
- [Поиск часового пояса, заданного в локальной системе](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Практическое руководство. Создание экземпляра объекта TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
