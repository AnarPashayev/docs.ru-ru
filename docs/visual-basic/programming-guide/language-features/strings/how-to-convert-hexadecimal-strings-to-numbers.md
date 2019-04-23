---
title: Практическое руководство. Преобразование шестнадцатеричных строк в числа (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: ddb7b39f7a47234c003ca16e1d7ea013e113c108
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773692"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Практическое руководство. Преобразование шестнадцатеричных строк в числа (Visual Basic)

Этот пример преобразует шестнадцатеричную строку в целое число, используя <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> метод.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Для преобразования шестнадцатеричной строки в число

- Используйте <xref:System.Convert.ToInt32(System.String,System.Int32)> метод преобразуемое число, представленное в base-16 в целое число.

  Первый аргумент <xref:System.Convert.ToInt32(System.String,System.Int32)> метод является строка для преобразования. Второй аргумент описывает базовый номер выражается в; шестнадцатеричное является основанием 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Обратите внимание на то, что шестнадцатеричная строка имеет следующие ограничения:

  - Он не может включать `&h` префикс.
  - Он не может включать `_` разделитель разрядов.

  Если префикс или разделителя разрядов отсутствует, вызов <xref:System.Convert.ToInt32(System.String,System.Int32)> вызывает метод <xref:System.FormatException>.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
