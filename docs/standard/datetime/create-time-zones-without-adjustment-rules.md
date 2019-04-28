---
title: Практическое руководство. Создание часовых поясов без правил коррекции
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026553"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Практическое руководство. Создание часовых поясов без правил коррекции

Точные сведения о часовом поясе, которые требуются для приложения может отсутствовать в конкретной системе по следующим причинам:

* Часовой пояс никогда не был определен в локального системного реестра.

* Данные о часовом поясе, изменен или удален из реестра.

* Часовой пояс существует, но не поддерживает точные сведения о коррекции часового пояса для конкретного исторического периода.

В этих случаях можно вызвать <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метод для определения часового пояса, необходимой для приложения. Можно использовать перегрузки этого метода, создаваемого с или без правил коррекции часового пояса. Если часовой пояс поддерживает летнее время, можно определить с помощью либо правила коррекции fixed или с плавающей запятой. (Для определения этих терминов см. в разделе «Терминология часовых поясов» в [Общие сведения о часовом поясе](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Пользовательский часовой пояс, созданных вызывающими <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метод не добавляются в реестр. Вместо этого они может осуществляться только через ссылку на объект, возвращаемый <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> вызова метода.

В этом разделе показано создание часовых поясов без правил коррекции. Чтобы создать часовой пояс, который поддерживает правил коррекции летнего времени, см. в разделе [как: Создание часовых поясов с правилами коррекции](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Создание часовых поясов без правил коррекции

1. Определите отображаемое имя часового пояса.

   Отображаемое имя соответствует стандартному формату, в котором смещение часового пояса от времени в формате UTC, заключенный в круглые скобки и сопровождается строку, которая определяет часовой пояс, один или несколько городов в часовой пояс, или один или несколько из частей в курс заданий или области в часовом поясе.

2. Определите имя для зимнего времени часового пояса. Как правило эта строка также используется как идентификатор часового пояса.

3. Если вы хотите использовать другой идентификатор, чем стандартное имя часового пояса, определите идентификатор часового пояса.

4. Создать экземпляр <xref:System.TimeSpan> объект, который определяет смещение часового пояса от времени UTC. Часовые пояса со временем, которые прибыли позже, чем UTC, имеют положительное смещение. Часовые пояса со временем, предшествующих UTC, имеют отрицательное смещение.

5. Вызовите <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> метод для создания экземпляра нового часового пояса.

## <a name="example"></a>Пример

В следующем примере определяется пользовательский часовой пояс для Моусон, Антарктика, который без правил коррекции.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Строкой, назначенной <xref:System.TimeZoneInfo.DisplayName%2A> свойство осуществляется согласно стандартному формату, в котором смещение часового пояса от времени UTC сопровождается понятное описание часового пояса.

## <a name="compiling-the-code"></a>Компиляция кода

Для этого примера требуются:

* Чтобы добавить в проект ссылку на библиотеку System.Core.dll.

* Что импортируется следующие пространства имен:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>См. также

- [Даты, время и часовые пояса](../../../docs/standard/datetime/index.md)
- [Общие сведения о часовых поясах](../../../docs/standard/datetime/time-zone-overview.md)
- [Практическое руководство. Создание часовых поясов с правилами коррекции](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
