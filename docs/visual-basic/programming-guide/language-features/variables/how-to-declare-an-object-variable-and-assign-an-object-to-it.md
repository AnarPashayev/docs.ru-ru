---
title: Практическое руководство. Объявление объектной переменной и присвоение объекта в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: e172d62e5bfadded254d5a5fd25b1dcf2da9634d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663580"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Практическое руководство. Объявление объектной переменной и присвоение объекта в Visual Basic
Объявите переменную [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) , указав `As Object` в [оператор Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Чтобы присвоить объект на такую переменную, поместите его после знака равенства (`=`) в предложении назначения инструкции или инициализации.  
  
## <a name="example"></a>Пример  
 В следующем примере объявляется `Object` переменной и назначает текущий экземпляр.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Назначение и объявление можно объединять путем инициализации переменной при ее объявлении. Следующий пример является эквивалентом предыдущего примера.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
- ссылка на пространство имен <xref:System>.  
  
- Класс, структура или модуль, в который помещаются `Dim` инструкции.  
  
- Процедура, в который помещаются оператора присваивания.  
  
## <a name="see-also"></a>См. также

- [Объявление переменных](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Объектные переменные](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Объявление объектной переменной](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Тип данных Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Оператор Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Вывод локального типа](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Оператор Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
