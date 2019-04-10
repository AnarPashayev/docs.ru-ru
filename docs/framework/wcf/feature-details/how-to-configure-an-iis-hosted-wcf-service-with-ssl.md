---
title: Практическое руководство. Как настраивать протокол SSL в службе WCF, размещенной в IIS
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8d3bbb1ceab8a3bc7e5e209fda29fd574110b4f7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326454"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="b8412-102">Практическое руководство. Как настраивать протокол SSL в службе WCF, размещенной в IIS</span><span class="sxs-lookup"><span data-stu-id="b8412-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="b8412-103">В этом разделе описано, как настроить размещенную в IIS службу WCF для использования безопасности транспорта HTTP.</span><span class="sxs-lookup"><span data-stu-id="b8412-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="b8412-104">Для безопасности транспорта HTTP требуется, чтобы SSL-сертификат был зарегистрирован в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="b8412-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="b8412-105">Если SSL-сертификат не установлен, для создания тестового сертификата можно использовать службы IIS.</span><span class="sxs-lookup"><span data-stu-id="b8412-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="b8412-106">Затем необходимо добавить SSL-привязку для проекта веб-сайта и установить свойства проверки подлинности веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="b8412-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="b8412-107">Наконец, необходимо настроить службу WCF на использование протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b8412-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="b8412-108">Создание самозаверяющего сертификата</span><span class="sxs-lookup"><span data-stu-id="b8412-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="b8412-109">Откройте диспетчер служб IIS (inetmgr.exe) и выберите имя компьютера в левой части представления в виде дерева.</span><span class="sxs-lookup"><span data-stu-id="b8412-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="b8412-110">В правой части экрана выберите сертификаты сервера</span><span class="sxs-lookup"><span data-stu-id="b8412-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="b8412-111">![Главный экран диспетчера IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="b8412-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="b8412-112">В окне сертификатов сервера щелкните **создать самозаверяющий сертификат...**</span><span class="sxs-lookup"><span data-stu-id="b8412-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="b8412-113">Связь.</span><span class="sxs-lookup"><span data-stu-id="b8412-113">Link.</span></span>  
  
     <span data-ttu-id="b8412-114">![Создание самозаверяющего&#45;сертификата со службами IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="b8412-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="b8412-115">Введите понятное имя для самозаверяющего сертификата и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b8412-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="b8412-116">![Создание собственные&#45;диалоговое окно сертификата подписи](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="b8412-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="b8412-117">Сведения о только что созданный самозаверяющий сертификат теперь отображаются в **сертификаты сервера** окна.</span><span class="sxs-lookup"><span data-stu-id="b8412-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="b8412-118">![Окно "сертификат сервера"](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="b8412-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="b8412-119">Созданный сертификат устанавливается в хранилище доверенных корневых центров сертификации.</span><span class="sxs-lookup"><span data-stu-id="b8412-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="b8412-120">Добавление привязки SSL</span><span class="sxs-lookup"><span data-stu-id="b8412-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="b8412-121">По-прежнему в диспетчер служб IIS, разверните **сайты** папку и затем **Default Web Site** папку в представлении в виде дерева в левой части экрана.</span><span class="sxs-lookup"><span data-stu-id="b8412-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="b8412-122">Нажмите кнопку **привязки...**</span><span class="sxs-lookup"><span data-stu-id="b8412-122">Click the **Bindings….**</span></span> <span data-ttu-id="b8412-123">Ссылка в **действия** в правой верхней части окна.</span><span class="sxs-lookup"><span data-stu-id="b8412-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="b8412-124">![Добавление привязки SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="b8412-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="b8412-125">В окне «привязки сайта» щелкните **добавить** кнопки.</span><span class="sxs-lookup"><span data-stu-id="b8412-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="b8412-126">![Диалоговое окно привязки сайта](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="b8412-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="b8412-127">В **Добавление привязки сайта** диалоговом окне выберите https в качестве типа и понятное имя самозаверяющего сертификата, который вы только что создан.</span><span class="sxs-lookup"><span data-stu-id="b8412-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="b8412-128">![Пример привязки сайта](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="b8412-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="b8412-129">Настройка виртуального каталога для SSL</span><span class="sxs-lookup"><span data-stu-id="b8412-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="b8412-130">В диспетчере служб IIS выберите виртуальный каталог, содержащий безопасную службу WCF.</span><span class="sxs-lookup"><span data-stu-id="b8412-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="b8412-131">В центральной области окна, выберите **параметры SSL** в разделе IIS.</span><span class="sxs-lookup"><span data-stu-id="b8412-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="b8412-132">![Параметры SSL для виртуального каталога](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="b8412-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="b8412-133">На панели параметров SSL выберите **Требовать SSL** флажок и нажмите кнопку **применить** ссылку в **действия** разделе правой стороны экрана.</span><span class="sxs-lookup"><span data-stu-id="b8412-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="b8412-134">![Параметры SSL виртуального каталога](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="b8412-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="b8412-135">Настройка службы WCF для безопасности транспорта HTTP</span><span class="sxs-lookup"><span data-stu-id="b8412-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="b8412-136">В файле web.config службы WCF настройте привязку HTTP на использование безопасности транспорта, как показано в следующем фрагменте XML.</span><span class="sxs-lookup"><span data-stu-id="b8412-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="b8412-137">Укажите службу и конечную точку службы, как показано в следующем фрагменте XML.</span><span class="sxs-lookup"><span data-stu-id="b8412-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="b8412-138">Пример</span><span class="sxs-lookup"><span data-stu-id="b8412-138">Example</span></span>  
 <span data-ttu-id="b8412-139">Ниже приведен полный пример файла web.config для службы WCF, использующей безопасность транспорта HTTP</span><span class="sxs-lookup"><span data-stu-id="b8412-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8412-140">См. также</span><span class="sxs-lookup"><span data-stu-id="b8412-140">See also</span></span>

- [<span data-ttu-id="b8412-141">Размещение в службах IIS</span><span class="sxs-lookup"><span data-stu-id="b8412-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="b8412-142">Инструкции по размещению в службах IIS</span><span class="sxs-lookup"><span data-stu-id="b8412-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="b8412-143">Рекомендации по размещению в службах IIS</span><span class="sxs-lookup"><span data-stu-id="b8412-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="b8412-144">Размещение в службах IIS с использованием встроенного кода</span><span class="sxs-lookup"><span data-stu-id="b8412-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
