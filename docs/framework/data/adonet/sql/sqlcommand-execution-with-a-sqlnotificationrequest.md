---
title: Выполнение SqlCommand с помощью SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791531"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="a489a-102">Выполнение SqlCommand с помощью SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="a489a-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="a489a-103">Объект <xref:System.Data.SqlClient.SqlCommand> можно настроить таким образом, чтобы при изменении выбранных с сервера данных создавалось уведомление, когда результирующий набор повторного запроса будет отличаться от результирующего набора первого запроса.</span><span class="sxs-lookup"><span data-stu-id="a489a-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="a489a-104">Это полезно в сценариях, в которых нужно создать пользовательские очереди уведомлений или не требуется поддерживать активные объекты.</span><span class="sxs-lookup"><span data-stu-id="a489a-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="a489a-105">Создание уведомления о запросах</span><span class="sxs-lookup"><span data-stu-id="a489a-105">Creating the Notification Request</span></span>

<span data-ttu-id="a489a-106">Объект <xref:System.Data.Sql.SqlNotificationRequest> можно использовать для создания уведомления о запросах, привязав его к объекту `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="a489a-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="a489a-107">После создания запроса объект `SqlNotificationRequest` больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="a489a-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="a489a-108">Очередь можно запрашивать на наличие уведомлений и реагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="a489a-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="a489a-109">Уведомления создаются, даже если приложение закрывается и запускается повторно.</span><span class="sxs-lookup"><span data-stu-id="a489a-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="a489a-110">Если выполняется команда со связанным уведомлением, любые изменения в исходном результирующем наборе приводят к отправке сообщения в очередь SQL Server, указанной в запросе уведомления.</span><span class="sxs-lookup"><span data-stu-id="a489a-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="a489a-111">Опрос очереди SQL Server и интерпретация сообщения зависят от конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="a489a-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="a489a-112">За опрос очереди и реакцию, основанную на содержимом сообщения, отвечает приложение.</span><span class="sxs-lookup"><span data-stu-id="a489a-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="a489a-113">При использовании уведомления о запросах SQL Server вместе с объектом <xref:System.Data.SqlClient.SqlDependency> присвойте очереди собственное имя, а не используйте имя службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a489a-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="a489a-114">Для <xref:System.Data.Sql.SqlNotificationRequest> не существует новых клиентских элементов безопасности.</span><span class="sxs-lookup"><span data-stu-id="a489a-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="a489a-115">Это в основном возможность сервера, который создает специальные права доступа, необходимые пользователю для запроса уведомления.</span><span class="sxs-lookup"><span data-stu-id="a489a-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="a489a-116">Пример</span><span class="sxs-lookup"><span data-stu-id="a489a-116">Example</span></span>

<span data-ttu-id="a489a-117">В приведенном ниже фрагменте кода демонстрируется создание объекта <xref:System.Data.Sql.SqlNotificationRequest> и его связь с объектом <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="a489a-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="a489a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a489a-118">See also</span></span>

- [<span data-ttu-id="a489a-119">Уведомления запросов в SQL Server</span><span class="sxs-lookup"><span data-stu-id="a489a-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="a489a-120">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a489a-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
