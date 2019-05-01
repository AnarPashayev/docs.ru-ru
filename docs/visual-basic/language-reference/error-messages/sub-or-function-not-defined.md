---
title: Sub или Function не определена (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 397648618ea3764efafb5cff41deaef320bbeff3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982440"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub или Function не определена (Visual Basic)
Объект `Sub` или `Function` должны быть определены для вызываться. Возможные причины этой ошибки:  
  
- Неправильное написание имени процедуры.  
  
- Попытка вызова процедуры из другого проекта без явного добавления ссылки на этот проект в **ссылки** диалоговое окно.  
  
- Задание процедуры, которая не отображается в вызывающую процедуру.  
  
- Объявление процедуры библиотеки динамической компоновки (DLL) для Windows или Macintosh ресурс кода подпрограмму, которая не находится в указанный ресурс библиотеки или кода.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Убедитесь, что имя процедуры указано правильно.  
  
2. Найдите имя проекта, содержащего процедуру, которую требуется вызывать в **ссылки** диалоговое окно. Если он не отображается, нажмите кнопку **Обзор** кнопку, чтобы найти его. Установите флажок слева от имени проекта и нажмите кнопку **ОК**.  
  
3. Проверьте имя процедуры.  
  
## <a name="see-also"></a>См. также

- [Типы ошибок](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Управление ссылками в проекте](/visualstudio/ide/managing-references-in-a-project)
- [Оператор Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Оператор Function](../../../visual-basic/language-reference/statements/function-statement.md)
