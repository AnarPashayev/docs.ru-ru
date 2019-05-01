---
title: Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053812"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic
В этом разделе перечислены распространенные проблемы, связанные с обработчиками событий в наследуемых компонентах.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Код в обработчике событий выполняется дважды для каждого вызова  
  
- Производный обработчик событий не должны содержать [обрабатывает](../../../../visual-basic/language-reference/statements/handles-clause.md) предложение. Метод в базовом классе уже связан с событием и будет запущен. Удалить `Handles` предложение из унаследованного метода.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Если нет унаследованный метод `Handles` ключевое слово, убедитесь, что ваш код не содержит лишних [оператор AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) или все дополнительные методы, которые обрабатывают то же событие.  
  
## <a name="see-also"></a>См. также

- [События](../../../../visual-basic/programming-guide/language-features/events/index.md)
