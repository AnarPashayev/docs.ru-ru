---
title: <typeparam> Руководство по программированию на C#.
description: Сведения о теге <typeparam> в XML. Этот тег используется в комментариях к объявлению универсального типа или метода для описания параметра типа.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380791"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Параметры

- `name`

  Имя параметра типа. Имя заключается в двойные кавычки (" ").

- `description`

  Описание параметра типа.

## <a name="remarks"></a>Примечания

Тег `<typeparam>` следует использовать в комментариях к объявлению универсального типа или метода для описания параметра типа. Добавьте такой тег для каждого параметра типа универсального типа или метода.

Дополнительные сведения см. в статье [Универсальные шаблоны](../generics/index.md).

Текст тега `<typeparam>` будет отображаться в IntelliSense, (веб-отчет по комментариям к коду в [окне обозревателя объектов](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)).

Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../language-reference/compiler-options/doc-compiler-option.md).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>См. также

- [справочник по C#](../../language-reference/index.md)
- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
