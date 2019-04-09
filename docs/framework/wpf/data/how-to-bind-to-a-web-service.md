---
title: Практическое руководство. Привязка к веб-службе
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 66e91190e68d9610dd95d677edb276e117ec6abb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098584"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="80ead-102">Практическое руководство. Привязка к веб-службе</span><span class="sxs-lookup"><span data-stu-id="80ead-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="80ead-103">В этом примере показано, как выполнить привязку для объектов, возвращенных вызовов метода веб-службы.</span><span class="sxs-lookup"><span data-stu-id="80ead-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ead-104">Пример</span><span class="sxs-lookup"><span data-stu-id="80ead-104">Example</span></span>  
 <span data-ttu-id="80ead-105">В этом примере используется [службы содержимого MSDN или TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) для получения списка языков, поддерживаемых указанного документа.</span><span class="sxs-lookup"><span data-stu-id="80ead-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="80ead-106">Перед вызовом метода веб-службы, необходимо создать ссылку на него.</span><span class="sxs-lookup"><span data-stu-id="80ead-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="80ead-107">Для создания веб-ссылки MTPS службе, используя [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="80ead-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="80ead-108">Откройте проект в [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80ead-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="80ead-109">Из **проекта** меню, щелкните **Add Web Reference**.</span><span class="sxs-lookup"><span data-stu-id="80ead-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="80ead-110">В диалоговом окне задайте **URL-адрес** для [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="80ead-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="80ead-111">Нажмите клавишу **Go** и затем **добавьте ссылку на**.</span><span class="sxs-lookup"><span data-stu-id="80ead-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="80ead-112">Затем вызовите метод веб-службы и задайте <xref:System.Windows.FrameworkElement.DataContext%2A> соответствующий элемент управления или окно, чтобы возвращенный объект.</span><span class="sxs-lookup"><span data-stu-id="80ead-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="80ead-113">**GetContent** метод службы MTPS принимает ссылку на **getContentRequest** объекта.</span><span class="sxs-lookup"><span data-stu-id="80ead-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="80ead-114">Таким образом в следующем примере сначала задается объект запроса:</span><span class="sxs-lookup"><span data-stu-id="80ead-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="80ead-115">После <xref:System.Windows.FrameworkElement.DataContext%2A> задано значение, можно создать привязку к свойствам объекта, <xref:System.Windows.FrameworkElement.DataContext%2A> было присвоено.</span><span class="sxs-lookup"><span data-stu-id="80ead-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="80ead-116">В этом примере <xref:System.Windows.FrameworkElement.DataContext%2A> присваивается **getContentResponse** объект, возвращаемый **GetContent** метод.</span><span class="sxs-lookup"><span data-stu-id="80ead-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="80ead-117">В следующем примере <xref:System.Windows.Controls.ItemsControl> привязывается к и отображает **языкового стандарта** значения **availableVersionsAndLocales** из **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="80ead-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="80ead-118">Сведения о структуре **getContentResponse**, см. в разделе [документации службы содержимого](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="80ead-118">For information about the structure of **getContentResponse**, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ead-119">См. также</span><span class="sxs-lookup"><span data-stu-id="80ead-119">See also</span></span>

- [<span data-ttu-id="80ead-120">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="80ead-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="80ead-121">Общие сведения об источниках привязки</span><span class="sxs-lookup"><span data-stu-id="80ead-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="80ead-122">Обеспечение доступности данных для привязки в XAML</span><span class="sxs-lookup"><span data-stu-id="80ead-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
