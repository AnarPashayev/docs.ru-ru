---
title: Сообщения без оболочки
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 161f38e474534d5a0e522817c4bd64925bb4cac6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976759"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="4a0c6-102">Сообщения без оболочки</span><span class="sxs-lookup"><span data-stu-id="4a0c6-102">Unwrapped Messages</span></span>
<span data-ttu-id="4a0c6-103">В этом образце показаны сообщения без оболочки.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="4a0c6-104">По умолчанию текст сообщения форматируется так, чтобы параметры, которые передаются операциям службы, находились в оболочке.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="4a0c6-105">В следующем образце показано заключенное в оболочку сообщение запроса `Add` для службы `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="4a0c6-106">Элемент `<Add>` в теле сообщения выступает в роли оболочки для параметров `n1` и `n2`.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="4a0c6-107">В следующем образце показано эквивалентное сообщение без оболочки.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 <span data-ttu-id="4a0c6-108">В этом сообщении параметры `n1` и `n2` не помещены в элемент-оболочку, а являются непосредственными дочерними элементами элемента soap body.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a0c6-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4a0c6-110">В этом образце сообщение без оболочки создается путем применения атрибута <xref:System.ServiceModel.MessageContractAttribute> к типу параметра и типу возвращаемого значения операции службы, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="4a0c6-111">Для просмотра всех отправляемых и получаемых сообщений в этом образце используется трассировка.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="4a0c6-112">Кроме того, для привязки <xref:System.ServiceModel.WSHttpBinding> не были настроены параметры безопасности, чтобы сократить число заносимых в журнал сообщений.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="4a0c6-113">Получившийся журнал трассировки (c:\logs\Message.log) можно просмотреть с помощью [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4a0c6-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="4a0c6-114">Чтобы просмотреть содержимое сообщения, выберите **сообщения** в левой и правой областях средства Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="4a0c6-115">Этот образец настроен таким образом, чтобы журналы трассировки сохранялись в папке C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="4a0c6-116">Создайте эту папку перед выполнением образца и предоставьте сетевой службе пользователя разрешение на запись в эту папку.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4a0c6-117">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="4a0c6-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4a0c6-118">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a0c6-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4a0c6-119">Создайте каталог C:\LOGS для регистрации сообщений.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="4a0c6-120">Предоставьте сетевой службе пользователя разрешение на запись в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="4a0c6-121">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a0c6-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4a0c6-122">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4a0c6-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a0c6-123">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a0c6-124">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4a0c6-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a0c6-125">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a0c6-126">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="4a0c6-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
