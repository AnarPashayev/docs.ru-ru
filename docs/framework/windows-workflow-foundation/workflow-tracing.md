---
title: Отслеживание рабочих процессов
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: fc27be295cbf0a83b65ff03e36f2aeffeda12db9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557506"
---
# <a name="workflow-tracing"></a><span data-ttu-id="e05e3-102">Отслеживание рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="e05e3-102">Workflow Tracing</span></span>
<span data-ttu-id="e05e3-103">Трассировка рабочего процесса позволяет получать сведения диагностики при помощи прослушивателей трассировки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e05e3-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="e05e3-104">Трассировку можно включить при обнаружении проблемы в работе приложения, а затем снова отключить после разрешения проблемы.</span><span class="sxs-lookup"><span data-stu-id="e05e3-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="e05e3-105">Существует два способа включения трассировки отладки для рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="e05e3-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="e05e3-106">Можно настроить отслеживание в средстве просмотра трассировки событий либо использовать <xref:System.Diagnostics> для отправки событий трассировки в файл.</span><span class="sxs-lookup"><span data-stu-id="e05e3-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="e05e3-107">Включение трассировки отладки в ETW</span><span class="sxs-lookup"><span data-stu-id="e05e3-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="e05e3-108">Для включения трассировки при помощи ETW включите канал отладки в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="e05e3-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="e05e3-109">Перейдите в узел аналитики и журналов отладки в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="e05e3-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="e05e3-110">В представлении в виде дерева в Просмотр событий перейдите к **Просмотр событий->журналы приложений и служб — >Microsoft->Windows->сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="e05e3-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="e05e3-111">Щелкните правой кнопкой мыши **сервер приложений — приложения** и выберите **вид->Показать журналы аналитики и отладки**.</span><span class="sxs-lookup"><span data-stu-id="e05e3-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="e05e3-112">Щелкните правой кнопкой мыши **Отладка** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="e05e3-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="e05e3-113">Когда рабочий процесс запускает отладку и трассы событий выдаются в канал отладки ETW, их можно просмотреть в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="e05e3-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="e05e3-114">Перейдите к разделу **Просмотр событий->журналы приложений и служб->Microsoft->Windows->сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="e05e3-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="e05e3-115">Щелкните правой кнопкой мыши элемент **Отладка** и выберите команду **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="e05e3-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="e05e3-116">Размер буфера аналитической трассировки по умолчанию составляет всего 4 килобайта (КБ). Рекомендуется увеличить этот размер до 32 КБ.</span><span class="sxs-lookup"><span data-stu-id="e05e3-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="e05e3-117">Для этого сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="e05e3-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="e05e3-118">Выполните следующую команду в текущем каталоге платформы (например, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="e05e3-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="e05e3-119">Измените \<bufferSize> значение в файле Windows. ApplicationServer. Applications. Man на 32.</span><span class="sxs-lookup"><span data-stu-id="e05e3-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="e05e3-120">Выполните следующую команду в текущем каталоге платформы (например, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="e05e3-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e05e3-121">Если вы используете клиентский профиль .NET Framework 4, сначала необходимо зарегистрировать манифест ETW, выполнив следующую команду из каталога .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="e05e3-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="e05e3-122">Включение трассировки отладки при помощи System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="e05e3-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="e05e3-123">Эти прослушиватели можно настроить в файле App.config приложения рабочего процесса либо в файле Web.config для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="e05e3-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="e05e3-124">В этом примере a <xref:System.Diagnostics.TextWriterTraceListener> настроен для сохранения данных трассировки в файл MyTraceLog.txt в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="e05e3-124">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e05e3-125">См. также</span><span class="sxs-lookup"><span data-stu-id="e05e3-125">See also</span></span>

- <span data-ttu-id="e05e3-126">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e05e3-126">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="e05e3-127">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e05e3-127">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
