---
title: Справочник по C#. Ключевое слово base
ms.custom: seodec18
description: Сведения о ключевом слове base, которое используется для доступа к членам базового класса из производного класса в C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 2ef0d07aed595fa630459171482e0b0849aed877
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401598"
---
# <a name="base-c-reference"></a>base (Справочник по C#)

Ключевое слово `base` используется для доступа к членам базового из производного класса в следующих случаях:

- Вызов метода базового класса, который был переопределен другим методом.

- Определение конструктора базового класса, который должен вызываться при создании экземпляров производного класса.

Доступ к базовому классу разрешен только в конструкторе, методе экземпляра или методе доступа к свойству экземпляра.

Использование ключевого слова `base` в статическом методе является недопустимым.

Доступ осуществляется к базовому классу, заданному в объявлении класса. Например, если указать `class ClassB : ClassA`, члены ClassA будут доступны из ClassB независимо от базового класса ClassA.

## <a name="example"></a>Пример

В приведенном ниже примере метод `Getinfo` присутствует как в базовом классе `Person`, так и в производном классе `Employee`. С помощью ключевого слова `base` можно вызвать метод `Getinfo` базового класса из производного класса.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Дополнительные примеры см. в разделах [new](new-modifier.md), [virtual](virtual.md) и [override](override.md).

## <a name="example"></a>Пример

В этом примере показано, как задать конструктор базового класса, вызываемый при создании экземпляров производного класса.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Ключевые слова в C#](../../../csharp/language-reference/keywords/index.md)
- [this](../../../csharp/language-reference/keywords/this.md)
