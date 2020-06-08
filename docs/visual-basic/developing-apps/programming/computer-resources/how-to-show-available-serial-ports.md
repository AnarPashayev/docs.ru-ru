---
title: Практическое руководство. Отображение доступных последовательных портов
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e7a9166f1879ed0850ca893bed307a0318298bbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401827"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Практическое руководство. Отображение доступных последовательных портов в Visual Basic

В этом разделе описывается использование объекта `My.Computer.Ports` для отображения доступных последовательных портов компьютера в Visual Basic.  
  
 Чтобы дать пользователю возможность выбрать используемый порт, имена последовательных портов отображаются в элементе управления <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Пример  

 В этом примере циклически перебираются все строки, которые возвращает свойство `My.Computer.Ports.SerialPortNames`. Эти строки представляют собой имена доступных последовательных портов на компьютере.  
  
 Как правило, пользователь выбирает, какой последовательный порт приложение должно использовать из списка доступных портов. В этом примере имена последовательных портов хранятся в элементе управления <xref:System.Windows.Forms.ListBox>. Дополнительные сведения см. в разделе [Элемент управления ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Этот пример кода также доступен в качестве фрагмента кода IntelliSense. В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**. Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Компиляция кода  

 Для этого примера требуются:  
  
- Ссылка проекта на System.Windows.Forms.dll.  
  
- Доступ к членам пространства имен <xref:System.Windows.Forms>. Добавьте оператор `Imports`, если в коде не используются полные имена членов. Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Ваша форма должна включать элемент управления <xref:System.Windows.Forms.ListBox> с именем `ListBox1`.  
  
## <a name="robust-programming"></a>Отказоустойчивость  

 Необязательно использовать элемент управления <xref:System.Windows.Forms.ListBox> для отображения имен доступных последовательных портов. Вместо него можно использовать <xref:System.Windows.Forms.ComboBox> или другой элемент управления. Если приложение не требует реакции от пользователя, можно использовать для отображения информации элемент управления <xref:System.Windows.Forms.TextBox>.  
  
> [!NOTE]
> Имена портов, возвращаемые свойством `My.Computer.Ports.SerialPortNames`, могут быть неверными при выполнении программы в Windows 98. Во избежание ошибок приложения используйте обработку исключений, например оператор `Try...Catch...Finally` или оператор `Using`, если для открытия портов необходимо использовать их имена.  
  
## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера](how-to-dial-modems-attached-to-serial-ports.md)
- [Практическое руководство. Отправка строк в последовательные порты](how-to-send-strings-to-serial-ports.md)
- [Практическое руководство. Получение строк из последовательных портов](how-to-receive-strings-from-serial-ports.md)
