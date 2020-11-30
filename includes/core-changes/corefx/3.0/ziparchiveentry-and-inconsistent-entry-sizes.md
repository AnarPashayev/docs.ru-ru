---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032164"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry больше не обрабатывает архивы с несогласованными размерами записей

Для ZIP-архивов указывается размер в сжатом и несжатом виде в центральном каталоге и в локальном заголовке.  В данных записи также содержится информация о ее размере.  В .NET Core 2.2 и более ранних версиях эти значения не проверялись на согласованность. Начиная с версии .NET Core 3.0 такая проверка выполняется.

#### <a name="change-description"></a>Описание изменений

В .NET Core 2.2 и более ранних версиях метод <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> выполняется успешно, даже если данные в локальном заголовке не совпадают с данными в центральном заголовке ZIP-файла. Данные распаковываются до тех пор, пока не будет достигнут конец сжатого потока, даже если его длина превышает размер несжатого файла, указанный в центральном каталоге или в локальном заголовке.

Начиная с .NET Core 3.0 метод <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> проверяет, чтобы данные в локальном и центральном заголовках о размерах сжатой и несжатой записи были согласованными.  Если в локальном заголовке архива и/или в дескрипторе данных указаны размеры, которые отличаются от размеров в центральном каталоге ZIP-файла, метод вызывает исключение <xref:System.IO.InvalidDataException>. При считывании записи распакованные данные усекаются до размера несжатого файла, который указан в заголовке.

Это изменение позволит <xref:System.IO.Compression.ZipArchiveEntry> корректно представлять размер данных и обеспечит считывание именно такого объема данных.

#### <a name="version-introduced"></a>Представленная версия

3,0

#### <a name="recommended-action"></a>Рекомендованное действие

Переархивируйте все ZIP-файлы, с которыми возникают такие проблемы.

#### <a name="category"></a>Категория

CoreFX

#### <a name="affected-apis"></a>Затронутые API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
