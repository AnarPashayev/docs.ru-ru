---
title: Руководство по программированию на C#. <paramref>
description: Сведения о теге <paramref> в XML. Этот тег позволяет указать, что присутствующее в коде слово является параметром.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381844"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра, на который указывается ссылка. Имя заключается в двойные кавычки (" ").

## <a name="remarks"></a>Примечания

Тег `<paramref>` позволяет указать, что слово в комментариях к коду, например в блоке `<summary>` или `<remarks>`, ссылается на параметр. В XML-файл такое слово может выделяться особым образом, например курсивом или полужирным шрифтом.

Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../language-reference/compiler-options/doc-compiler-option.md).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
