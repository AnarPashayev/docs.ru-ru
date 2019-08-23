---
title: Средство регистрации ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 519f303507ed873266cc05a7556073887b66ba6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923027"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="bbda1-102">Средство регистрации ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="bbda1-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="bbda1-103">Этот инструмент командной строки предоставляет возможность управления регистрацией компонентов WCF и WF на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="bbda1-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="bbda1-104">В обычных условиях использование данного средства не требуется, так как при установке компонентов WCF и WF производится их правильная настройка.</span><span class="sxs-lookup"><span data-stu-id="bbda1-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="bbda1-105">Но если вы испытываете проблемы с активацией службы, то можно попробовать зарегистрировать компоненты с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="bbda1-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbda1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bbda1-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="bbda1-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="bbda1-107">Remarks</span></span>  
 <span data-ttu-id="bbda1-108">Это средство можно найти в следующей папке:</span><span class="sxs-lookup"><span data-stu-id="bbda1-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="bbda1-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bbda1-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="bbda1-110">[!INCLUDE[wv](../../../includes/wv-md.md)]При запуске средства регистрации ServiceModel в диалоговом окне " **компоненты Windows** " может не отображаться, что параметр **Windows Communication Foundation активации HTTP** в разделе **Microsoft .NET Framework 3,0** включен.</span><span class="sxs-lookup"><span data-stu-id="bbda1-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="bbda1-111">Чтобы открыть диалоговое окно **компонентов Windows** , нажмите кнопку **Пуск**, выберите команду **выполнить** и введите **оптионалфеатурес**.</span><span class="sxs-lookup"><span data-stu-id="bbda1-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="bbda1-112">В следующей таблице представлены параметры, которые могут использоваться с ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="bbda1-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="bbda1-113">Параметр</span><span class="sxs-lookup"><span data-stu-id="bbda1-113">Option</span></span>|<span data-ttu-id="bbda1-114">Описание</span><span class="sxs-lookup"><span data-stu-id="bbda1-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="bbda1-115">Устанавливает все компоненты WCF и WF.</span><span class="sxs-lookup"><span data-stu-id="bbda1-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="bbda1-116">Удаляет все компоненты WCF и WF.</span><span class="sxs-lookup"><span data-stu-id="bbda1-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="bbda1-117">Ремонтирует все компоненты WCF и WF.</span><span class="sxs-lookup"><span data-stu-id="bbda1-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="bbda1-118">Устанавливает компоненты WCF и WF, заданные с помощью ключа «-с».</span><span class="sxs-lookup"><span data-stu-id="bbda1-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="bbda1-119">Удаляет компоненты WCF и WF, заданные с помощью ключа «-с».</span><span class="sxs-lookup"><span data-stu-id="bbda1-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="bbda1-120">Устанавливает или удаляет компонент.</span><span class="sxs-lookup"><span data-stu-id="bbda1-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="bbda1-121">-хттпнамеспаце — резервирование пространства имен HTTP</span><span class="sxs-lookup"><span data-stu-id="bbda1-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="bbda1-122">-ткппортшаринг — служба общего доступа к портам TCP</span><span class="sxs-lookup"><span data-stu-id="bbda1-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="bbda1-123">-ткпактиватион — служба активации TCP (не поддерживается в клиентском профиле .NET 4)</span><span class="sxs-lookup"><span data-stu-id="bbda1-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="bbda1-124">-намедпипеактиватион — служба активации именованных каналов (не поддерживается в клиентском профиле .NET 4)</span><span class="sxs-lookup"><span data-stu-id="bbda1-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="bbda1-125">-Служба msmqactivation — служба активации MSMQ (не поддерживается в клиентском профиле .NET 4)</span><span class="sxs-lookup"><span data-stu-id="bbda1-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="bbda1-126">-ETW — манифесты трассировки событий ETW (Windows Vista или более поздней версии)</span><span class="sxs-lookup"><span data-stu-id="bbda1-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="bbda1-127">Тихий режим (только для отображения журнала ошибок)</span><span class="sxs-lookup"><span data-stu-id="bbda1-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="bbda1-128">Режим подробного вывода.</span><span class="sxs-lookup"><span data-stu-id="bbda1-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="bbda1-129">Подавляет вывод логотипа и сообщения об авторском праве.</span><span class="sxs-lookup"><span data-stu-id="bbda1-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="bbda1-130">Отображает текст справки</span><span class="sxs-lookup"><span data-stu-id="bbda1-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="bbda1-131">Исправление ошибки FileLoadException</span><span class="sxs-lookup"><span data-stu-id="bbda1-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="bbda1-132">Если вы установили предыдущие версии WCF на компьютере, при запуске средства ServiceModelReg для `FileLoadFoundException` регистрации новой установки может возникнуть ошибка.</span><span class="sxs-lookup"><span data-stu-id="bbda1-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="bbda1-133">Это может произойти, даже если пользователь вручную удалил файлы из каталога установки предыдущей версии, но оставил файл machine.config без изменений.</span><span class="sxs-lookup"><span data-stu-id="bbda1-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="bbda1-134">Сообщение об ошибке подобно приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="bbda1-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="bbda1-135">Из этого сообщения об ошибке можно выяснить, что сборка System.ServiceModel версии 2.0.0.0 была установлена более ранней CTP-версией.</span><span class="sxs-lookup"><span data-stu-id="bbda1-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="bbda1-136">Текущая версия сборки System.ServiceModel - 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="bbda1-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="bbda1-137">Таким образом, эта проблема возникает, если необходимо установить официальный выпуск WCF на компьютере, где была установлена ранняя CTP-версия WCF, но не полностью удалена.</span><span class="sxs-lookup"><span data-stu-id="bbda1-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="bbda1-138">ServiceModelReg.exe не может удалять записи предыдущих версий или регистрировать записи новой версии.</span><span class="sxs-lookup"><span data-stu-id="bbda1-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="bbda1-139">Единственным решением является изменение файла machine.config вручную. Этот файл находится в следующем расположении.</span><span class="sxs-lookup"><span data-stu-id="bbda1-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="bbda1-140">Если WCF выполняется на 64-разрядном компьютере, необходимо также изменить тот же файл в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="bbda1-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="bbda1-141">Найдите в этом файле все XML-узлы, которые ссылаются на "System. ServiceModel, версия = 2.0.0.0", удалите их и все дочерние узлы.</span><span class="sxs-lookup"><span data-stu-id="bbda1-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="bbda1-142">Сохраните файл и повторно запустите ServiceModelReg.exe. Проблема устранена.</span><span class="sxs-lookup"><span data-stu-id="bbda1-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bbda1-143">Примеры</span><span class="sxs-lookup"><span data-stu-id="bbda1-143">Examples</span></span>  
 <span data-ttu-id="bbda1-144">В следующих примерах показано, как использовать наиболее употребимые параметры средства ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="bbda1-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
