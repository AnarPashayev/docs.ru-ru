---
title: Доступ к службам WCF из клиентского приложения Магазина Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 9316a46f809eec21f73e8eeadb49baf1748c6ca0
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988249"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="06e48-102">Доступ к службам WCF из клиентского приложения Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="06e48-103">В Windows 8 появился новый тип приложения - приложения Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="06e48-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="06e48-104">Эти приложения предназначены для работы с сенсорным экраном.</span><span class="sxs-lookup"><span data-stu-id="06e48-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="06e48-105">.NET Framework 4.5 позволяет приложениям Магазина Windows вызывать службы WCF.</span><span class="sxs-lookup"><span data-stu-id="06e48-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="06e48-106">Поддержка WCF в приложениях Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="06e48-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="06e48-107">Подмножество функций WCF доступно из приложения Магазина Windows. Дополнительную информацию см. в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="06e48-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="06e48-108">Используйте API-синдикации WinRT вместо методов, доступных через службу WCF.</span><span class="sxs-lookup"><span data-stu-id="06e48-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="06e48-109">Дополнительные сведения см. в разделе [API синдикации WinRT](https://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="06e48-109">For more information see, [WinRT Syndication API](https://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="06e48-110">Использование диалогового окна «Добавление ссылки на службу» для добавления ссылки на веб-службу в компонент среды выполнения Windows не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="06e48-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="06e48-111">Поддерживаемые привязки</span><span class="sxs-lookup"><span data-stu-id="06e48-111">Supported Bindings</span></span>  
 <span data-ttu-id="06e48-112">Поддерживаются следующие привязки WCF в приложениях Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="06e48-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="06e48-113">Поддерживаются следующие элементы привязки в приложениях Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="06e48-114">Поддерживается текстовое и двоичное кодирование.</span><span class="sxs-lookup"><span data-stu-id="06e48-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="06e48-115">Поддерживаются все режимы передачи WCF.</span><span class="sxs-lookup"><span data-stu-id="06e48-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="06e48-116">Дополнительные сведения см. в разделе [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="06e48-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="06e48-117">Добавление ссылки на службу</span><span class="sxs-lookup"><span data-stu-id="06e48-117">Add Service Reference</span></span>  
 <span data-ttu-id="06e48-118">Для вызова службы WCF из приложения Магазина Windows пользуйтесь функцией «Добавить ссылку на службу» среды Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="06e48-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="06e48-119">Можно заметить небольшие изменения в работе функции «Добавить ссылку на службу» при работе с приложением Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="06e48-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="06e48-120">Во-первых, не создается файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="06e48-120">First no configuration file is generated.</span></span> <span data-ttu-id="06e48-121">Приложения Магазина Windows не используют файлы конфигурации, поэтому их необходимо настраивать в коде.</span><span class="sxs-lookup"><span data-stu-id="06e48-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="06e48-122">Код конфигурации можно найти в файле References.cs, который создается функцией «Добавить ссылку на службу».</span><span class="sxs-lookup"><span data-stu-id="06e48-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="06e48-123">Чтобы просмотреть этот файл, выберите "Показать все файлы" в обозревателе решений.</span><span class="sxs-lookup"><span data-stu-id="06e48-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="06e48-124">Файл будет расположен под пунктом «Ссылки на службу», а затем в узлах Reference.svcmap в рамках проекта.</span><span class="sxs-lookup"><span data-stu-id="06e48-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="06e48-125">Все операции, созданные для служб WCF внутри приложения Магазина Windows, будут асинхронными, использующими асинхронную технологию на основе событий.</span><span class="sxs-lookup"><span data-stu-id="06e48-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="06e48-126">Дополнительные сведения см. в разделе [Async Tasks — упрощение асинхронного программирования с помощью задач](https://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="06e48-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="06e48-127">Поскольку конфигурация создается в коде, любые изменения, внесенные в файл Reference.cs, будут перезаписываться при каждом обновлении ссылки на службу.</span><span class="sxs-lookup"><span data-stu-id="06e48-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="06e48-128">Чтобы исправить эту ситуацию, код конфигурации создается внутри разделяемого метода, который вы можно реализовать в клиентском прокси-классе.</span><span class="sxs-lookup"><span data-stu-id="06e48-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="06e48-129">Разделяемый метод определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="06e48-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="06e48-130">Затем можно реализовать этот разделяемый метод и изменить привязку или конечную точку в клиентском прокси-классе следующим образом:</span><span class="sxs-lookup"><span data-stu-id="06e48-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="06e48-131">Сериализация</span><span class="sxs-lookup"><span data-stu-id="06e48-131">Serialization</span></span>  
 <span data-ttu-id="06e48-132">Поддерживаются следующие сериализаторы WCF в приложениях Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="06e48-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="06e48-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="06e48-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="06e48-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="06e48-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="06e48-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="06e48-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="06e48-136">XmlDictionaryWriter.Write (DateTime) теперь записывает объект DateTime в виде строки.</span><span class="sxs-lookup"><span data-stu-id="06e48-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="06e48-137">Безопасность</span><span class="sxs-lookup"><span data-stu-id="06e48-137">Security</span></span>  

