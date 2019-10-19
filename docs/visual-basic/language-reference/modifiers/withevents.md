---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583044"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Указывает, что одна или несколько объявленных переменных-членов ссылаются на экземпляр класса, который может создавать события.

## <a name="remarks"></a>Заметки

Если переменная определена с помощью `WithEvents`, можно декларативно указать, что метод обрабатывает события переменной с помощью ключевого слова `Handles`.

@No__t_0 можно использовать только на уровне класса или модуля. Это означает, что контекст объявления для переменной `WithEvents` должен быть классом или модулем и не может быть исходным файлом, пространством имен, структурой или процедурой.

Нельзя использовать `WithEvents` в члене структуры.

С помощью `WithEvents` можно объявлять только отдельные переменные (а не массивы).

## <a name="rules"></a>Правила

**Типы элементов.** Необходимо объявить переменные `WithEvents` как переменные объекта, чтобы они могли принимать экземпляры класса. Однако их нельзя объявить как `Object`. Их необходимо объявить в качестве конкретного класса, который может вызывать события.

Модификатор `WithEvents` можно использовать в этом контексте: [оператор Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Пример

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>См. также

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Ключевые слова](../../../visual-basic/language-reference/keywords/index.md)
- [События](../../../visual-basic/programming-guide/language-features/events/index.md)
