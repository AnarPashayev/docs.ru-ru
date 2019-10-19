---
title: Оператор Resume (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583278"
---
# <a name="resume-statement"></a>Оператор Resume
Возобновляет выполнение по завершении подпрограммы обработки ошибок.  
  
 Мы рекомендуем использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и инструкций `On Error` и `Resume`. Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Части  
 `Resume`  
 Обязательный. Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, вызвавшей ошибку. Если ошибка произошла в вызванной процедуре, выполнение возобновляется с оператора, который последний раз вызывался из процедуры, содержащей подпрограмму обработки ошибок.  
  
 `Next`  
 Необязательный. Если ошибка произошла в той же процедуре, что и обработчик ошибок, выполнение возобновляется с помощью инструкции, следующей за инструкцией, вызвавшей ошибку. Если ошибка произошла в вызываемой процедуре, выполнение возобновляется с помощью инструкции, следующей за инструкцией, которая была вызвана из процедуры, содержащей подпрограмму обработки ошибок (или инструкцию `On Error Resume Next`).  
  
 `line`  
 Необязательный. Выполнение возобновляется в строке, указанной в аргументе Required `line`. Аргумент `line` является меткой или номером строки и должен находиться в той же процедуре, что и обработчик ошибок.  
  
## <a name="remarks"></a>Заметки  
  
> [!NOTE]
> Рекомендуется использовать структурированную обработку исключений в коде, когда это возможно, вместо использования неструктурированной обработки исключений и инструкций `On Error` и `Resume`. Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 При использовании оператора `Resume` в любом месте, кроме в подпрограммы обработки ошибок, возникает ошибка.  
  
 Инструкцию `Resume` нельзя использовать в любой процедуре, содержащей инструкцию `Try...Catch...Finally`.  
  
## <a name="example"></a>Пример  
 В этом примере оператор `Resume` используется для завершения обработки ошибок в процедуре и возобновления выполнения с инструкцией, вызвавшей ошибку. Для иллюстрации использования оператора `Resume` создается ошибка с номером 55.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Сборка:** Библиотека времени выполнения Visual Basic (в Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>См. также

- [Оператор Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Оператор Error](../../../visual-basic/language-reference/statements/error-statement.md)
- [Оператор On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
