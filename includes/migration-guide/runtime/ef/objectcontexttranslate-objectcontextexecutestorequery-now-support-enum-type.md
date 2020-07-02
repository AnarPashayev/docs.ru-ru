---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620630"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate и ObjectContext.ExecuteStoreQuery теперь поддерживают тип перечисления

#### <a name="details"></a>Подробнее

В .NET Framework 4.0 универсальный параметр <code>T</code> методов <code>ObjectContext.Translate</code> и <code>ObjectContext.ExecuteStoreQuery</code> не мог иметь тип перечисления. Теперь этот сценарий поддерживается.

#### <a name="suggestion"></a>Предложение

Если метод Translate или ExecuteStoreQuery вызывался для типа перечисления в .NET Framework 4.0, возвращалось значение "0". Если такое поведение было желательным, вызовы следовало заменять константой 0 (или его эквивалентом перечисления).

| name    | Значение       |
|:--------|:------------|
| Область   |Пограничный случай|
|Version|4.5|
|Type|Среда выполнения|

#### <a name="affected-apis"></a>Затронутые API

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
