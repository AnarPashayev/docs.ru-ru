---
title: Конструктор <name> не может вызывать сам себя
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: f40319cde8388b17e27cfaec2117ebd519ebd4ff
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160949"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a>BC30298: конструктор " \<name> " не может вызвать сам себя

`Sub New`Процедура в классе или структуре вызывает саму себя.

 Назначение конструктора заключается в инициализации экземпляра класса или структуры при первом создании. Класс или структура может иметь несколько конструкторов, при условии, что все они имеют разные списки параметров. Конструктору разрешено вызывать другой конструктор для выполнения его функциональных возможностей в дополнение к собственным. Однако конструктор не имеет смысла вызывать сам себя, и на самом деле это может привести к бесконечной рекурсии, если это разрешено.

 **Идентификатор ошибки:** BC30298

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Проверьте список параметров вызываемого конструктора. Он должен отличаться от конструктора, выполняющего вызов.

2. Если вы не планируете вызывать другой конструктор, удалите `Sub New` вызов полностью.

## <a name="see-also"></a>См. также

- [Время существования: создание и уничтожение объектов](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
