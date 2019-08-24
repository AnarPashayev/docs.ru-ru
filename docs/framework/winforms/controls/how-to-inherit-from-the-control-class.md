---
title: Практическое руководство. Наследование класса Control
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015856"
---
# <a name="how-to-inherit-from-the-control-class"></a>Практическое руководство. Наследование класса Control

Если необходимо создать полностью настраиваемый элемент управления для использования в форме Windows Forms, следует наследовать от <xref:System.Windows.Forms.Control> класса. При наследовании от <xref:System.Windows.Forms.Control> класса требуется выполнение большего планирования и реализации, а также обеспечивается самый широкий диапазон параметров. При наследовании от <xref:System.Windows.Forms.Control>вы наследуете самые базовые функции, делающие элементы управления работоспособными. Функции, реализованные в <xref:System.Windows.Forms.Control> классе, управляют вводом данных пользователем с помощью клавиатуры и мыши, определяют границы и размер элемента управления, предоставляют дескриптор Windows и обеспечивают обработку сообщений и безопасность. Они не включают оформление (в данном случае отрисовку графического интерфейса элемента управления) или конкретные функции взаимодействия с пользователем. Все эти аспекты необходимо прописывать в пользовательском коде.

## <a name="to-create-a-custom-control"></a>Создание пользовательского элемента управления

1. В Visual Studio создайте новый проект **приложения Windows** или **библиотеки элементов управления Windows** .

2. В меню **Проект** выберите команду **Добавить класс**.

3. В диалоговом окне **Добавление нового элемента** щелкните пункт **Пользовательский элемент управления**.

   В ваш проект будет добавлен новый пользовательский элемент управления.

4. Нажмите клавишу **F7** , чтобы открыть **Редактор кода** для пользовательского элемента управления.

5. Выберите метод, который будет пустым, за исключением вызова <xref:System.Windows.Forms.Control.OnPaint%2A> метода базового класса. <xref:System.Windows.Forms.Control.OnPaint%2A>

6. Измените код, добавив в него пользовательское оформление вашего элемента управления.

   Сведения о написании кода для отрисовки графического интерфейса элементов управления см. в разделе [Рисование и отрисовка пользовательского элемента управления](custom-control-painting-and-rendering.md).

7. Реализуйте необходимые пользовательские методы, свойства или события, которые будут входить в ваш элемент управления.

8. Сохраните и проверьте элемент управления.

## <a name="see-also"></a>См. также

- [Разновидности пользовательских элементов управления](varieties-of-custom-controls.md)
- [Практическое руководство. Наследование от класса UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Практическое руководство. Наследовать от существующих элементов управления Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Практическое руководство. Создание элементов управления для Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Создание элементов управления Windows Forms во время разработки](developing-windows-forms-controls-at-design-time.md)