<span data-ttu-id="06e48-138">В приложениях Магазина Windows поддерживаются следующие режимы безопасности:</span><span class="sxs-lookup"><span data-stu-id="06e48-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="06e48-139">В приложениях Магазина Windows поддерживаются следующие типы учетных данных клиента:</span><span class="sxs-lookup"><span data-stu-id="06e48-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="06e48-140">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="06e48-140">None</span></span>  
  
2. <span data-ttu-id="06e48-141">Стандартная</span><span class="sxs-lookup"><span data-stu-id="06e48-141">Basic</span></span>  
  
3. <span data-ttu-id="06e48-142">Digest</span><span class="sxs-lookup"><span data-stu-id="06e48-142">Digest</span></span>  
  
4. <span data-ttu-id="06e48-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="06e48-143">Negotiate</span></span>  
  
5. <span data-ttu-id="06e48-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="06e48-144">NTLM</span></span>  
  
6. <span data-ttu-id="06e48-145">Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-145">Windows</span></span>  
  
7. <span data-ttu-id="06e48-146">Имя пользователя (безопасность сообщений)</span><span class="sxs-lookup"><span data-stu-id="06e48-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="06e48-147">Windows (безопасность транспорта)</span><span class="sxs-lookup"><span data-stu-id="06e48-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="06e48-148">Чтобы приложения Магазина Windows могли получать и передавать учетные данные Windows по умолчанию, необходимо включить эту возможность в файле Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="06e48-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="06e48-149">Откройте этот файл и перейдите на вкладку "возможности" и выберите "учетные данные Windows по умолчанию".</span><span class="sxs-lookup"><span data-stu-id="06e48-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="06e48-150">Это позволит приложению подключаться к ресурсам интрасети, для доступа к которым требуются учетные данные домена.</span><span class="sxs-lookup"><span data-stu-id="06e48-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="06e48-151">Чтобы приложения Магазина Windows могли выполнять вызовы между компьютерами, необходимо включить другую возможность, называемую "Домашняя или Рабочая сеть".</span><span class="sxs-lookup"><span data-stu-id="06e48-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="06e48-152">Этот параметр также находится в файле Package.appmanifest под вкладкой «Возможности». Установите флаг «Домашняя или рабочая сеть».</span><span class="sxs-lookup"><span data-stu-id="06e48-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="06e48-153">Приложение получит входящий и исходящий доступ к доверенным сетям пользователя - домашней и рабочей.</span><span class="sxs-lookup"><span data-stu-id="06e48-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="06e48-154">Важные входящие порты всегда заблокированы.</span><span class="sxs-lookup"><span data-stu-id="06e48-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="06e48-155">Для доступа к службам в Интернете необходимо также включить возможность «Интернет (клиент)».</span><span class="sxs-lookup"><span data-stu-id="06e48-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="06e48-156">Прочее</span><span class="sxs-lookup"><span data-stu-id="06e48-156">Misc</span></span>  
 <span data-ttu-id="06e48-157">Поддерживается использование следующих классов для приложений Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="06e48-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="06e48-158">Определение контрактов службы</span><span class="sxs-lookup"><span data-stu-id="06e48-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="06e48-159">Рекомендуется определять только асинхронные операции службы с помощью асинхронной модели на основе событий.</span><span class="sxs-lookup"><span data-stu-id="06e48-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="06e48-160">Это гарантирует, что приложения Магазина Windows сохранят высокую скорость отклика при вызове операции службы.</span><span class="sxs-lookup"><span data-stu-id="06e48-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="06e48-161">Хотя исключение не возникнет, если указать синхронную операцию, настоятельно рекомендуется определять только асинхронные операции.</span><span class="sxs-lookup"><span data-stu-id="06e48-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="06e48-162">Вызов служб WCF из приложений Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="06e48-163">Как уже говорилось, вся настройка должна быть сделана в коде метода GetBindingForEndpoint в сформированном прокси-классе.</span><span class="sxs-lookup"><span data-stu-id="06e48-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="06e48-164">Вызов операции службы выполняется точно так же, как и вызов любого асинхронного метода, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="06e48-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="06e48-165">Обратите внимание на использование ключевого слова async при асинхронном вызове, а также ключевого слова await при вызове асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="06e48-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e48-166">См. также</span><span class="sxs-lookup"><span data-stu-id="06e48-166">See also</span></span>

- [<span data-ttu-id="06e48-167">Блог по WCF в приложениях для Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-167">WCF in Windows Store Apps Blog</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [<span data-ttu-id="06e48-168">Клиенты и безопасность магазина Windows в WCF</span><span class="sxs-lookup"><span data-stu-id="06e48-168">WCF Windows Store Clients and Security</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [<span data-ttu-id="06e48-169">Приложения Магазина Windows и вызовы между компьютерами</span><span class="sxs-lookup"><span data-stu-id="06e48-169">Windows Store Apps and Cross Machine Calls</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="06e48-170">Вызов службы WCF, развернутой в Azure, из приложения Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="06e48-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="06e48-171">Программирование безопасности WCF</span><span class="sxs-lookup"><span data-stu-id="06e48-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="06e48-172">Привязки</span><span class="sxs-lookup"><span data-stu-id="06e48-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
