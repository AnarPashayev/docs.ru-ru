---
title: События подключения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: fd935306a493bf5a20f5cd6cd61a175c02d8bbba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203765"
---
# <a name="connection-events"></a><span data-ttu-id="b2a67-102">События подключения</span><span class="sxs-lookup"><span data-stu-id="b2a67-102">Connection Events</span></span>

<span data-ttu-id="b2a67-103">Все поставщики данных .NET Framework имеют объекты **соединения** с двумя событиями, которые можно использовать для получения информационных сообщений из источника данных или для определения, изменилось ли состояние **соединения** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="b2a67-104">В следующей таблице описаны события объекта **Connection** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="b2a67-105">Событие</span><span class="sxs-lookup"><span data-stu-id="b2a67-105">Event</span></span>|<span data-ttu-id="b2a67-106">Описание</span><span class="sxs-lookup"><span data-stu-id="b2a67-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2a67-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="b2a67-107">**InfoMessage**</span></span>|<span data-ttu-id="b2a67-108">Возникает, когда из источника данных возвращается информационное сообщение.</span><span class="sxs-lookup"><span data-stu-id="b2a67-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="b2a67-109">Информационные сообщения - это сообщения из источника данных, которые не приводят к формированию исключения.</span><span class="sxs-lookup"><span data-stu-id="b2a67-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="b2a67-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="b2a67-110">**StateChange**</span></span>|<span data-ttu-id="b2a67-111">Происходит при изменении состояния **соединения** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="b2a67-112">Работа с событием InfoMessage</span><span class="sxs-lookup"><span data-stu-id="b2a67-112">Working with the InfoMessage Event</span></span>  

 <span data-ttu-id="b2a67-113">При помощи события <xref:System.Data.SqlClient.SqlConnection.InfoMessage> объекта <xref:System.Data.SqlClient.SqlConnection> можно получать предупреждения и информационные сообщения из источника данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b2a67-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="b2a67-114">Ошибки со степенью серьезности от 11 до 16, возвращаемые из источника данных, вызывают формирование исключения.</span><span class="sxs-lookup"><span data-stu-id="b2a67-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="b2a67-115">Однако событие <xref:System.Data.SqlClient.SqlConnection.InfoMessage> также можно использовать, чтобы получать сообщения из источника данных, которые не связаны с ошибками.</span><span class="sxs-lookup"><span data-stu-id="b2a67-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="b2a67-116">В случае с Microsoft SQL Server любая ошибка с серьезностью 10 или меньше считается информационным сообщением, их можно отслеживать при помощи события <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="b2a67-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="b2a67-117">Дополнительные сведения см. в статье [ядро СУБД серьезности ошибок](/sql/relational-databases/errors-events/database-engine-error-severities) .</span><span class="sxs-lookup"><span data-stu-id="b2a67-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="b2a67-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage>Событие получает <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> объект, содержащий в его свойстве **Errors** коллекцию сообщений из источника данных.</span><span class="sxs-lookup"><span data-stu-id="b2a67-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="b2a67-119">Вы можете запросить объекты **ошибок** в этой коллекции, чтобы получить номер ошибки и текст сообщения, а также источник ошибки.</span><span class="sxs-lookup"><span data-stu-id="b2a67-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="b2a67-120">Поставщик данных .NET Framework для SQL Server также указывает сведения о базе данных, хранимой процедуре и номере строки, из которой поступило сообщение.</span><span class="sxs-lookup"><span data-stu-id="b2a67-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b2a67-121">Пример</span><span class="sxs-lookup"><span data-stu-id="b2a67-121">Example</span></span>  

 <span data-ttu-id="b2a67-122">В следующем примере кода показано, как добавлять обработчик для события <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="b2a67-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="b2a67-123">Обработка ошибок как событий InfoMessages</span><span class="sxs-lookup"><span data-stu-id="b2a67-123">Handling Errors as InfoMessages</span></span>  

 <span data-ttu-id="b2a67-124">Событие <xref:System.Data.SqlClient.SqlConnection.InfoMessage> обычно вызывается только для информационных и предупреждающих сообщений, которые отправляются с сервера.</span><span class="sxs-lookup"><span data-stu-id="b2a67-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="b2a67-125">Однако при возникновении фактической ошибки выполнение метода **ExecuteNonQuery** или **ExecuteReader** , инициировавшего операцию сервера, останавливается и создается исключение.</span><span class="sxs-lookup"><span data-stu-id="b2a67-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="b2a67-126">Если требуется продолжить обработку остальных инструкций команды несмотря ни на какие ошибки, выдаваемые сервером, следует задать свойству <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> объекта <xref:System.Data.SqlClient.SqlConnection> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="b2a67-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="b2a67-127">В этом случае соединение вызовет для ошибок событие <xref:System.Data.SqlClient.SqlConnection.InfoMessage>, а не будет формировать исключение и прерывать обработку.</span><span class="sxs-lookup"><span data-stu-id="b2a67-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="b2a67-128">После этого клиентское приложение сможет обработать это событие и отреагировать на условия ошибки.</span><span class="sxs-lookup"><span data-stu-id="b2a67-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2a67-129">Ошибка со степенью серьезности 17 и выше, в результате которой сервер прекращает обработку команды, должна обрабатываться как исключение.</span><span class="sxs-lookup"><span data-stu-id="b2a67-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="b2a67-130">В этом случае исключение формируется независимо от того, как обрабатывается ошибка в событии <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="b2a67-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="b2a67-131">Работа с событием StateChange</span><span class="sxs-lookup"><span data-stu-id="b2a67-131">Working with the StateChange Event</span></span>  

 <span data-ttu-id="b2a67-132">Событие **StateChange** возникает при изменении состояния **соединения** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="b2a67-133">Событие **StateChange** получает, позволяющее <xref:System.Data.StateChangeEventArgs> определить изменение состояния **соединения** с помощью свойств **оригиналстате** и **CurrentState** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="b2a67-134">Свойство **оригиналстате** — это <xref:System.Data.ConnectionState> перечисление, которое указывает состояние **соединения** до его изменения.</span><span class="sxs-lookup"><span data-stu-id="b2a67-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="b2a67-135">**CurrentState** — это <xref:System.Data.ConnectionState> перечисление, указывающее состояние **соединения** после его изменения.</span><span class="sxs-lookup"><span data-stu-id="b2a67-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="b2a67-136">В следующем примере кода событие **StateChange** используется для записи сообщения в консоль при изменении состояния **соединения** .</span><span class="sxs-lookup"><span data-stu-id="b2a67-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2a67-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b2a67-137">See also</span></span>

- [<span data-ttu-id="b2a67-138">Подключение к источнику данных</span><span class="sxs-lookup"><span data-stu-id="b2a67-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="b2a67-139">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2a67-139">ADO.NET Overview</span></span>](ado-net-overview.md)
