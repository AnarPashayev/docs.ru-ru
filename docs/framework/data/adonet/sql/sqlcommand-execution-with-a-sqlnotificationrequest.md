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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Выполнение SqlCommand с помощью SqlNotificationRequest

Объект <xref:System.Data.SqlClient.SqlCommand> можно настроить таким образом, чтобы при изменении выбранных с сервера данных создавалось уведомление, когда результирующий набор повторного запроса будет отличаться от результирующего набора первого запроса. Это полезно в сценариях, в которых нужно создать пользовательские очереди уведомлений или не требуется поддерживать активные объекты.

## <a name="creating-the-notification-request"></a>Создание уведомления о запросах

Объект <xref:System.Data.Sql.SqlNotificationRequest> можно использовать для создания уведомления о запросах, привязав его к объекту `SqlCommand`. После создания запроса объект `SqlNotificationRequest` больше не требуется. Очередь можно запрашивать на наличие уведомлений и реагировать соответствующим образом. Уведомления создаются, даже если приложение закрывается и запускается повторно.

Если выполняется команда со связанным уведомлением, любые изменения в исходном результирующем наборе приводят к отправке сообщения в очередь SQL Server, указанной в запросе уведомления.

Опрос очереди SQL Server и интерпретация сообщения зависят от конкретного приложения. За опрос очереди и реакцию, основанную на содержимом сообщения, отвечает приложение.

> [!NOTE]
> При использовании уведомления о запросах SQL Server вместе с объектом <xref:System.Data.SqlClient.SqlDependency> присвойте очереди собственное имя, а не используйте имя службы по умолчанию.

Для <xref:System.Data.Sql.SqlNotificationRequest> не существует новых клиентских элементов безопасности. Это в основном возможность сервера, который создает специальные права доступа, необходимые пользователю для запроса уведомления.

### <a name="example"></a>Пример

В приведенном ниже фрагменте кода демонстрируется создание объекта <xref:System.Data.Sql.SqlNotificationRequest> и его связь с объектом <xref:System.Data.SqlClient.SqlCommand>.

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

## <a name="see-also"></a>См. также

- [Уведомления запросов в SQL Server](query-notifications-in-sql-server.md)
- [Общие сведения об ADO.NET](../ado-net-overview.md)
