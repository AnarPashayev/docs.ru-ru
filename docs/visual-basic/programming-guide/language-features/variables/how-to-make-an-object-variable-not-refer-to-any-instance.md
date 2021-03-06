---
title: Практическое руководство. Как сделать так, чтобы объектная переменная не указывала ни на какой экземпляр
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080259"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Практическое руководство. Как сделать так, чтобы объектная переменная не указывала ни на какой экземпляр (Visual Basic)

Можно разорвать связь объектной переменной с любым экземпляром объекта, задав для него значение [Nothing](../../../language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Отмена связывания объектной переменной с любым экземпляром объекта  
  
- Присвойте переменной значение `Nothing` в операторе присваивания.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Отказоустойчивость  

 Если код пытается получить доступ к члену объектной переменной, для которой задано значение `Nothing` , <xref:System.NullReferenceException> возникает. Если переменная объекта задана как `Nothing` часто или если переменная не инициализирована, рекомендуется заключить доступ к членам в `Try...Catch...Finally` блок.  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  

 При использовании объектной переменной для объектов, содержащих конфиденциальные или конфиденциальные данные, можно присвоить переменной значение, `Nothing` Если вы не работаете с одним из этих объектов. Это снижает вероятность того, что вредоносный код получает доступ к данным.  
  
## <a name="see-also"></a>См. также

- <xref:System.NullReferenceException>
- [Объектные переменные](object-variables.md)
- [Присваивание объектных переменных](object-variable-assignment.md)
- [Nothing](../../../language-reference/nothing.md)
- [Попробуйте... Перехватить... Оператор finally](../../../language-reference/statements/try-catch-finally-statement.md)
