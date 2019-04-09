---
title: Пример службы AJAX с JSON и XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e5f2838575b212f6b95fd01b469d771017ef534c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207491"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="09380-102">Пример службы AJAX с JSON и XML</span><span class="sxs-lookup"><span data-stu-id="09380-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="09380-103">В этом примере показано, как использовать Windows Communication Foundation (WCF) для создания служб асинхронных сценариев JavaScript и XML (AJAX), возвращающих нотацию объектов JavaScript (JSON) или XML-данные.</span><span class="sxs-lookup"><span data-stu-id="09380-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="09380-104">К службе AJAX можно обращаться с помощью кода JavaScript из веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="09380-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="09380-105">Этот пример основан на [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) образца.</span><span class="sxs-lookup"><span data-stu-id="09380-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="09380-106">В отличие от других примеров AJAX, в данном примере не используется ASP.NET AJAX и управление <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="09380-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="09380-107">Дополнительная настройка службы WCF AJAX может осуществляться из любой HTML-страницы через JavaScript, и этот сценарий показан здесь.</span><span class="sxs-lookup"><span data-stu-id="09380-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="09380-108">Пример использования WCF с ASP.NET AJAX, см. в разделе [образцы AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="09380-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>
  
 <span data-ttu-id="09380-109">В данном разделе показано переключение типа отклика операции между JSON и XML.</span><span class="sxs-lookup"><span data-stu-id="09380-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="09380-110">Данная функциональность доступна независимо от того, настроена служба для доступа через клиентскую страницу ASP.NET AJAX или через HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="09380-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09380-111">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="09380-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>
  
<span data-ttu-id="09380-112">Чтобы разрешить использование клиентов, не являющихся клиентами ASP.NET AJAX, используйте <xref:System.ServiceModel.Activation.WebServiceHostFactory> (а не <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) в SVC-файле.</span><span class="sxs-lookup"><span data-stu-id="09380-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <xref:System.ServiceModel.Activation.WebServiceHostFactory> <span data-ttu-id="09380-113">Добавляет <xref:System.ServiceModel.Description.WebHttpEndpoint> стандартной конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="09380-113">adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="09380-114">Конечная точка настраивается с пустым адресом относительно SVC-файла; Это означает, что адресом службы является `http://localhost/ServiceModelSamples/service.svc`, без дополнительных суффиксов, за исключением имени операции.</span><span class="sxs-lookup"><span data-stu-id="09380-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="09380-115">Следующий раздел в Web.config может использоваться для дополнительных изменений конфигурации конечной точки.</span><span class="sxs-lookup"><span data-stu-id="09380-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="09380-116">Если дополнительных изменений не требуется, он может быть удален.</span><span class="sxs-lookup"><span data-stu-id="09380-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="09380-117">Форматом данных по умолчанию для <xref:System.ServiceModel.Description.WebHttpEndpoint> является XML, а формат данных по умолчанию для <xref:System.ServiceModel.Description.WebScriptEndpoint> является JSON.</span><span class="sxs-lookup"><span data-stu-id="09380-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="09380-118">Дополнительные сведения см. в разделе [создание служб WCF AJAX без использования ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="09380-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="09380-119">В следующем примере она стандартной службы WCF с двумя операциями.</span><span class="sxs-lookup"><span data-stu-id="09380-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="09380-120">Обе операции требуют использования основного стиля <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> в <xref:System.ServiceModel.Web.WebGetAttribute> или атрибутов <xref:System.ServiceModel.Web.WebInvokeAttribute>, которые относятся к поведению `webHttp` и не влияют на переключение формата данных JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="09380-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="09380-121">Формат ответа для операции задан как XML, который используется по умолчанию для [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) поведение.</span><span class="sxs-lookup"><span data-stu-id="09380-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="09380-122">Тем не менее, рекомендуется явно указывать формат ответа.</span><span class="sxs-lookup"><span data-stu-id="09380-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="09380-123">Другая операция использует атрибут `WebInvokeAttribute` и явно указывает JSON вместо XML для ответа.</span><span class="sxs-lookup"><span data-stu-id="09380-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="09380-124">Обратите внимание, что в обоих случаях операции возвращают сложный тип, `MathResult`, который является стандартный тип контракта данных WCF.</span><span class="sxs-lookup"><span data-stu-id="09380-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>  
  
 <span data-ttu-id="09380-125">Клиентская веб-страница XmlAjaxClientPage.htm содержит код JavaScript, который вызывает один из двух предшествующих операций, когда пользователь щелкает **выполнить расчет (возвратить JSON)** или **выполнить расчет (возвратить XML)**  кнопок на странице.</span><span class="sxs-lookup"><span data-stu-id="09380-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="09380-126">Код, вызывающий службу, создает тело JSON и отправляет его с помощью HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="09380-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="09380-127">Запрос создается вручную в JavaScript, в отличие от [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) пример и других примеров с использованием ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="09380-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 <span data-ttu-id="09380-128">При ответе службы ответ отображается без какой-либо дополнительной обработки в текстовом поле страницы.</span><span class="sxs-lookup"><span data-stu-id="09380-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="09380-129">Это реализовано с целью демонстрации и дает возможность непосредственно ознакомиться с используемыми форматами данных XML и JSON.</span><span class="sxs-lookup"><span data-stu-id="09380-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="09380-130">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="09380-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="09380-131">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="09380-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="09380-132">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="09380-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09380-133">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="09380-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="09380-134">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="09380-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="09380-135">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="09380-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="09380-136">Построение решения XmlAjaxService.sln, как описано в разделе [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="09380-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="09380-137">Перейдите к `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (не открывайте XmlAjaxClientPage.htm в браузере из каталога проекта).</span><span class="sxs-lookup"><span data-stu-id="09380-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09380-138">См. также</span><span class="sxs-lookup"><span data-stu-id="09380-138">See also</span></span>

- [<span data-ttu-id="09380-139">Служба AJAX с использованием HTTP POST</span><span class="sxs-lookup"><span data-stu-id="09380-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
