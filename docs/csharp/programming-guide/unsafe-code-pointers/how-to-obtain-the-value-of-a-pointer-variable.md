---
title: Практическое руководство по программированию на C#. Получение значения переменной указателя
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 9a10bcc809f3ecbc9a0fa9b917940b8e030fab8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635102"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Практическое руководство по программированию на C#. Получение значения переменной указателя

Оператор косвенного обращения к указателю позволяет получить переменную в расположении, на которое указывает указатель. Выражение имеет следующую форму, где `p` — это тип указателя:  

```csharp
*p;  
```

Унарный оператор косвенного обращения можно использовать только по отношению к выражениям с типом указателя. Кроме того, его нельзя применять к указателю [void](../../../csharp/language-reference/keywords/void.md).  

Если оператор косвенного обращения применяется к указателю [NULL](../../../csharp/language-reference/keywords/null.md), результат будет зависеть от особенностей реализации.  

## <a name="example"></a>Пример

В следующем примере доступ к переменной типа `char` осуществляется с использованием указателей разных типов. Обратите внимание, что адрес `theChar` может изменяться с каждым запуском из-за изменения физического адреса переменной.  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
**Значение theChar = Z**  
**Адрес theChar = 12F718**  
**Значение pChar = Z**  
**Значение pInt = 90**  

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Типы указателей](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Типы](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Оператор fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
