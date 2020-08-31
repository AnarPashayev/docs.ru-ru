---
title: <include> Руководство по программированию на C#.
description: Сведения о теге <include> XML. Этот тег позволяет указать ссылку на комментарии в другом файле, которые описывают типы и элементы вашего исходного кода.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: d2de8fea17850685668766bc4ec6e64b1be77cce
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053195"
---
# <a name="include-c-programming-guide"></a>\<include> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Параметры

- `filename`

  Имя XML-файла, содержащего документацию. Имя файла может быть квалифицировано с помощью относительного пути к файлу исходного кода. `filename` необходимо заключать в одинарные кавычки (' ').

- `tagpath`

  Путь тегов в `filename`, который ведет к тегу `name`. Путь необходимо заключать в одинарные кавычки (' ').

- `name`

  Спецификатор имени в теге, предшествующий комментариям. `name` будет иметь идентификатор `id`.

- `id`

  Идентификатор тега, который предшествует комментариям. Идентификатор заключается в двойные кавычки (" ").

## <a name="remarks"></a>Примечания

Тег `<include>` позволяет задать ссылку на комментарии в другом файле, которые описывают типы и элементы вашего исходного кода. Этот способ является альтернативой размещению комментариев документации непосредственно в файле исходного кода. Помещая комментарии документации в отдельный файл, вы можете реализовать управление их версиями отдельно от версий исходного кода. В этом случае файл исходного кода может быть извлечен для изменения одним пользователем, а файл документации — другим.

Тег `<include>` использует XML-синтаксис XPath. Сведения об использовании тега `<include>` см. в документации по XPath.

## <a name="example"></a>Пример

В этом примере представлено несколько файлов. Ниже показан первый файл, в котором используется тег `<include>`.

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

Второй файл, *xml_include_tag.doc*, содержит следующие комментарии документации:

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Выходные данные программы

При компиляции классов Test и Test2 с использованием следующей команды в командной строке создаются следующие выходные данные: `-doc:DocFileName.xml.` В Visual Studio параметр "Комментарии XML-документа" задается в области построения конструктора проектов. При обнаружении тега `<include>` компилятор C# выполняет поиск комментариев документации в файле *xml_include_tag.doc* вместо текущего файла исходного кода. После этого компилятор создает файл *DocFileName.xml*, который будет использоваться средствами для работы с документацией, такими как [Sandcastle](https://github.com/EWSoftware/SHFB), для подготовки окончательной версии документации.  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
