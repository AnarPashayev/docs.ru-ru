---
title: Использование средств разработки WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 1ffa3be4a6b8976ab978ea995e8b2c1faaacf0ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144642"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="bc95b-102">Использование средств разработки WCF</span><span class="sxs-lookup"><span data-stu-id="bc95b-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="bc95b-103">В этом разделе описываются средства разработки Visual Studio, которые могут помочь в разработке служб WCF.</span><span class="sxs-lookup"><span data-stu-id="bc95b-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="bc95b-104">Можно использовать шаблоны Visual Studio как основу для быстрого создания собственной службы, а затем использовать для отладки и тестирования службы WCF Service Auto Host и тестового клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="bc95b-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="bc95b-105">Оба этих инструмента обеспечивают быстрый и удобный цикл отладки и тестирования и исключают необходимость фиксации модели размещения на ранней стадии.</span><span class="sxs-lookup"><span data-stu-id="bc95b-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="bc95b-106">Инструменты разработчика WCF</span><span class="sxs-lookup"><span data-stu-id="bc95b-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="bc95b-107">Шаблоны WCF в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc95b-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="bc95b-108">Предопределенных шаблонов проектов и элементов Visual Studio в Visual Studio можно использовать для быстрого создания служб WCF и окружающих приложений.</span><span class="sxs-lookup"><span data-stu-id="bc95b-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="bc95b-109">Узел службы WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="bc95b-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="bc95b-110">WCF Service Auto Host (WcfSvcHost.exe) позволяет запустить отладчик Visual Studio (F5) для автоматического размещения и проверки службы, реализованный.</span><span class="sxs-lookup"><span data-stu-id="bc95b-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="bc95b-111">Затем можно проверить службу, используя клиент тестирования WCF (wcfTestClient.exe) или своего собственного клиента для поиска и устранения потенциальных ошибок.</span><span class="sxs-lookup"><span data-stu-id="bc95b-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="bc95b-112">Тестовый клиент WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="bc95b-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="bc95b-113">Тестовый клиент WCF (WcfTestClient.exe) это средство графического интерфейса пользователя, которое позволяет вводить параметры произвольных типов, отправлять их в службу и представление, которое отправляет ответ службы.</span><span class="sxs-lookup"><span data-stu-id="bc95b-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="bc95b-114">Он предоставляет удобный способ тестирования в сочетании с WCF Service Auto Host служб.</span><span class="sxs-lookup"><span data-stu-id="bc95b-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="bc95b-115">Формирование классов типов данных из XML</span><span class="sxs-lookup"><span data-stu-id="bc95b-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="bc95b-116">Данные XML, сохраненные в буфере обмена, можно вставить в кодовую страницу.</span><span class="sxs-lookup"><span data-stu-id="bc95b-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="bc95b-117">Классы, определенные в данных, будут преобразованы в типы кода.</span><span class="sxs-lookup"><span data-stu-id="bc95b-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="bc95b-118">Использование инструментов без прав администратора</span><span class="sxs-lookup"><span data-stu-id="bc95b-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="bc95b-119">Чтобы разрешить пользователям без прав администратора для разработки служб WCF, создается список ACL (список управления доступом) для пространства имен "http://+:8731/Design_Time_Addresses" во время установки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc95b-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="bc95b-120">Список управления доступом определяется пользовательским интерфейсом, который включает всех пользователей, выполнивших вход в систему.</span><span class="sxs-lookup"><span data-stu-id="bc95b-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="bc95b-121">Администраторы могут добавлять или удалять пользователей из этого списка ACL или открыть дополнительные порты. Этот список ACL позволяет шаблонам WCF или WF отправлять и получать данные в их конфигурации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bc95b-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="bc95b-122">Он также позволяет пользователям использовать WCF Service Auto Host (wcfSvcHost.exe) без предоставления им прав администратора.</span><span class="sxs-lookup"><span data-stu-id="bc95b-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="bc95b-123">Можно изменить доступ используя средство Netsh.exe в [!INCLUDE[wv](../../../includes/wv-md.md)] под учетной записью администратора.</span><span class="sxs-lookup"><span data-stu-id="bc95b-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="bc95b-124">Ниже приведен пример использования средства Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="bc95b-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="bc95b-125">Дополнительные сведения о Netsh.exe см. в разделе [способы использования средства Netsh.exe и переключателей командной строки](https://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="bc95b-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc95b-126">См. также</span><span class="sxs-lookup"><span data-stu-id="bc95b-126">See also</span></span>

- [<span data-ttu-id="bc95b-127">Шаблоны WCF в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc95b-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)
- [<span data-ttu-id="bc95b-128">Узел службы WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="bc95b-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="bc95b-129">Тестовый клиент WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="bc95b-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
