---
title: Маршалинг данных при вызове неуправляемого кода
description: Маршалинг данных при вызове платформы в .NET. См. список типов данных, используемых в API-интерфейсах и функциях стиля C и найдите для них эквиваленты управляемых типов .NET.
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: 27045790780c1eef9537bdf7e52deb579e2b467c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904108"
---
# <a name="marshaling-data-with-platform-invoke"></a>Маршалинг данных при вызове неуправляемого кода

Для вызова функций, экспортированных из неуправляемой библиотеки, приложению .NET Framework требуется прототип функции в управляемом коде, представляющий неуправляемую функцию. Чтобы создать прототип, который допускает вызов неуправляемого кода для правильного маршалинга данных, необходимо выполнить указанные ниже действия.

- Примените атрибут <xref:System.Runtime.InteropServices.DllImportAttribute> к статической функции или методу в управляемом коде.

- Замените неуправляемые типы данных на управляемые.

Чтобы создать эквивалентный управляемый прототип путем применения атрибута с необязательными полями и замены неуправляемых типов данных на управляемые, можно использовать документацию, предоставляемую с неуправляемой функцией. Инструкции по применению <xref:System.Runtime.InteropServices.DllImportAttribute> см. в разделе [Использование неуправляемых функций DLL](consuming-unmanaged-dll-functions.md).

В этом разделе содержатся примеры, демонстрирующие способы создания прототипов управляемых функций для передачи аргументов и получения значений от функций, экспортируемых из неуправляемых библиотек. В примерах также демонстрируется использование атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute> и класса <xref:System.Runtime.InteropServices.Marshal> для явного маршалинга данных.

## <a name="platform-invoke-data-types"></a>Типы данных в вызове неуправляемого кода

Ниже перечислены типы данных, используемые в API Windows и в функциях в стиле C. Многие неуправляемые библиотеки содержат функции, передающие эти типы данных в качестве параметров и возвращаемых значений. В третьем столбце представлены соответствующие встроенные типы значений .NET Framework или классы, используемые в управляемом коде. В некоторых случаях типы, перечисленные в таблице, можно заменить на типы того же размера.

|Неуправляемый тип в API Windows|Неуправляемый тип языка C|Управляемый тип|Описание|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Применяется к функции, которая не возвращает значение.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> или <xref:System.UIntPtr?displayProperty=nameWithType>|32 бита в 32-разрядных операционных системах Windows, 64 бита в 64-разрядных операционных системах Windows.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 бит|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 бит|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 бит|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 бита|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 бита|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 бита|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> или <xref:System.Int32?displayProperty=nameWithType>|32 бита|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 бита|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 бита|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|В кодировке ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|В кодировке Юникод.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> или <xref:System.Text.StringBuilder?displayProperty=nameWithType>|В кодировке ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> или <xref:System.Text.StringBuilder?displayProperty=nameWithType>|В кодировке ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> или <xref:System.Text.StringBuilder?displayProperty=nameWithType>|В кодировке Юникод.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> или <xref:System.Text.StringBuilder?displayProperty=nameWithType>|В кодировке Юникод.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 бита|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 бита|

Соответствующие типы в Visual Basic, C# и C++ см. в разделе [Общие сведения о библиотеке классов .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

В примере кода ниже определяются функции библиотеки, предоставляемые Pinvoke.dll. Многие из примеров, описанных в этом разделе, вызывают эту библиотеку.

### <a name="example"></a>Пример

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
