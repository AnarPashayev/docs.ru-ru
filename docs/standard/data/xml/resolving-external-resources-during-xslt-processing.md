---
title: Разрешение внешних ресурсов в ходе обработки XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: d38aea1a54c93b00ec14c6aac7ed11ceba288f7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291504"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="e9b2d-102">Разрешение внешних ресурсов в ходе обработки XSLT</span><span class="sxs-lookup"><span data-stu-id="e9b2d-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="e9b2d-103">Во время XSLT-преобразования может понадобиться несколько раз разрешать внешние ресурсы.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="e9b2d-104">Использование класса XmlResolver</span><span class="sxs-lookup"><span data-stu-id="e9b2d-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="e9b2d-105">Класс <xref:System.Xml.XmlResolver> используется для разрешения внешних ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="e9b2d-106">В следующей таблице описывается, когда класс <xref:System.Xml.XmlResolver> участвует в XSLT-обработке.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="e9b2d-107">Задача XSLT</span><span class="sxs-lookup"><span data-stu-id="e9b2d-107">XSLT task</span></span>|<span data-ttu-id="e9b2d-108">Зачем используется класс XmlResolver</span><span class="sxs-lookup"><span data-stu-id="e9b2d-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="e9b2d-109">Компиляция таблицы стилей</span><span class="sxs-lookup"><span data-stu-id="e9b2d-109">Compile the style sheet.</span></span>|<span data-ttu-id="e9b2d-110">Разрешение URI таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="e9b2d-111">\- и -</span><span class="sxs-lookup"><span data-stu-id="e9b2d-111">-and-</span></span><br /><br /> <span data-ttu-id="e9b2d-112">Разрешение URI-ссылок в любых элементах `xsl:import` или `xsl:include`.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="e9b2d-113">Выполнение таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-113">Execute the style sheet.</span></span>|<span data-ttu-id="e9b2d-114">Разрешение URI документа контекста.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="e9b2d-115">\- и -</span><span class="sxs-lookup"><span data-stu-id="e9b2d-115">-and-</span></span><br /><br /> <span data-ttu-id="e9b2d-116">Разрешение URI-ссылок в любых функциях XSLT `document()`.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="e9b2d-117">Методы <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> и <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> включают в себя перегружаемые, принимающие объект <xref:System.Xml.XmlResolver> в качестве одного из аргументов.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="e9b2d-118">Если <xref:System.Xml.XmlResolver> не указан, используется <xref:System.Xml.XmlUrlResolver> по умолчанию без учетных данных.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="e9b2d-119">Следующий список описывает, когда может потребоваться указать объект <xref:System.Xml.XmlResolver>:</span><span class="sxs-lookup"><span data-stu-id="e9b2d-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="e9b2d-120">Если процессу XSLT требуется доступ к сетевому ресурсу, требующему проверки подлинности, можно использовать <xref:System.Xml.XmlResolver> с необходимыми учетными данными.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="e9b2d-121">Если необходимо ограничить ресурсы, к которым имеет доступ процесс XSLT, можно использовать <xref:System.Xml.XmlSecureResolver> с надлежащим набором разрешений.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="e9b2d-122">Использовать класс <xref:System.Xml.XmlSecureResolver> рекомендуется, если вам необходимо открыть ресурс, которым вы не управляете или к которому нет доверия.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="e9b2d-123">Если необходимо настроить поведение особым образом, можно реализовать собственный класс <xref:System.Xml.XmlResolver> и использовать его для разрешения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="e9b2d-124">Если необходимо убедиться в отсутствии доступа к внешним ресурсам, можно указать `null` в качестве значения аргумента <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9b2d-125">Пример</span><span class="sxs-lookup"><span data-stu-id="e9b2d-125">Example</span></span>  
 <span data-ttu-id="e9b2d-126">В следующем примере компилируется таблица стилей, которая хранится на сетевом ресурсе.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="e9b2d-127">Объект <xref:System.Xml.XmlUrlResolver> задает учетные данные, необходимые для доступа к таблице стилей.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e9b2d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="e9b2d-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="e9b2d-129">Преобразования XSLT</span><span class="sxs-lookup"><span data-stu-id="e9b2d-129">XSLT Transformations</span></span>](xslt-transformations.md)
