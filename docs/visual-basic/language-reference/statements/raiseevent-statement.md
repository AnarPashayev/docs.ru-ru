---
title: Оператор RaiseEvent (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 5d8fd6adf33c992341324e07bcd2ad12986bbdf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783972"
---
# <a name="raiseevent-statement"></a>Оператор RaiseEvent
Вызывает событие, объявленное на уровне модуля в классе, форме или документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Части  
 `eventname`  
 Обязательный. Имя события.  
  
 `argumentlist`  
 Необязательный параметр. Разделенный запятыми список переменных, массивов или выражения. `argumentlist` Аргумент должен быть заключен в круглые скобки. Если аргументы не используются, скобки должен быть опущен.  
  
## <a name="remarks"></a>Примечания  
 Необходимая `eventname` является имя события, объявленного в модуле. Следует правилам именования переменных Visual Basic.  
  
 Если не был объявлен в модуле, в котором вызывается событие, возникает ошибка. В следующем фрагменте кода показано объявление события и процедуры, в котором события.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Нельзя использовать `RaiseEvent` для вызова событий, которые не объявлены явно в модуле. Например, наследуют все формы <xref:System.Windows.Forms.Control.Click> событий из <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, он не может быть изменен с помощью `RaiseEvent` в производной форме. При объявлении `Click` событий в модуле формы, он скрывает формы собственные <xref:System.Windows.Forms.Control.Click> событий. Можно по-прежнему вызывать формы <xref:System.Windows.Forms.Control.Click> событие путем вызова <xref:System.Windows.Forms.Control.OnClick%2A> метод.  
  
 По умолчанию события, определенного в Visual Basic вызывает обработчики событий в порядке, что подключения. Поскольку события могут содержать `ByRef` параметров, процесс, подключившийся позже, может получить параметры, которые были изменены с помощью более ранних обработчика событий. После выполнения обработчиков событий, управление возвращается в подпрограмму, который вызвал событие.  
  
> [!NOTE]
>  Не следует ли создавать события, не являющиеся общими в конструктор класса, в котором они объявлены. Несмотря на то, что такие события не вызывают ошибок времени выполнения, они могут не обнаруживаться связаны обработчики событий. Используйте `Shared` модификатор для создания общего события, если вам нужно вызвать событие из конструктора.  
  
> [!NOTE]
>  События по умолчанию можно изменить, определив пользовательское событие. Для пользовательских событий `RaiseEvent` инструкция вызывает события `RaiseEvent` метода доступа. Дополнительные сведения о пользовательских событиях см. в разделе [оператор Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Пример  
 В следующем примере события используются для выполнения обратного отсчета от 10 до 0 секунд. Код иллюстрирует различные связанные с событиями методы, свойства и инструкций, включая `RaiseEvent` инструкции.  
  
 Класс, который вызывает событие, является источником события, а методы, обрабатывающие события, — обработчиками событий. Источник события может иметь несколько обработчиков для создаваемых им событий. Когда класс создает событие, это событие создается во всех классах, выбранных для обработки событий данного экземпляра объекта.  
  
 В примере также используется форма (`Form1`) с кнопкой (`Button1`) и текстовым полем (`TextBox1`). При нажатии кнопки в первом текстовом поле отображается обратный отсчет от 10 до 0 секунд. По истечении всего времени (10 секунд) в первом текстовом поле отображается надпись Done.  
  
 Код для `Form1` указывает начальное и конечное состояния формы. Он также содержит код, выполняемый при создании событий.  
  
 Чтобы использовать этот пример, откройте новый проект приложения Windows, добавьте кнопку с именем `Button1` и текстовое поле с именем `TextBox1` в главную форму с именем `Form1`. Затем щелкните правой кнопкой мыши форму и нажмите кнопку **Просмотр кода** чтобы открыть редактор кода.  
  
 Добавить `WithEvents` переменной в раздел объявлений `Form1` класса.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Пример  
 Добавьте следующий код в код для `Form1`. Замените все повторяющиеся процедуры, которые могут существовать, такие как `Form_Load`, или `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Нажмите клавишу F5 для запуска примера и нажмите кнопку с надписью **запустить**. Первое текстовое поле начинает обратный отсчет. По истечении всего времени (10 секунд) в первом текстовом поле отображается надпись Done.  
  
> [!NOTE]
>  `My.Application.DoEvents` Метод отличается от обработки событий в точно так же, как и форму. Чтобы разрешить форме обрабатывать события напрямую, можно использовать многопоточность. Дополнительные сведения см. в разделе [управляемых потоков](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>См. также

- [События](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Оператор Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Оператор AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Оператор RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
