---
title: Практическое руководство. Создание кнопки принятия в формах Windows Forms с помощью конструктора
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039661"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Практическое руководство. Создание кнопки принятия в формах Windows Forms с помощью конструктора
В любой форме Windows Forms можно назначить <xref:System.Windows.Forms.Button> элемент управления кнопкой Accept («принять»), также называемой кнопкой по умолчанию. Когда пользователь нажимает клавишу ВВОД, нажата кнопка по умолчанию независимо от того, какой элемент управления формы имеет фокус. Исключением является то, что элемент управления с фокусом — это еще одна кнопка — в этом случае будет нажата кнопка с фокусом или многострочное текстовое поле или пользовательский элемент управления, который захватывает клавишу ВВОД.

## <a name="to-designate-the-accept-button"></a>Назначение кнопки «принять»

1. Выберите форму, в которой находится кнопка.

2. В окне **Свойства** задайте для <xref:System.Windows.Forms.Form.AcceptButton%2A> <xref:System.Windows.Forms.Button> свойства формы имя элемента управления.

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Общие сведения об элементе управления Button](button-control-overview-windows-forms.md)
- [Способы активации элемента управления Button в Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Практическое руководство. Реакция на нажатие кнопки Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Практическое руководство. Назначение Windows Forms кнопки "Отмена" с помощью конструктора](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Элемент управления Button](button-control-windows-forms.md)
