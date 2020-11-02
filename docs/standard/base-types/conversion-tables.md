---
title: Таблицы преобразования типов в .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET], type conversions
- data types [.NET], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: 27578d46a80b0372c6ddc2266a751cd0e6e9aa91
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889456"
---
# <a name="type-conversion-tables-in-net"></a>Таблицы преобразования типов в .NET
Расширяющее преобразование — это преобразование, при котором значение одного типа преобразуется в другой тип равного или большего размера. Сужающее преобразование — это преобразование, при котором значение одного типа преобразуется в другой тип меньшего размера. Таблицы в этом разделе описывают характеристики обоих типов преобразований.  
  
## <a name="widening-conversions"></a>Расширяющие преобразования  
 В следующей таблице описаны расширяющие преобразования, которые можно выполнять без потери данных.  
  
|Type|Можно без потери данных преобразовать в|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Некоторые расширяющие преобразования к типу <xref:System.Single> или <xref:System.Double> могут привести к потере точности. В следующей таблице описаны расширяющие преобразования, которые могут привести к частичной потере данных.  
  
|Type|Можно преобразовать в|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Сужающие преобразования  
 Сужающее преобразование к типу <xref:System.Single> или <xref:System.Double> может привести к потере данных. Если целевой тип не позволяет должным образом выразить порядок величины исходного типа, то результирующий тип будет приравнен к константе `PositiveInfinity` или `NegativeInfinity`. `PositiveInfinity` возникает в результате деления положительного числа на ноль, а также в том случае, если значение типа <xref:System.Single> или <xref:System.Double> превышает значение поля `MaxValue`. `NegativeInfinity` возникает в результате деления отрицательного числа на ноль, а также в том случае, если значение типа <xref:System.Single> или <xref:System.Double> ниже значения поля `MinValue`. Результат преобразования из <xref:System.Double> в <xref:System.Single> может быть равен `PositiveInfinity` или `NegativeInfinity`.  
  
 Сужающее преобразование может также приводить к потере данных и для других типов данных. Тем не менее, если значение преобразуемого типа выходит за пределы диапазона, заданные в полях `MaxValue` и `MinValue` для целевого типа, возникает исключение <xref:System.OverflowException>. Среда выполнения проверяет преобразование, чтобы гарантировать соблюдение ограничений `MaxValue` и `MinValue` для целевого типа. Преобразования, выполняемые с помощью класса <xref:System.Convert?displayProperty=nameWithType>, всегда проверяются подобным образом.  
  
 В следующей таблице приведен список преобразований, порождающих исключение <xref:System.OverflowException> при использовании <xref:System.Convert?displayProperty=nameWithType> или любого преобразования с проверкой, если значение преобразуемого типа находится вне диапазона, определенного для результирующего типа.  
  
|Type|Можно преобразовать в|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Convert?displayProperty=nameWithType>
- [Преобразование типов в .NET](type-conversion.md)
