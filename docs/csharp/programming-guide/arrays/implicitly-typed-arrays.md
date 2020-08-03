---
title: Руководство по программированию на C#. Неявно типизированные массивы
description: Тип неявно типизированного массива в C# определяется на основе элементов в инициализаторе массива. Используйте неявно типизированные массивы в выражениях запросов.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474713"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Неявно типизированные массивы (Руководство по программированию на C#)

Вы можете создать неявно типизированный массив, тип экземпляра которого будет определяться на основе элементов, указанных в инициализаторе массива. В отношении таких массивов действуют правила для неявно типизированных переменных. Дополнительные сведения см. в статье [ Неявно типизированные локальные переменные (руководство по программированию на C#)](../classes-and-structs/implicitly-typed-local-variables.md).

Неявно типизированные массивы обычно используются в выражениях запросов вместе с анонимными типами, а также инициализаторами объектов и коллекций.

В следующих примерах демонстрируется создание неявно типизированного массива:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

Обратите внимание, что в предыдущем примере с неявно типизированными массивами в левой части выражения инициализации не используются квадратные скобки. Также обратите внимание, что массивы массивов инициализируются с помощью выражения `new []`, как и одномерные массивы.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Неявно типизированные массивы в инициализаторах объектов

При создании анонимного типа, содержащего массив, этот массив необходимо неявно типизировать в инициализаторе объекта типа. В следующем примере `contacts` представляет собой неявно типизированный массив анонимных типов, каждый из которых содержит массив с именем `PhoneNumbers`. Обратите внимание, что внутри инициализаторов объектов не используется ключевое слово `var`.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Неявно типизированные локальные переменные](../classes-and-structs/implicitly-typed-local-variables.md)
- [Массивы](./index.md)
- [Анонимные типы](../classes-and-structs/anonymous-types.md)
- [Инициализаторы объектов и коллекций](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ в C#](../../linq/index.md)
