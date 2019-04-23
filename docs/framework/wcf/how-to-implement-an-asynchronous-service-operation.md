---
title: Практическое руководство. Асинхронная реализация операции службы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 603ee57475b3e7b1af607d49050e3276fd3082d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298660"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="fd43e-102">Практическое руководство. Асинхронная реализация операции службы</span><span class="sxs-lookup"><span data-stu-id="fd43e-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="fd43e-103">В приложениях Windows Communication Foundation (WCF) операции службы можно реализовать асинхронно или синхронно без жесткого задания клиенту как к нему обратиться.</span><span class="sxs-lookup"><span data-stu-id="fd43e-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="fd43e-104">Например асинхронные операции службы могут вызываться синхронно, и синхронные операции службы могут вызываться асинхронно.</span><span class="sxs-lookup"><span data-stu-id="fd43e-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="fd43e-105">Пример, демонстрирующий способы асинхронного вызова операции в клиентском приложении, см. в разделе [как: Асинхронный вызов операций службы](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="fd43e-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="fd43e-106">Дополнительные сведения о синхронных и асинхронных операциях см. в разделе [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) и [синхронные и асинхронные операции](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fd43e-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="fd43e-107">В этом разделе описывается базовая структура асинхронной операции службы, код не завершен.</span><span class="sxs-lookup"><span data-stu-id="fd43e-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="fd43e-108">Полный пример, служба и клиент сторон, см. в разделе [асинхронной](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fd43e-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="fd43e-109">Асинхронная реализация операции службы</span><span class="sxs-lookup"><span data-stu-id="fd43e-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="fd43e-110">В контракте службы объявите пару асинхронных методов в соответствии с рекомендациями по асинхронной разработке для платформы .NET.</span><span class="sxs-lookup"><span data-stu-id="fd43e-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="fd43e-111">Метод `Begin` принимает параметр, объект обратного вызова и объект состояния, а возвращает <xref:System.IAsyncResult?displayProperty=nameWithType>; соответствующий метод `End` принимает <xref:System.IAsyncResult?displayProperty=nameWithType> и возвращает возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="fd43e-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="fd43e-112">Дополнительные сведения об асинхронных вызовах см. в разделе [проектные шаблоны асинхронного программирования](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="fd43e-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="fd43e-113">Пометьте метод `Begin` пары асинхронных методов атрибутом <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> и задайте для свойства <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="fd43e-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="fd43e-114">Например, приведенный ниже код выполняет шаги 1 и 2.</span><span class="sxs-lookup"><span data-stu-id="fd43e-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="fd43e-115">Реализуйте пару методов `Begin/End` в классе своей службы в соответствии с рекомендациями по асинхронной разработке.</span><span class="sxs-lookup"><span data-stu-id="fd43e-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="fd43e-116">Например, в следующем примере кода показана реализация, в которой строка записывается в консоль как в части `Begin`, так и в части `End` асинхронной операции службы, и возвращаемое значение операции `End` возвращается клиенту.</span><span class="sxs-lookup"><span data-stu-id="fd43e-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="fd43e-117">Полный пример кода см. в подразделе "Пример".</span><span class="sxs-lookup"><span data-stu-id="fd43e-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="fd43e-118">Пример</span><span class="sxs-lookup"><span data-stu-id="fd43e-118">Example</span></span>  
 <span data-ttu-id="fd43e-119">В следующих примерах кода показаны:</span><span class="sxs-lookup"><span data-stu-id="fd43e-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="fd43e-120">Интерфейс контракта службы с:</span><span class="sxs-lookup"><span data-stu-id="fd43e-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="fd43e-121">Синхронной операцией `SampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="fd43e-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="fd43e-122">Асинхронной операцией `BeginSampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="fd43e-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="fd43e-123">Асинхронную `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` пары операции.</span><span class="sxs-lookup"><span data-stu-id="fd43e-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="fd43e-124">Реализацией службы с использованием объекта <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd43e-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fd43e-125">См. также</span><span class="sxs-lookup"><span data-stu-id="fd43e-125">See also</span></span>

- [<span data-ttu-id="fd43e-126">Разработка контрактов службы</span><span class="sxs-lookup"><span data-stu-id="fd43e-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="fd43e-127">Синхронные и асинхронные операции</span><span class="sxs-lookup"><span data-stu-id="fd43e-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
