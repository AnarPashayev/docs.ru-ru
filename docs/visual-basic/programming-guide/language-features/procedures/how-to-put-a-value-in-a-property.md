---
title: Практическое руководство. Запись значения в свойство
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 7d85066d4678ee2a53b8339bee2db20374482579
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071408"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Практическое руководство. Запись значения в свойство (Visual Basic)

Значение в свойстве сохраняется путем размещения имени свойства в левой части оператора присваивания.  
  
 `Set`Процедура свойства сохраняет значение, но явно не вызывает его по имени. Свойство используется так же, как и переменная. Visual Basic выполняет вызовы процедур свойств.  
  
### <a name="to-store-a-value-in-a-property"></a>Сохранение значения в свойстве  
  
1. Используйте имя свойства в левой части оператора присваивания.  
  
     В следующем примере свойству Visual Basic присваивается значение `TimeOfDay` полдень, неявное вызов его `Set` процедуры.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Если свойство принимает аргументы, следует следовать имени свойства с круглыми скобками, чтобы заключить список аргументов. Если аргументы отсутствуют, можно дополнительно опустить круглые скобки.  
  
3. Поместите аргументы в список аргументов в круглых скобках, разделяя их запятыми. Убедитесь, что аргументы указываются в том же порядке, в котором свойство определяет соответствующие параметры.  
  
4. Значение, созданное в правой части оператора присваивания, хранится в свойстве.  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Процедуры свойств](./property-procedures.md)
- [Параметры и аргументы процедуры](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Различия между свойствами и переменными в Visual Basic](./differences-between-properties-and-variables.md)
- [Практическое руководство. Создание свойства](./how-to-create-a-property.md)
- [Практическое руководство. Объявление свойства со смешанным уровнем доступа](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Практическое руководство. Вызов процедуры свойства](./how-to-call-a-property-procedure.md)
- [Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Практическое руководство. Получение значения из свойства](./how-to-get-a-value-from-a-property.md)
