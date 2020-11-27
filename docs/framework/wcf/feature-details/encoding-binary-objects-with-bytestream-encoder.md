---
title: Кодирование двоичных объектов при помощи кодировщика ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: cc63cb8de1e245c3b58fb69819e59cb815b777d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276741"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="c3a4f-102">Кодирование двоичных объектов при помощи кодировщика ByteStream</span><span class="sxs-lookup"><span data-stu-id="c3a4f-102">Encoding Binary Objects with ByteStream Encoder</span></span>

<span data-ttu-id="c3a4f-103">Отправка и получение необработанных двоичных данных с помощью Windows Communication Foundation (WCF) настраивается с использованием <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="c3a4f-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="c3a4f-104">Архитектура кодировщика сообщений потока байтов</span><span class="sxs-lookup"><span data-stu-id="c3a4f-104">Byte Stream Message Encoder Architecture</span></span>  

 <span data-ttu-id="c3a4f-105">Кодировщик двоичных сообщений, используемый WCF, не имеет средства для обработки, проверки или идентификации базовых двоичных данных в сообщении.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="c3a4f-106">Производится кодирование пакета данных в XML, отправка, получение и декодирование.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="c3a4f-107">Кодировщик обрабатывает данные после передачи транспортной подсистеме, до передачи сообщения в очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="c3a4f-108">С технической точки зрения двоичный кодировщик упаковывает данные сообщения в элементы `<binary>` и удаляет эти элементы после его получения.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="c3a4f-109">Использование кодировщика сообщений потока байтов</span><span class="sxs-lookup"><span data-stu-id="c3a4f-109">Using the Byte Stream Message Encoder</span></span>  

 <span data-ttu-id="c3a4f-110">В следующем примере показан контракт службы, реализующий кодировщик сообщений потока байтов.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="c3a4f-111">В следующем примере показан вызов службы.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="c3a4f-112">Если служба реализует инфраструктуру сообщения (например, маршрутизатора), то сообщение обрабатывается без проверки и любого другого взаимодействия с сообщением, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="c3a4f-113">Сценарии</span><span class="sxs-lookup"><span data-stu-id="c3a4f-113">Scenarios</span></span>  

 <span data-ttu-id="c3a4f-114">Кодировщик байтового потока полезен в следующих сценариях.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="c3a4f-115">Передача изображения JPEG между компьютерами с помощью WCF.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="c3a4f-116">В данном сценарии изображение поступает через этот транспорт из внешнего источника и отправляемые данные представляют собой необработанные байты, из которых состоит изображение.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="c3a4f-117">Служба получает двоичные данные и отображает изображение.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-117">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="c3a4f-118">Чтение данных из очереди сообщений и их обработка.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="c3a4f-119">Сообщение считывается из диспетчера очереди сообщений и передается по каналу очереди сообщений для обработки.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="c3a4f-120">Канал очереди сообщений будет работать как диспетчер очереди в стеке канала WCF.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="c3a4f-121">В случае если сообщение отправляется по каналу очереди сообщений, отправитель не управляет байтами, получаемыми от диспетчера очереди.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="c3a4f-122">Если принимающий процесс не может считывать необработанные байты, полученное сообщение будет рассматриваться как имеющее неправильный формат и не будет обработано. Предполагается, что принимающий процесс умеет преобразовывать полученные байты в поддерживаемый формат.</span><span class="sxs-lookup"><span data-stu-id="c3a4f-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
