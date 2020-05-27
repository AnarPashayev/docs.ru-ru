---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721398"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Операции синтаксического анализа с плавающей запятой больше не завершаются ошибкой и не вызывают исключение OverflowException

Методы синтаксического анализа с плавающей запятой больше не вызывают <xref:System.OverflowException> и не возвращают `false` при синтаксическом анализе строки, числовое значение которой находится вне диапазона типа с плавающей запятой <xref:System.Single> или <xref:System.Double>.

#### <a name="change-description"></a>Описание изменений

В .NET Core 2.2 и более ранних версиях методы <xref:System.Double.Parse%2A?displayProperty=nameWithType> и <xref:System.Single.Parse%2A?displayProperty=nameWithType> вызывают <xref:System.OverflowException> для значений, которые выходят за пределы диапазона соответствующего типа. Методы <xref:System.Double.TryParse%2A?displayProperty=nameWithType> и <xref:System.Single.TryParse%2A?displayProperty=nameWithType> возвращают `false` для строковых представлений числовых значений вне диапазона.

Начиная с .NET Core 3.0 методы <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> и <xref:System.Single.TryParse%2A?displayProperty=nameWithType> больше не завершаются сбоем при анализе числовых строк вне диапазона. Вместо этого методы синтаксического анализа <xref:System.Double> возвращают <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> для значений, превышающих <xref:System.Double.MaxValue?displayProperty=nameWithType>, и <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> — для значений, которые меньше <xref:System.Double.MinValue?displayProperty=nameWithType>. Подобным образом, методы синтаксического анализа <xref:System.Single> возвращают <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> для значений, превышающих <xref:System.Single.MaxValue?displayProperty=nameWithType>, и <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> — для значений, которые меньше <xref:System.Single.MinValue?displayProperty=nameWithType>.

Это изменение было внесено для улучшения соответствия требованиям IEEE 754:2008.

#### <a name="version-introduced"></a>Представленная версия

3.0

#### <a name="recommended-action"></a>Рекомендованное действие

Это изменение может повлиять на код одним из двух способов:

- Код зависит от обработчика <xref:System.OverflowException> для выполнения при переполнении. В этом случае следует удалить оператор `catch` и поместить необходимый код в инструкцию `If`, которая проверяет, является ли <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> или <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>`true`.

- В коде предполагается, что значения с плавающей запятой не являются `Infinity`. В этом случае следует добавить необходимый код для проверки значений с плавающей запятой `PositiveInfinity` и `NegativeInfinity`.

#### <a name="category"></a>Категория

Библиотеки Core .NET

#### <a name="affected-apis"></a>Затронутые API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
