---
title: Руководство по программированию на C#. Инициализация словаря с помощью инициализатора набора
description: Узнайте, как в C# инициализировать словарь с помощью метода Add или инициализатора индекса. В этом примере показаны оба варианта.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: bcb9c5af215ff468812d08e93d37eecc40d745ea
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513085"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Практическое руководство. Инициализация словаря с помощью инициализатора коллекции (Руководство по программированию на C#)

<xref:System.Collections.Generic.Dictionary%602> содержит коллекцию пар "ключ-значение". Ее метод <xref:System.Collections.Generic.Dictionary%602.Add%2A> принимает два параметра: один для ключа, другой — для значения. Для инициализации <xref:System.Collections.Generic.Dictionary%602> или любой коллекции, метод `Add` которой принимает несколько параметров, можно заключить каждый набор параметров в скобки, как показано в приведенном ниже примере. Другой вариант — использовать инициализатор индекса, как показано также в следующем примере.

## <a name="example"></a>Пример

В следующем примере кода <xref:System.Collections.Generic.Dictionary%602> инициализируется экземплярами типа `StudentName`.  Первая инициализация использует метод `Add` с двумя аргументами. Компилятор создает вызов метода `Add` для каждой пары ключа `int` и значения `StudentName`. Вторая инициализация использует общедоступный метод индексатора чтения и записи класса `Dictionary`:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Обратите внимание на две пары фигурных скобок в каждом элементе коллекции в первом объявлении. Во внутренней паре фигурных скобок заключен инициализатор объекта `StudentName`, а во внешней паре — инициализатор пары "ключ-значение", которая будет добавлена в коллекцию `students` <xref:System.Collections.Generic.Dictionary%602>. И наконец, весь инициализатор коллекции для словаря заключается в фигурные скобки. Во второй инициализации левая часть оператора присваивания является ключом, а правая часть — значением, использующим инициализатор объекта для `StudentName`.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Инициализаторы объектов и коллекций](./object-and-collection-initializers.md)
