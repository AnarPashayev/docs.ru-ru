---
title: Асинхронные операции (службы данных WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: ef41b458a3f5b977eaaff523413c1a8d3b1982a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793423"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Асинхронные операции (службы данных WCF)
При разработке веб-приложений необходимо учитывать наличие большего времени задержки между клиентом и сервером по сравнению с приложениями, выполняющимися во внутренних сетях. Для оптимизации производительности и взаимодействия приложения с пользователем рекомендуется использовать асинхронные методы классов <xref:System.Data.Services.Client.DataServiceContext> и <xref:System.Data.Services.Client.DataServiceQuery%601> при доступе к серверам [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] через Интернет.  
  
 Хотя серверы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] обрабатывают запросы HTTP асинхронно, некоторое методы клиентской библиотеки служб [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] являются синхронными и ожидают завершения всего обмена запрос-ответ до продолжения выполнения. Асинхронные методы клиентской библиотеки служб [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] не ожидают завершения этого обмена и дают возможность приложению в это время поддерживать быстро реагирующий пользовательский интерфейс.  
  
 Асинхронные операции можно выполнять с помощью пары методов на <xref:System.Data.Services.Client.DataServiceContext> и <xref:System.Data.Services.Client.DataServiceQuery%601> классы, которые начинаются с *начать* и *окончания* соответственно. *Начать* методы регистрируют делегат, который вызывается службой по завершении операции. *Окончания* методы должны вызываться в делегате, зарегистрированном для обработки обратного вызова по завершении операций. При вызове *окончания* метод для завершения асинхронной операции, сделайте это с использованием того же <xref:System.Data.Services.Client.DataServiceQuery%601> или <xref:System.Data.Services.Client.DataServiceContext> экземпляр, который использовался для запуска операции. Каждый *начать* альбома `state` параметр, который можно передать объект состояния в обратный вызов. Этот объект состояния извлекается из <xref:System.IAsyncResult> который предоставляется в обратном вызове и используется для вызова соответствующего *окончания* метод для завершения асинхронной операции. Например, если передать экземпляр <xref:System.Data.Services.Client.DataServiceQuery%601> в качестве параметра `state` при вызове применительно к экземпляру метода <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>, тот же экземпляр <xref:System.Data.Services.Client.DataServiceQuery%601> возвращается интерфейсом <xref:System.IAsyncResult>. Этот экземпляр <xref:System.Data.Services.Client.DataServiceQuery%601> затем используется при вызове метода <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> для завершения операции запроса. Дополнительные сведения см. в разделе [Как Выполнение запросов к службе данных в асинхронном](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Клиентские библиотеки, предоставленные в среде .NET Framework для Silverlight, поддерживают только асинхронные операции. Дополнительные сведения см. в разделе [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Клиентские библиотеки .NET Framework поддерживают следующие асинхронные операции.  
  
|Операция|Методы|  
|---------------|-------------|  
|Выполнение запроса <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Выполнение запроса из контекста <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Выполнение пакетного запроса из контекста <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Загрузка связанной сущности в контекст <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Сохранение изменений в объектах контекста <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Вопросы использования потоков в асинхронных операциях  
 В многопоточном приложении делегат, который зарегистрирован в качестве обратного вызова для асинхронной операции не обязательно вызывать в том же потоке, который использовался для вызова *начать* метод, который создает исходный запрос. В приложении, где функция обратного вызова должен вызываться из определенного потока, необходимо выполнить явный маршалинг выполнения *окончания* метод, который обрабатывает ответ, в нужный поток. Например, в приложениях на основе Windows Presentation Foundation (WPF) и на основе Silverlight необходимо выполнить маршалинг ответа обратно в поток пользовательского интерфейса с помощью метода <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> объекта <xref:System.Windows.Threading.Dispatcher>. Дополнительные сведения см. в разделе [запросы к службе данных (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>См. также

- [Библиотека клиентов служб данных WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
