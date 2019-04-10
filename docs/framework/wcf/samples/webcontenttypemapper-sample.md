---
title: Пример WebContentTypeMapper
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 381fc4a3084b1a2620384a04de85b9085e02ae16
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344680"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="decfe-102">Пример WebContentTypeMapper</span><span class="sxs-lookup"><span data-stu-id="decfe-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="decfe-103">В этом примере показано, как сопоставить новые типы содержимого с форматами тела сообщения Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="decfe-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="decfe-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Элемент подключает кодировщик веб-сообщений, которая позволяет WCF для получения JSON, XML или необработанные двоичные сообщения в той же конечной точке.</span><span class="sxs-lookup"><span data-stu-id="decfe-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="decfe-105">Кодировщик определяет формат тела сообщения, просмотрев тип содержимого HTTP запроса.</span><span class="sxs-lookup"><span data-stu-id="decfe-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="decfe-106">В этом примере показан класс <xref:System.ServiceModel.Channels.WebContentTypeMapper>, который позволяет пользователю управлять сопоставлением типа содержимого и формата тела.</span><span class="sxs-lookup"><span data-stu-id="decfe-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="decfe-107">WCF предоставляет набор сопоставлений по умолчанию для типов содержимого.</span><span class="sxs-lookup"><span data-stu-id="decfe-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="decfe-108">Например, `application/json` сопоставляется с JSON, а `text/xml` сопоставляет с XML.</span><span class="sxs-lookup"><span data-stu-id="decfe-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="decfe-109">Любой тип содержимого, который не сопоставляется с JSON или XML, сопоставляется с необработанным двоичным форматом.</span><span class="sxs-lookup"><span data-stu-id="decfe-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="decfe-110">В некоторых сценариях (например, интерфейсы API внедрения) разработчик службы не управляет типом содержимого, возвращаемым клиентом.</span><span class="sxs-lookup"><span data-stu-id="decfe-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="decfe-111">Например, клиенты могут возвращать JSON как `text/javascript`, а не `application/json`.</span><span class="sxs-lookup"><span data-stu-id="decfe-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="decfe-112">В этом случае разработчик службы должен предоставить тип, унаследованный от <xref:System.ServiceModel.Channels.WebContentTypeMapper>, для правильной обработки данного типа содержимого, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="decfe-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="decfe-113">Тип должен переопределить метод <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="decfe-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="decfe-114">Метод должен оценить аргумент `contentType` и возвратить одно из следующих значений: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw> или <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="decfe-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="decfe-115">Возврат <xref:System.ServiceModel.Channels.WebContentFormat.Default> следует сопоставлениям кодировщика веб-сообщений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="decfe-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="decfe-116">В предыдущем примере кода тип содержимого `text/javascript` сопоставляется с JSON, а все другие сопоставления остаются неизменными.</span><span class="sxs-lookup"><span data-stu-id="decfe-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="decfe-117">Для использования класса `JsonContentTypeMapper` воспользуйтесь следующими элементами Web.config:</span><span class="sxs-lookup"><span data-stu-id="decfe-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="decfe-118">Чтобы проверить требование к использованию JsonContentTypeMapper, удалите атрибут contentTypeMapper из указанного выше файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="decfe-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="decfe-119">Не удается загрузить страницу клиента при попытке использования `text/javascript` для отправки содержимого JSON.</span><span class="sxs-lookup"><span data-stu-id="decfe-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="decfe-120">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="decfe-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="decfe-121">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="decfe-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="decfe-122">Построение решения webcontenttypemappersample.sln, описанное в разделе [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="decfe-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="decfe-123">Перейдите к `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (не открывайте страницу JCTMClientPage.htm в браузере из каталога проекта).</span><span class="sxs-lookup"><span data-stu-id="decfe-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="decfe-124">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="decfe-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="decfe-125">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="decfe-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="decfe-126">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="decfe-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="decfe-127">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="decfe-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
