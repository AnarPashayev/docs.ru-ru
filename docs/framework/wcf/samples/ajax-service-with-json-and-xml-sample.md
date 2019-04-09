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
# <a name="ajax-service-with-json-and-xml-sample"></a>Пример службы AJAX с JSON и XML
В этом примере показано, как использовать Windows Communication Foundation (WCF) для создания служб асинхронных сценариев JavaScript и XML (AJAX), возвращающих нотацию объектов JavaScript (JSON) или XML-данные. К службе AJAX можно обращаться с помощью кода JavaScript из веб-браузера. Этот пример основан на [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) образца.  
  
 В отличие от других примеров AJAX, в данном примере не используется ASP.NET AJAX и управление <xref:System.Web.UI.ScriptManager>. Дополнительная настройка службы WCF AJAX может осуществляться из любой HTML-страницы через JavaScript, и этот сценарий показан здесь. Пример использования WCF с ASP.NET AJAX, см. в разделе [образцы AJAX](ajax.md).
  
 В данном разделе показано переключение типа отклика операции между JSON и XML. Данная функциональность доступна независимо от того, настроена служба для доступа через клиентскую страницу ASP.NET AJAX или через HTML/JavaScript.  
  
> [!NOTE]
> Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.
  
Чтобы разрешить использование клиентов, не являющихся клиентами ASP.NET AJAX, используйте <xref:System.ServiceModel.Activation.WebServiceHostFactory> (а не <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) в SVC-файле. <xref:System.ServiceModel.Activation.WebServiceHostFactory> Добавляет <xref:System.ServiceModel.Description.WebHttpEndpoint> стандартной конечной точки службы. Конечная точка настраивается с пустым адресом относительно SVC-файла; Это означает, что адресом службы является `http://localhost/ServiceModelSamples/service.svc`, без дополнительных суффиксов, за исключением имени операции.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Следующий раздел в Web.config может использоваться для дополнительных изменений конфигурации конечной точки. Если дополнительных изменений не требуется, он может быть удален.  
  
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
  
 Форматом данных по умолчанию для <xref:System.ServiceModel.Description.WebHttpEndpoint> является XML, а формат данных по умолчанию для <xref:System.ServiceModel.Description.WebScriptEndpoint> является JSON. Дополнительные сведения см. в разделе [создание служб WCF AJAX без использования ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 В следующем примере она стандартной службы WCF с двумя операциями. Обе операции требуют использования основного стиля <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> в <xref:System.ServiceModel.Web.WebGetAttribute> или атрибутов <xref:System.ServiceModel.Web.WebInvokeAttribute>, которые относятся к поведению `webHttp` и не влияют на переключение формата данных JSON/XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Формат ответа для операции задан как XML, который используется по умолчанию для [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) поведение. Тем не менее, рекомендуется явно указывать формат ответа.  
  
 Другая операция использует атрибут `WebInvokeAttribute` и явно указывает JSON вместо XML для ответа.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Обратите внимание, что в обоих случаях операции возвращают сложный тип, `MathResult`, который является стандартный тип контракта данных WCF.  
  
 Клиентская веб-страница XmlAjaxClientPage.htm содержит код JavaScript, который вызывает один из двух предшествующих операций, когда пользователь щелкает **выполнить расчет (возвратить JSON)** или **выполнить расчет (возвратить XML)**  кнопок на странице. Код, вызывающий службу, создает тело JSON и отправляет его с помощью HTTP POST. Запрос создается вручную в JavaScript, в отличие от [базовой службы AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) пример и других примеров с использованием ASP.NET AJAX.  

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

 При ответе службы ответ отображается без какой-либо дополнительной обработки в текстовом поле страницы. Это реализовано с целью демонстрации и дает возможность непосредственно ознакомиться с используемыми форматами данных XML и JSON.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Построение решения XmlAjaxService.sln, как описано в разделе [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Перейдите к `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (не открывайте XmlAjaxClientPage.htm в браузере из каталога проекта).  
  
## <a name="see-also"></a>См. также

- [Служба AJAX с использованием HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
