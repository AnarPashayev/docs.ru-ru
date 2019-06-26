---
title: Программа регистрации служб WorkFlow (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 211af75c04dfe971228bc1710fbe1fc4d7aaee60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402473"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="81463-102">Программа регистрации служб WorkFlow (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="81463-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="81463-103">Средство регистрации служб Workflow Services (WFServicesReg.exe) - это автономное средство, которое можно использовать для добавления, удаления или восстановления элементов конфигурации для служб Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="81463-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81463-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81463-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="81463-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="81463-105">Remarks</span></span>  
 <span data-ttu-id="81463-106">Это средство можно найти в следующей папке установки [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]: %windir%\Microsoft.NET\Framework\v3.5 или %windir%\Microsoft.NET\Framework64\v3.5 на 64-разрядных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="81463-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="81463-107">В следующей таблице представлены параметры, которые могут использоваться со средством регистрации служб Workflow Services (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="81463-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="81463-108">Параметр</span><span class="sxs-lookup"><span data-stu-id="81463-108">Option</span></span>|<span data-ttu-id="81463-109">Описание</span><span class="sxs-lookup"><span data-stu-id="81463-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="81463-110">Настраивает службы Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="81463-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="81463-111">Используется в сценариях установки и восстановления.</span><span class="sxs-lookup"><span data-stu-id="81463-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="81463-112">Удаляет конфигурацию служб Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="81463-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="81463-113">Отображает подробную выходную информацию (при настройке или удалении).</span><span class="sxs-lookup"><span data-stu-id="81463-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="81463-114">Включает формат ведения журнала MSI.</span><span class="sxs-lookup"><span data-stu-id="81463-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="81463-115">Сворачивает окно при выполнении приложения.</span><span class="sxs-lookup"><span data-stu-id="81463-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="81463-116">Регистрация</span><span class="sxs-lookup"><span data-stu-id="81463-116">Registration</span></span>  
 <span data-ttu-id="81463-117">Средство проверяет файл Web.config и регистрирует следующие объекты.</span><span class="sxs-lookup"><span data-stu-id="81463-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="81463-118">Ссылочные сборки [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81463-118">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] reference assemblies.</span></span>  
  
- <span data-ttu-id="81463-119">Поставщик построения для XOML-файлов.</span><span class="sxs-lookup"><span data-stu-id="81463-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="81463-120">Обработчики HTTP-данных для XOML- и RULES-файлов.</span><span class="sxs-lookup"><span data-stu-id="81463-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="81463-121">Средство проверяет файл Machine.config и регистрирует следующие расширения.</span><span class="sxs-lookup"><span data-stu-id="81463-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="81463-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="81463-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="81463-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="81463-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="81463-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="81463-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="81463-125">Средство также регистрирует следующие средства импорта метаданных клиента.</span><span class="sxs-lookup"><span data-stu-id="81463-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="81463-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="81463-126">policyImporters</span></span>  
  
- <span data-ttu-id="81463-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="81463-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="81463-128">Средство также регистрирует карты скриптов и обработчики XOML и RULES в метабазе IIS.</span><span class="sxs-lookup"><span data-stu-id="81463-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="81463-129">На [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] и [!INCLUDE[wxp](../../../includes/wxp-md.md)] машины регистрируются (IIS 5.1 и IIS 6.0), один набор карт скриптов XOML и Rules.</span><span class="sxs-lookup"><span data-stu-id="81463-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="81463-130">На 64-разрядных компьютерах средство регистрирует карты скриптов режима WOW, если включен переключатель `Enable32BitAppOnWin64`, или собственные 64-разрядные карты скриптов, если переключатель `Enable32BitAppOnWin64` отключен.</span><span class="sxs-lookup"><span data-stu-id="81463-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="81463-131">На [!INCLUDE[wv](../../../includes/wv-md.md)] и Windows Server 2008 (IIS 7.0 и более поздних версий) регистрацией компьютеров, два набора обработчиков XOML и Rules: один для интегрированного режима и один для классического режима.</span><span class="sxs-lookup"><span data-stu-id="81463-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="81463-132">На 64-разрядных компьютерах регистрируется три набора обработчиков (независимо от состояния переключателя `Enable32BitAppOnWin64`): один для интегрированного режима, один для классического режима WOW и один для собственного 64-разрядного классического режима.</span><span class="sxs-lookup"><span data-stu-id="81463-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81463-133">В отличие от ServiceModelreg.exe средство WFServicesReg.exe не позволяет добавлять, удалять или восстанавливать карты скриптов или обработчики для конкретного веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="81463-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="81463-134">Пути обхода данной проблемы см. в разделе "Восстановление карт скриптов".</span><span class="sxs-lookup"><span data-stu-id="81463-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="81463-135">Сценарии использования</span><span class="sxs-lookup"><span data-stu-id="81463-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="81463-136">Установка IIS после установки .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="81463-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="81463-137">На компьютере под управлением [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] установка [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] выполняется перед установкой IIS.</span><span class="sxs-lookup"><span data-stu-id="81463-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="81463-138">Из-за недоступности метабазы IIS при установке [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] карты скриптов XOML и RULES не устанавливаются.</span><span class="sxs-lookup"><span data-stu-id="81463-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="81463-139">После установки IIS можно воспользоваться средством WFServicesReg.exe с переключателем `/c` для установки этих карт скриптов.</span><span class="sxs-lookup"><span data-stu-id="81463-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="81463-140">Восстановление карт скриптов</span><span class="sxs-lookup"><span data-stu-id="81463-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="81463-141">Карта скрипта удалена из узла "Веб-сайты"</span><span class="sxs-lookup"><span data-stu-id="81463-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="81463-142">На компьютере под управлением [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] XOML- и RULES-файлы были случайно удалены из узла "Веб-сайты".</span><span class="sxs-lookup"><span data-stu-id="81463-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="81463-143">Чтобы выполнить восстановление, запустите средство WFServicesReg.exe с переключателем `/c`.</span><span class="sxs-lookup"><span data-stu-id="81463-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="81463-144">Карта скрипта удалена из конкретного веб-сайта</span><span class="sxs-lookup"><span data-stu-id="81463-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="81463-145">На компьютере под управлением [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] XOML- и RULES-файлы были случайно удалены из конкретного веб-сайта (например, из веб-сайта по умолчанию), а не из узла "Веб-сайты".</span><span class="sxs-lookup"><span data-stu-id="81463-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="81463-146">Чтобы восстановить удаленные обработчики для конкретного веб-сайта, необходимо запустить «WFServicesReg.exe/r» для удаления обработчиков из всех веб-сайтов, затем выполните команду «WFServicesReg.exe c» для создания соответствующих обработчиков для всех веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="81463-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="81463-147">Настройка обработчиков после переключения режима IIS</span><span class="sxs-lookup"><span data-stu-id="81463-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="81463-148">Если IIS работает в режиме общей конфигурации и установлена платформа [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], метабаза IIS настраивается в общем расположении.</span><span class="sxs-lookup"><span data-stu-id="81463-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="81463-149">Если переключить IIS в режим, отличный от режима общей конфигурации, в локальной метабазе не будут содержаться необходимые обработчики.</span><span class="sxs-lookup"><span data-stu-id="81463-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="81463-150">Чтобы правильно настроить локальную метабазу, можно импортировать общую метабазу в локальную или выполнить «WFServicesReg.exe c», позволяющую настроить локальную метабазу.</span><span class="sxs-lookup"><span data-stu-id="81463-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
