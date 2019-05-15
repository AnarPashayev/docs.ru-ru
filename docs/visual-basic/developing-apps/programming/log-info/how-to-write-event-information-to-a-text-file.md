---
title: Практическое руководство. Запись сведений о событиях в текстовый файл (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: f9abf99a06437f08c65eca69e54760e44a217023
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665756"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Практическое руководство. Запись сведений о событиях в текстовый файл (Visual Basic)
Объекты `My.Application.Log` и `My.Log` можно использовать для записи в журнал информации о событиях, происходящих в приложении. В этом примере показано использование метода `My.Application.Log.WriteEntry` для записи данных трассировки в файл журнала.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Добавление и настройка прослушивателя файлового журнала  
  
1. Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.  
  
     \- или -  
  
     Если файл app.config отсутствует, выполните указанные ниже действия.  
  
    1. В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
    2. В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.  
  
    3. Нажмите кнопку **Добавить**.  
  
2. Найдите раздел `<listeners>` в файле конфигурации приложения.  
  
     Вы найдете раздел \<listeners> в разделе \<source> с именем атрибута "DefaultSource", который вложен в раздел \<system.diagnostics>, который, в свою очередь, вложен в раздел верхнего уровня \<configuration>.  
  
3. Добавьте в этот раздел `<listeners>` следующий элемент:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Найдите раздел `<sharedListeners>` в разделе `<system.diagnostics>` в разделе верхнего уровня `<configuration>`.  
  
5. Добавьте в этот раздел `<sharedListeners>` следующий элемент:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Измените значение атрибута `customlocation` на путь к каталогу журнала.  
  
    > [!NOTE]
    >  Чтобы задать значение свойства прослушивателя, используйте атрибут, имеющий то же имя, что и свойство, но со всеми строчными буквами в имени. Например, атрибуты `location` и `customlocation` задают значения свойств <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> и <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Запись информации о событии в файловый журнал  
  
- Для записи сведений в файловый журнал используйте метод `My.Application.Log.WriteEntry` или `My.Application.Log.WriteException`. Дополнительные сведения см. в разделе [Практическое руководство. Запись сообщений в журнал](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) и [Практическое руководство. Исключения журналов](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     После настройки прослушивателя файлового журнала для сборки он получает все сообщения, которые записываются объектом `My.Application.Log` из этой сборки.  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Работа с журналами приложения](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Практическое руководство. Исплючения журналов](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
