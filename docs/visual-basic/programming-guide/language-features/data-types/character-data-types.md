---
title: Символьные типы данных (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840982"
---
# <a name="character-data-types-visual-basic"></a>Символьные типы данных (Visual Basic)
Visual Basic предоставляет *символьные типы данных* для работы с символами печати и отображения. Оба они работают с символами Юникода, `Char` содержит один символ, тогда как `String` содержит неопределенное число символов.  
  
 Таблицу, отображающую side-by-side сравнение типов данных Visual Basic, см. в разделе [типы данных](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Тип char  
 `Char` Тип данных — это символ Юникода (16-разрядная версия) размером 2 байта. Если переменная всегда хранит ровно один символ, он объявляется как `Char`. Пример:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Каждое возможное значение в `Char` или `String` переменная является *кодовую точку*, или код знака в кодировке Юникод. Символы Юникода включают базовый набор символов ASCII, различные другие буквы алфавита, диакритические знаки, символы валют, дроби, диакритические знаки и математические и технические символы.  
  
> [!NOTE]
>  Набор символов Юникода кодовые точки от D800 до DFFF (55296 до 55551) для Резервы *суррогатные пары*, который требует два 16-разрядных значений для представления одну кодовую точку. Объект `Char` переменной не может удерживать суррогатную пару и `String` использует две позиции для хранения таких пар.  
  
 Дополнительные сведения см. в разделе [тип данных Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Тип строки  
 `String` Тип данных представляет собой последовательность из нуля или более символов Юникода (16-разрядная версия) размером 2 байта. Если переменная может содержать неограниченное количество символов, объявите его как `String`. Пример:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Дополнительные сведения см. в разделе [строковый тип данных](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>См. также

- [Простые типы данных](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Составные типы данных](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Преобразование типов в Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Устранение неполадок, связанных с типами данных](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Знаки типов](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
