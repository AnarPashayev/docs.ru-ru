---
title: Настройка службы активации процессов Windows для использования с Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: a4c331465087c6910cb67a71d2153e08f82a6cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147710"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="845d1-102">Настройка службы активации процессов Windows для использования с Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="845d1-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="845d1-103">В этом разделе описываются шаги, необходимые для настройки службы активации Windows (WAS) в [!INCLUDE[wv](../../../../includes/wv-md.md)] для размещения Windows Communication Foundation (WCF) служб, которые не поддерживают связь по протоколу HTTP сетевые протоколы.</span><span class="sxs-lookup"><span data-stu-id="845d1-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="845d1-104">Настройка предполагает следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="845d1-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="845d1-105">Установите (или подтвердить установку) требуемые компоненты активации WCF.</span><span class="sxs-lookup"><span data-stu-id="845d1-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="845d1-106">Создайте узел WAS с привязками сетевых протоколов, которые планируется использовать, или добавьте новую привязку протокола в существующий узел.</span><span class="sxs-lookup"><span data-stu-id="845d1-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="845d1-107">Создайте приложение для размещения служб и разрешите этому приложению использовать требуемые сетевые протоколы.</span><span class="sxs-lookup"><span data-stu-id="845d1-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="845d1-108">Создание службы WCF, которая предоставляет конечную точку, отличные от HTTP.</span><span class="sxs-lookup"><span data-stu-id="845d1-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="845d1-109">Настройка узла с привязками протоколов, отличных от HTTP</span><span class="sxs-lookup"><span data-stu-id="845d1-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="845d1-110">Для использования в сочетании со службой WAS привязки к протоколу, отличному от HTTP, необходимо добавить привязку узла в конфигурацию WAS.</span><span class="sxs-lookup"><span data-stu-id="845d1-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="845d1-111">Хранилищем конфигурации для службы WAS является файл applicationHost.config, находящийся в каталоге %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="845d1-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="845d1-112">Это хранилище конфигурации используется и службой WAS, и службами IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="845d1-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="845d1-113">applicationHost.config представляет собой текстовый XML-файл, который можно открыть в любом стандартном текстовом редакторе, таком как Блокнот.</span><span class="sxs-lookup"><span data-stu-id="845d1-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="845d1-114">Тем не менее, для добавления привязок узла к отличным от HTTP протоколам рекомендуется использовать программу настройки [!INCLUDE[iisver](../../../../includes/iisver-md.md)] из командной строки (appcmd.exe).</span><span class="sxs-lookup"><span data-stu-id="845d1-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="845d1-115">Следующая команда добавляет в веб-узел по умолчанию привязку узла к протоколу net.tcp с помощью команды appcmd.exe (вводится как одна строка).</span><span class="sxs-lookup"><span data-stu-id="845d1-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="845d1-116">Эта команда добавляет новую привязку net.tcp в веб-узел по умолчанию путем добавления приведенной ниже строки в файл applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="845d1-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="845d1-117">Разрешение приложению использовать протоколы, отличные от HTTP</span><span class="sxs-lookup"><span data-stu-id="845d1-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="845d1-118">Можно включить или отключить отдельные сетевые protocolsat уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="845d1-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="845d1-119">Следующая команда иллюстрирует включение и протокола HTTP, и протокола net.tcp для приложения, выполняющегося на сайте `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="845d1-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="845d1-120">Список разрешенных протоколов также может задаваться в \<applicationDefaults > элемент конфигурации XML сайта, хранящейся в файле ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="845d1-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="845d1-121">Следующий XML-код из файла applicationHost.config иллюстрирует сайт, привязанный и к протоколу HTTP, и к протоколу, отличному от HTTP.</span><span class="sxs-lookup"><span data-stu-id="845d1-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="845d1-122">Дополнительная конфигурация, необходимая для поддержки отличных от HTTP протоколов, выделена комментариями.</span><span class="sxs-lookup"><span data-stu-id="845d1-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="845d1-123">При попытке запустить службу с помощью WAS для активации по протоколу, отличному от HTTP, когда службы WAS не установлены и не настроены, может появиться сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="845d1-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="845d1-124">Если появилось это сообщение об ошибке, убедитесь, что установлены и правильно настроены службы WAS для активации по протоколу, отличному от HTTP.</span><span class="sxs-lookup"><span data-stu-id="845d1-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="845d1-125">Дополнительные сведения см. в разделе [Как Установка и настройка компонентов активации WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="845d1-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="845d1-126">Построение службы WCF, использующей WAS для активации по протоколу, отличному от HTTP</span><span class="sxs-lookup"><span data-stu-id="845d1-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="845d1-127">После выполнения действия по установке и настройке WAS (см. в разделе [как: Установка и настройка компонентов активации WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), Настройка службы для использования WAS для активации производится аналогично настройке службы, размещенной в IIS.</span><span class="sxs-lookup"><span data-stu-id="845d1-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="845d1-128">Подробные инструкции по построению службы WCF активации WAS см. в разделе [как: Размещение службы WCF в WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="845d1-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845d1-129">См. также</span><span class="sxs-lookup"><span data-stu-id="845d1-129">See also</span></span>

- [<span data-ttu-id="845d1-130">Размещение в службе активации процессов Windows</span><span class="sxs-lookup"><span data-stu-id="845d1-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [<span data-ttu-id="845d1-131">Возможности размещения Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="845d1-131">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
