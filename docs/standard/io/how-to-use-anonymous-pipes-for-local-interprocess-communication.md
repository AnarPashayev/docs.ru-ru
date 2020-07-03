---
title: Практическое руководство. Использование анонимных каналов для локального взаимодействия между процессами
description: Узнайте, как использовать анонимные каналы для локального взаимодействия между процессами на локальном компьютере в .NET. Анонимные каналы требуют меньше ресурсов, чем именованные.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 090a25aea4f280fc2ad00cf7777a501c475dfc66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594807"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="0108f-104">Практическое руководство. Использование анонимных каналов для локального взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="0108f-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="0108f-105">Анонимные каналы обеспечивают межпроцессное взаимодействие на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0108f-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="0108f-106">Они предоставляют меньше возможностей, чем именованные каналы, но требуют меньше ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0108f-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="0108f-107">С помощью анонимных каналов вы можете легко организовать межпроцессное взаимодействие на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0108f-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="0108f-108">Анонимные каналы не подходят для обмена данными по сети.</span><span class="sxs-lookup"><span data-stu-id="0108f-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="0108f-109">Для реализации анонимных каналов используются классы <xref:System.IO.Pipes.AnonymousPipeServerStream> и <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="0108f-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0108f-110">Пример</span><span class="sxs-lookup"><span data-stu-id="0108f-110">Example</span></span>  
 <span data-ttu-id="0108f-111">В следующем примере показано, как отправить строку из родительского процесса в дочерний процесс через анонимные каналы.</span><span class="sxs-lookup"><span data-stu-id="0108f-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="0108f-112">В этом примере создается объект <xref:System.IO.Pipes.AnonymousPipeServerStream> в родительском процессе, в котором параметру <xref:System.IO.Pipes.PipeDirection> задано значение <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="0108f-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="0108f-113">Затем родительский процесс создает дочерний процесс, используя дескриптор клиента для создания объекта <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="0108f-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="0108f-114">В дочернем процессе <xref:System.IO.Pipes.PipeDirection> имеет значение <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="0108f-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="0108f-115">Теперь родительский процесс отправляет предоставленную пользователем строку в дочерний процесс.</span><span class="sxs-lookup"><span data-stu-id="0108f-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="0108f-116">Эта строка выводится в консоль дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="0108f-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="0108f-117">Ниже представлен серверный процесс для этого примера.</span><span class="sxs-lookup"><span data-stu-id="0108f-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="0108f-118">Пример</span><span class="sxs-lookup"><span data-stu-id="0108f-118">Example</span></span>  
 <span data-ttu-id="0108f-119">Ниже представлен клиентский процесс для этого примера.</span><span class="sxs-lookup"><span data-stu-id="0108f-119">The following example shows the client process.</span></span> <span data-ttu-id="0108f-120">Серверный процесс запускает клиентский процесс и передает ему дескриптор клиента.</span><span class="sxs-lookup"><span data-stu-id="0108f-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="0108f-121">Полученному исполняемому файлу в коде клиентского процесса следует присвоить имя `pipeClient.exe` и сохранить его в том же каталоге, где расположен исполняемый файл серверного процесса, прежде чем запускать серверный процесс.</span><span class="sxs-lookup"><span data-stu-id="0108f-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="0108f-122">См. также</span><span class="sxs-lookup"><span data-stu-id="0108f-122">See also</span></span>

- [<span data-ttu-id="0108f-123">Каналы</span><span class="sxs-lookup"><span data-stu-id="0108f-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="0108f-124">Практическое руководство. Использование именованных каналов для сетевого взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="0108f-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
