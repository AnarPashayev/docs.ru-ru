---
title: Переключатели трассировки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85a1a017197826717280f53995ed98f26f1d80bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132669"
---
# <a name="trace-switches"></a>Переключатели трассировки
Переключатели трассировки позволяют включать, отключать и фильтровать выходные данные трассировки. Они являются объектами, которые существуют в коде и могут настраиваться извне с помощью файла конфигурации. В .NET Framework существует три типа переключателей трассировки: класс <xref:System.Diagnostics.BooleanSwitch> , класс <xref:System.Diagnostics.TraceSwitch> и класс <xref:System.Diagnostics.SourceSwitch> . Класс <xref:System.Diagnostics.BooleanSwitch> действует как переключатель, включая или отключая различные операторы трассировки. Классы <xref:System.Diagnostics.TraceSwitch> и <xref:System.Diagnostics.SourceSwitch> позволяют включать переключатель трассировки для определенного уровня трассировки, чтобы отображались сообщения <xref:System.Diagnostics.Trace> или <xref:System.Diagnostics.TraceSource> , заданные для данного уровня и всех уровней ниже него. Если этот переключатель отключить, то сообщения трассировки не будут отображаться. Все эти классы являются производными от абстрактного (**MustInherit**) класса **Switch**, как и следует переключателям, разработанным пользователями.  
  
 Переключатели трассировки можно использовать для фильтрации сведений. Например, можно просматривать все сообщения трассировки в модуле доступа к данным, но только сообщения об ошибках в остальной части приложения. В этом случае следует использовать один переключатель трассировки для модуля доступа к данным и еще один переключатель для остальной части приложения. Используя файл конфигурации для настройки соответствующих значений переключателей, можно управлять типами получаемых сообщений трассировки. Дополнительные сведения см. в разделе [Как Создание, инициализация и настройка переключателей трассировки](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Как правило, развертываемое приложение выполняется с отключенными переключателями, чтобы пользователям не приходилось наблюдать большое количество ненужных сообщений трассировки, появляющихся на экране или заполняющих файл журнала во время выполнения приложения. Если во время выполнения приложения возникает проблема, можно остановить приложение, включить переключатели и перезапустить приложение. Затем будут отображены сообщения трассировки.  
  
 Перед использованием переключателя необходимо создать объект переключателя из класса **BooleanSwitch** , класса **TraceSwitch** или класса переключателя, определенного разработчиком. Дополнительные сведения о создании определенных разработчиками переключателей см. в описании класса <xref:System.Diagnostics.Switch> в справочнике по .NET Framework. Затем задается значение конфигурации, определяющее, когда должен использоваться объект переключателя. Затем проверяется настройка объекта переключателя в различных методах трассировки **Trace** (или **Debug**).  
  
## <a name="trace-levels"></a>Уровни трассировки  
 При использовании **TraceSwitch**существуют дополнительные рекомендации. Объект **TraceSwitch** имеет четыре свойства, которые возвращают **логические** значения, указывающие, установлен ли переключатель хотя бы для отдельного уровня:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Уровни позволяют ограничить количество получаемых сведений трассировки только теми, которые необходимы для решения проблемы. Вы указываете нужный уровень детализации в выходных данных трассировки путем установки и настройки переключателей трассировки для соответствующего уровня трассировки. Можно получать сообщения об ошибках, предупреждения, информационные сообщения, подробные сообщения трассировки или совсем не получать сообщения.  
  
 Только вы решаете, какие виды сообщений связать с каждым уровнем. Обычно содержание сообщений трассировки зависит от того, что вы связываете с каждым уровнем, но вы определяете разницу между уровнями. Например, может потребоваться получать подробное описание проблемы на уровне 3 (**Info**), например, но получать только номер ссылки на ошибку на уровне 1 (**Error**). Только вы решаете, какая схема лучше всего подходит для вашего приложения.  
  
 Этим свойствам соответствуют значения от 1 до 4 перечисления **TraceLevel** . В следующей таблице приведены уровни перечисления **TraceLevel** и их значения.  
  
|Перечисляемое значение|Целочисленное значение|Тип отображаемого сообщения (или записываемого в указанный целевой объект)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Нет|  
|Error|1|Только сообщения об ошибках|  
|Предупреждение|2|Предупреждающие сообщения и сообщения об ошибках|  
|Info|3|Информационные сообщения, предупреждения и сообщения об ошибках|  
|Verbose|4|Подробные сообщения, информационные сообщения, предупреждения и сообщения об ошибках|  
  
 Свойства **TraceSwitch** указывают максимальный уровень трассировки для переключателя. То есть сведения трассировки записываются для указанного уровня, а также для всех более низких уровней. Например, если **TraceInfo** имеет значение **true**, то **TraceError** и **TraceWarning** также имеют значение **true** , но **TraceVerbose** может иметь значение **false**.  
  
 Эти свойства доступны только для чтения. Объект **TraceSwitch** автоматически устанавливает их при установке свойства **TraceLevel** . Пример:  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =   
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to   
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>Переключатели, определяемые разработчиком  
 Помимо предоставления **BooleanSwitch** и **TraceSwitch**вы можете определить свои собственные переключатели путем наследования от класса **Switch** и переопределения методов базового класса настраиваемыми методами. Дополнительные сведения о создании определенных разработчиками переключателей см. в описании класса <xref:System.Diagnostics.Switch> в справочнике по .NET Framework.  
  
## <a name="see-also"></a>См. также

- [Прослушиватели трассировки](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Практическое руководство. Добавление операторов трассировки в код приложения](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Трассировка и оборудование приложений](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
