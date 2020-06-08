---
title: Выполнение в массивах строковых операций, не зависящих от языка и региональных параметров
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 02690f78184ca4f216df7346a84f0266c2dcec99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288606"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Выполнение в массивах строковых операций, не зависящих от языка и региональных параметров

Перегруженные версии методов <xref:System.Array.Sort%2A?displayProperty=nameWithType> и <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> выполняют сортировку с учетом языка и региональных параметров, используя свойство <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Результат, возвращаемый этими методами, зависит от порядка сортировки в параметрах языка и региональных параметров. Чтобы результат не зависел от языка и региональных параметров, используйте перегрузки этого метода, которые принимают параметр `comparer`. Параметр `comparer` указывает реализацию <xref:System.Collections.IComparer>, которую нужно использовать при сравнении элементов массива. Укажите в этом параметре пользовательский инвариантный класс сравнения, который использует <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Пример настраиваемого инвариантного класса сравнения предлагается в подразделе "Использование класса SortedList" статьи [Выполнение в коллекциях строковых операций, не зависящих от языка и региональных параметров](performing-culture-insensitive-string-operations-in-collections.md).

> [!NOTE]
> Если передать **CultureInfo.InvariantCulture** в метод сравнения, сравнение выполняется без учета языка и региональных параметров. Однако при этом не выполняется нелингвистическое сравнение, например для путей к файлам, разделов реестра и переменных среды. Также не поддерживается принятие решений по безопасности на основе результата сравнения. Для нелингвистического сравнения и (или) поддержки принятия решений по безопасности в приложении следует использовать метод сравнения, который принимает значение <xref:System.StringComparison>. Приложение должно передавать <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>См. также раздел

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Выполнение строковых операций, не зависящих от языка и региональных параметров](performing-culture-insensitive-string-operations.md)
