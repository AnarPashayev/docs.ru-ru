---
title: Справочник по C#. Таблица форматирования числовых результатов
ms.custom: seodec18
description: Сведения об использовании строк стандартных числовых форматов C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 0f2b5bc54a0e9055d64a95dc229eaadf66687b43
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421970"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Таблица форматирования числовых результатов (справочник по C#)

В следующей таблице приводятся описатели поддерживаемых форматов для форматирования числовых результатов. Форматированный результат в последнем столбце соответствует формату "en-US" (<xref:System.Globalization.CultureInfo>).

|Описатель формата|Описание|Примеры|Результат|  
|----------------------|-----------------|--------------|------------|  
|C или c|Валюта|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D или d|Десятичное число|`string s = $"{25:D5}";`|00025|  
|E или e|Экспоненциальный|`string s = $"{250000:E2}";`|2.50E+005|  
|F или f|С фиксированной запятой|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G или g|Общие|`string s = $"{2.5:G}";`|2.5|  
|N или n|Numeric|`string s = $"{2500000:N}";`|2,500,000.00|  
|P или p|Процент|`string s = $"{0.25:P}";`|25.00%|  
|R или r|Приемо-передача|`string s = $"{2.5:R}";`|2.5|  
|X или x|Шестнадцатеричный|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Примечания

Для создания строки формата используйте описатель формата. Строка формата имеет вид `Axx`:

- где `A` — это описатель формата, который управляет типом форматирования, применяемым к числовому значению;
- а `xx` — указатель точности, который влияет на количество цифр в форматированном выводе. Значение описателя точности находится в диапазоне от 0 до 99.

Описатели десятичного ("D" или "d") и шестнадцатеричного форматов ("X" или "x") поддерживаются только для целочисленных типов. Описатель формата обратного преобразования ("R" или "r") поддерживается только для типов <xref:System.Single>, <xref:System.Double> и <xref:System.Numerics.BigInteger>.

Строки стандартных числовых форматов поддерживаются в следующих сценариях.

- Некоторые перегрузки метода `ToString` для всех числовых типов. Например, можно задать строку числового формата для методов <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> и <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

- [Функция составного форматирования](../../../standard/base-types/composite-formatting.md) .NET, которая поддерживается методом <xref:System.String.Format%2A?displayProperty=nameWithType>, например.

- [Интерполированные строки](../tokens/interpolated.md).

Дополнительные сведения см. в статье [Строки стандартных числовых форматов](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Типы форматирования](../../../standard/base-types/formatting-types.md)
- [Составное форматирование](../../../standard/base-types/composite-formatting.md)
- [Интерполяция строк](../tokens/interpolated.md)
- [string](string.md)
