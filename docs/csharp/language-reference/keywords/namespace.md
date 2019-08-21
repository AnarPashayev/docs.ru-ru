---
title: Ключевое слово namespace. Справочник по C#
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 8cc1d1461a33ab94f8ae399d6ff40f26eaf7f74a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039448"
---
# <a name="namespace-c-reference"></a>namespace (Справочник по C#)

Ключевое слово `namespace` используется для объявления области действия, которая содержит набор связанных объектов. Пространство имен можно использовать для организации элементов кода и для создания глобально уникальных типов.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Примечания

В пространстве имен можно объявить ноль или больше следующих типов:

- другое пространство имен

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

Независимо от того, было ли пространство имен объявлено явным образом в исходном файле на языке C#, компилятор добавляет пространство имен по умолчанию. Это безымянное пространство имен, иногда называемое глобальным пространством имен, существует в каждом файле. Любой идентификатор в глобальном пространстве имен доступен для использования в именованном пространстве имен.

Пространства имен неявно имеют общий доступ, и это невозможно изменить. Описание модификаторов доступа, которые можно назначить элементам в пространстве имен, см. в разделе [Модификаторы доступа](access-modifiers.md).

Пространство имен можно определить в двух или нескольких объявлениях. Например, в следующем примере два класса определяются в качестве части пространства имен `MyCompany`:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Пример

В следующем примере показано, как можно вызвать статический метод вложенного пространства имен.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в статье [Пространства имен](~/_csharplang/spec/namespaces.md) в разделе [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Ключевые слова C#](index.md)
- [using](using-directive.md)
- [using static](using-static.md)
- [Квалификатор псевдонима пространства имен `::`](../operators/namespace-alias-qualifier.md)
- [Пространства имен](../../programming-guide/namespaces/index.md)
