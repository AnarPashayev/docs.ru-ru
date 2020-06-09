---
title: Практическое руководство. Создание базового канала Atom
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 0317e7b42f589b31f5c77b89d26cb46815f13054
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599052"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="35370-102">Практическое руководство. Создание базового канала Atom</span><span class="sxs-lookup"><span data-stu-id="35370-102">How to: Create a Basic Atom Feed</span></span>
<span data-ttu-id="35370-103">Windows Communication Foundation (WCF) позволяет создать службу, предоставляющую канал синдикации.</span><span class="sxs-lookup"><span data-stu-id="35370-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="35370-104">В этом разделе рассматривается процесс создания службы синдикации, предоставляющей веб-канал синдикации Atom.</span><span class="sxs-lookup"><span data-stu-id="35370-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="35370-105">Создание базовой службы синдикации</span><span class="sxs-lookup"><span data-stu-id="35370-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="35370-106">Определите контракт службы с помощью интерфейса, отмеченного атрибутом <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="35370-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="35370-107">Каждая операция, предоставляемая как веб-канал синдикации, должна возвращать объект <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="35370-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="35370-108">Все операции службы, которые применяют атрибут <xref:System.ServiceModel.Web.WebGetAttribute>, сопоставляются с запросами HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="35370-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="35370-109">Чтобы сопоставить операцию с другим методом HTTP, используйте <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="35370-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="35370-110">Дополнительные сведения см. [в разделе как создать базовую веб-службу HTTP WCF](how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="35370-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="35370-111">Реализуйте контракт службы.</span><span class="sxs-lookup"><span data-stu-id="35370-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="35370-112">Создайте объект <xref:System.ServiceModel.Syndication.SyndicationFeed>, затем добавьте автора, категорию и описание.</span><span class="sxs-lookup"><span data-stu-id="35370-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="35370-113">Создайте несколько объектов <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="35370-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="35370-114">Добавьте объекты <xref:System.ServiceModel.Syndication.SyndicationItem> в веб-канал.</span><span class="sxs-lookup"><span data-stu-id="35370-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="35370-115">Возвратите веб-канал.</span><span class="sxs-lookup"><span data-stu-id="35370-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="35370-116">Размещение службы</span><span class="sxs-lookup"><span data-stu-id="35370-116">To host the service</span></span>  
  
1. <span data-ttu-id="35370-117">Создание объекта <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="35370-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="35370-118">Откройте узел службы, загрузите веб-канал из службы, отобразите веб-канал и дождитесь нажатия клавиши ВВОД пользователем.</span><span class="sxs-lookup"><span data-stu-id="35370-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="35370-119">Вызов GetBlog() c HTTP GET</span><span class="sxs-lookup"><span data-stu-id="35370-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="35370-120">Откройте Internet Explorer, введите следующий URL-адрес и нажмите клавишу ВВОД:`http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="35370-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="35370-121">URL-адрес содержит базовый адрес службы ( `http://localhost:8000/BlogService` ), относительный адрес конечной точки и операцию службы для вызова.</span><span class="sxs-lookup"><span data-stu-id="35370-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="35370-122">Вызов GetBlog() из кода</span><span class="sxs-lookup"><span data-stu-id="35370-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="35370-123">Создайте <xref:System.Xml.XmlReader> с базовым адресом и вызываемым методом.</span><span class="sxs-lookup"><span data-stu-id="35370-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="35370-124">Вызовите статический метод <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>, передав ему только что созданный объект <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="35370-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="35370-125">Это вызывает операцию службы и заполняет новый <xref:System.ServiceModel.Syndication.SyndicationFeed> с помощью модуля форматирования, возвращенного от операции службы.</span><span class="sxs-lookup"><span data-stu-id="35370-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="35370-126">Откройте объект веб-канала.</span><span class="sxs-lookup"><span data-stu-id="35370-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="35370-127">Пример</span><span class="sxs-lookup"><span data-stu-id="35370-127">Example</span></span>  
 <span data-ttu-id="35370-128">Ниже приведен полный код этого примера.</span><span class="sxs-lookup"><span data-stu-id="35370-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35370-129">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="35370-129">Compiling the Code</span></span>  
 <span data-ttu-id="35370-130">При компиляции приведенного выше кода задайте ссылки на файлы System.ServiceModel.dll и System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="35370-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35370-131">См. также</span><span class="sxs-lookup"><span data-stu-id="35370-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
