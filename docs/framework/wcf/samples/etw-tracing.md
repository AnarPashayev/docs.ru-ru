---
title: Трассировка ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 964c8fbe04f61ebf7a68e1bf36f9efdaab841e7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105434"
---
# <a name="etw-tracing"></a>Трассировка ETW
В этом примере показано, как реализовать сквозную трассировку (E2E) с помощью трассировки событий для Windows (трассировка событий Windows) и `ETWTraceListener`, предоставляемого с этим примером. Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) и включает трассировку событий Windows.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 В этом примере предполагается, что вы знакомы с [трассировка и ведение журнала сообщений](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Каждый источник трассировки в модели трассировки <xref:System.Diagnostics> может иметь несколько прослушивателей трассировки, которые определяют место и способ трассировки данных. Тип прослушивателя определяет формат записи данных трассировки в журнал. В следующем образце кода показано, как добавить прослушиватель в конфигурацию.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Перед использованием этого прослушивателя необходимо запустить сеанс трассировки событий Windows. Этот сеанс может быть запущен с помощью программ Logman.exe или Tracelog.exe. В этот образец включен файл SetupETW.bat, поэтому можно настроить сеанс трассировки событий Windows вместе с файлом CleanupETW.bat для закрытия сеанса и завершения выполнения файла журнала.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела. Дополнительные сведения об этих средствах см. в разделе [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 При использовании ETWTraceListener трассировки заносятся в журнал в двоичных файлах с расширением ETL. Если трассировка ServiceModel включена, все созданные трассировки отображаются в одном и том же файле. Используйте [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) для просмотра файлов журнала ETL и svclog. Средство просмотра создает сквозное представление системы, позволяющее выполнять трассировку сообщения на пути от источника в место назначения и точку потребления.  
  
 Прослушиватель трассировки событий Windows поддерживает циклическое ведение журнала. Чтобы включить эту функцию, перейдите к **запустить**, **запуска** и тип `cmd` для запуска командной консоли. В следующей команде замените параметр `<logfilename>` на имя требуемого файла журнала.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 Коммутаторы `-f` и `-max` необязательны. Они указывают двоичный циклический формат и максимальный размер журнала (1000 МБ) соответственно. Коммутатор `-p` используется для указания поставщика трассировки. В этом примере `"{411a0819-c24b-428c-83e2-26b41091702e}"` является идентификатором GUID для примера поставщика трассировки событий Windows XML.  
  
 Для запуска сеанса введите следующую команду:  
  
```  
Logman start Wcf  
```  
  
 По завершении ведения журнала можно остановить сеанс с помощью следующей команды.  
  
```  
Logman stop Wcf  
```  
  
 При этом создаются двоичные циклические журналы, которые можно обрабатывать с помощью любого средства программирования, включая [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) или Tracerpt.  
  
 Вы также можете просмотреть [циклическая трассировка](../../../../docs/framework/wcf/samples/circular-tracing.md) образец Дополнительные сведения об использовании альтернативного прослушивателя для выполнения циклического ведения журнала.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Для запуска команд RegisterProvider.bat, SetupETW.bat и CleanupETW.bat необходимо использовать учетную запись локального администратора. При использовании [!INCLUDE[wv](../../../../includes/wv-md.md)] или позже необходимо также запустить командную строку с более высоким уровнем привилегий. Чтобы сделать это, щелкните правой кнопкой мыши значок командной строки, а затем нажмите кнопку **Запуск от имени администратора**.  
  
3.  Перед выполнением примера запустите файл RegisterProvider.bat на стороне клиента и сервера. При этом выполняется настройка получаемого файла ETWTracingSampleLog.etl для создания трассировок, которые можно считать с помощью программы Service Trace Viewer. Этот файл можно найти в папке C:\logs. Если эта папка не существует, ее необходимо создать, в противном случае трассировки создаваться не будут. Затем запустите файл SetupETW.bat на клиентском и серверном компьютерах, чтобы начать сеанс трассировки событий Windows. Файл SetupETW.bat можно найти в папке CS\Client.  
  
4.  Чтобы запустить образец в конфигурации с одной или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  По завершении образца запустите файл CleanupETW.bat, чтобы завершить создание файла ETWTracingSampleLog.etl.  
  
6.  Откройте файл ETWTracingSampleLog.etl с помощью программы Service Trace Viewer. Будет предложено сохранить двоичный файл как файл с расширением SVCLOG.  
  
7.  Откройте только что созданный файл с расширением SVCLOG с помощью программы Service Trace Viewer, чтобы просмотреть трассировки событий Windows и трассировки ServiceModel.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>См. также

- [Образцы наблюдения за AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
