---
title: Использование синхронного сокета клиента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: 339f9c9d8b25f6deef4cc77f60c26b7b5d017ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105785"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="bcb1b-102">Использование синхронного сокета клиента</span><span class="sxs-lookup"><span data-stu-id="bcb1b-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="bcb1b-103">Синхронный сокет клиента приостанавливает работу программы, пока выполняется сетевая операция.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="bcb1b-104">Синхронные сокеты не подходят для приложений, которые сильно загружают сеть своими операциями, но они могут обеспечивать простой доступ к сетевым службам для других приложений.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="bcb1b-105">Для отправки данных передайте массив байтов в один из методов отправки данных класса <xref:System.Net.Sockets.Socket> (<xref:System.Net.Sockets.Socket.Send%2A> и <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="bcb1b-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="bcb1b-106">В приведенном же примере строка кодируется в буфер массива байтов с помощью свойства <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>, после чего буфер передается сетевому устройству с помощью метода **Send**.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="bcb1b-107">Метод **Send** возвращает количество байтов, отправленных сетевому устройству.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="bcb1b-108">Метод **Send** удаляет байты из буфера и помещает их в очередь сетевого интерфейса для отправки сетевому устройству.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="bcb1b-109">Сетевой интерфейс может отправлять данные не сразу, однако он отправит их рано или поздно, если подключение не будет закрыто стандартным образом с помощью метода <xref:System.Net.Sockets.Socket.Shutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="bcb1b-110">Для получения данных от сетевого устройства необходимо передать буфер в один из методов приема данных класса **Socket** (<xref:System.Net.Sockets.Socket.Receive%2A> и <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="bcb1b-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="bcb1b-111">Синхронные сокеты приостанавливают работу приложения до тех пор, пока все байты не будут получены из сети или пока сокет не будет закрыт.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="bcb1b-112">В приведенном ниже примере данные принимаются из сети, а затем выводятся в консоли.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="bcb1b-113">В нем предполагается, что данные поступают из сети в виде текста в кодировке ASCII.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="bcb1b-114">Метод **Receive** возвращает количество байтов, полученных из сети.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 <span data-ttu-id="bcb1b-115">Если сокет больше не нужен, его следует освободить, вызвав метод <xref:System.Net.Sockets.Socket.Shutdown%2A>, а затем метод **Close**.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="bcb1b-116">В приведенном ниже примере освобождается объект **Socket**.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="bcb1b-117">Перечисление <xref:System.Net.Sockets.SocketShutdown> включает в себя константы, которые определяют, должен ли сокет быть закрыт для отправки данных, их получения или и того, и другого.</span><span class="sxs-lookup"><span data-stu-id="bcb1b-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcb1b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="bcb1b-118">See also</span></span>

- [<span data-ttu-id="bcb1b-119">Использование асинхронных сокетов клиента</span><span class="sxs-lookup"><span data-stu-id="bcb1b-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="bcb1b-120">прослушивание с помощью сокетов</span><span class="sxs-lookup"><span data-stu-id="bcb1b-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
- [<span data-ttu-id="bcb1b-121">Пример синхронного сокета клиента</span><span class="sxs-lookup"><span data-stu-id="bcb1b-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
