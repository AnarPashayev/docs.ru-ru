---
title: Практическое руководство. Использование поставщика ролей диспетчера авторизации ASP.NET со службой
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: ebdfa8bd7d222c4f9a33b6718b215d327d589c6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073576"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="99b90-102">Практическое руководство. Использование поставщика ролей диспетчера авторизации ASP.NET со службой</span><span class="sxs-lookup"><span data-stu-id="99b90-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="99b90-103">При размещении веб-службы в [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] можно интегрировать в приложение диспетчер авторизации, чтобы обеспечить службу возможностью авторизации.</span><span class="sxs-lookup"><span data-stu-id="99b90-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="99b90-104">Диспетчер авторизации позволяет разработчику приложения определить отдельные операции, которые можно сгруппировать для образования задач.</span><span class="sxs-lookup"><span data-stu-id="99b90-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="99b90-105">Администратор затем может авторизовать роли на выполнение определенных задач или отдельных операций.</span><span class="sxs-lookup"><span data-stu-id="99b90-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="99b90-106">Диспетчер авторизации предоставляет средство администрирования в виде оснастки консоли управления (MMC) для управления ролями, задачами, операциями и пользователями.</span><span class="sxs-lookup"><span data-stu-id="99b90-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="99b90-107">Администратор может настроить хранилище политик диспетчера авторизации в XML-файле, Active Directory или в хранилище Active Directory Application Mode (ADAM).</span><span class="sxs-lookup"><span data-stu-id="99b90-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="99b90-108">Диспетчер авторизации интегрируется в приложение путем настройки поставщика ролей диспетчера авторизации [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] для приложения [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], в котором размещается веб-служба.</span><span class="sxs-lookup"><span data-stu-id="99b90-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="99b90-109">Как и другие [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] поставщиков ролей, диспетчер авторизации [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] поставщика ролей настраивается с помощью <`providers`> элемента.</span><span class="sxs-lookup"><span data-stu-id="99b90-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="99b90-110">Следующий пример кода представляет собой отрывок файла конфигурации для веб-службы, за счет которого диспетчер авторизации интегрируется в приложение.</span><span class="sxs-lookup"><span data-stu-id="99b90-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="99b90-111">Дополнительные сведения об интеграции [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] поставщик ролей с помощью приложения WCF, см. в разделе [как: Использование поставщика ролей ASP.NET со службой](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="99b90-111">For more information about integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="99b90-112">Дополнительные сведения об использовании диспетчера авторизации с [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], см. в разделе [как: Использовать диспетчер авторизации (AzMan) с помощью ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="99b90-112">For more information about using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b90-113">См. также</span><span class="sxs-lookup"><span data-stu-id="99b90-113">See also</span></span>

- [<span data-ttu-id="99b90-114">Практическое руководство. Использование поставщика ролей ASP.NET со службой</span><span class="sxs-lookup"><span data-stu-id="99b90-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
