---
title: Storeadm.exe (средство изолированного хранилища)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906d9d4dfd1c1082a4b49b7143f590967dcc7fd0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092271"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="31886-102">Storeadm.exe (средство изолированного хранилища)</span><span class="sxs-lookup"><span data-stu-id="31886-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="31886-103">Программа изолированного хранилища выводит список или удаляет все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="31886-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="31886-104">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31886-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="31886-105">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="31886-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="31886-106">Дополнительные сведения см. в разделе [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="31886-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="31886-107">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="31886-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31886-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="31886-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="31886-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="31886-109">Parameters</span></span>  
  
|<span data-ttu-id="31886-110">Параметр</span><span class="sxs-lookup"><span data-stu-id="31886-110">Option</span></span>|<span data-ttu-id="31886-111">Описание</span><span class="sxs-lookup"><span data-stu-id="31886-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="31886-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="31886-112">**/h**[**elp**]</span></span>|<span data-ttu-id="31886-113">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="31886-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="31886-114">**/list**</span><span class="sxs-lookup"><span data-stu-id="31886-114">**/list**</span></span>|<span data-ttu-id="31886-115">Отображает все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="31886-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="31886-116">В их число включаются хранилища для всех приложений или сборок, выполненных данным пользователем.</span><span class="sxs-lookup"><span data-stu-id="31886-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="31886-117">**/machine**</span><span class="sxs-lookup"><span data-stu-id="31886-117">**/machine**</span></span>|<span data-ttu-id="31886-118">Выбирает хранилище компьютера.</span><span class="sxs-lookup"><span data-stu-id="31886-118">Selects the machine store.</span></span> <span data-ttu-id="31886-119">Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к хранилищу компьютера.</span><span class="sxs-lookup"><span data-stu-id="31886-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="31886-120">Новые возможности в .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="31886-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="31886-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="31886-121">**/quiet**</span></span>|<span data-ttu-id="31886-122">Определяет тихий режим, отключает вывод всех сообщений, кроме сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="31886-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="31886-123">**/remove**</span><span class="sxs-lookup"><span data-stu-id="31886-123">**/remove**</span></span>|<span data-ttu-id="31886-124">Полностью удаляет все существующие хранилища для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="31886-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="31886-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="31886-125">**/roaming**</span></span>|<span data-ttu-id="31886-126">Задает перемещаемое хранилище.</span><span class="sxs-lookup"><span data-stu-id="31886-126">Selects the roaming store.</span></span> <span data-ttu-id="31886-127">Используйте этот параметр вместе с параметром **/list** или **/remove**, чтобы указать, что данное действие должно применяться к перемещаемому хранилищу.</span><span class="sxs-lookup"><span data-stu-id="31886-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="31886-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="31886-128">**/?**</span></span>|<span data-ttu-id="31886-129">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="31886-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31886-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="31886-130">Remarks</span></span>  
 <span data-ttu-id="31886-131">При запуске программы Storeadm.exe из командной строки без указания параметров будут отображены ее синтаксис и параметры.</span><span class="sxs-lookup"><span data-stu-id="31886-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="31886-132">Обычно используется лишь один из параметров **/list** и **/remove**, однако при использовании нескольких параметров они будут обрабатываться в порядке их указания в командной строке.</span><span class="sxs-lookup"><span data-stu-id="31886-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="31886-133">Приложение может выбрать для сохранения одно из двух хранилищ пользователя или хранилище компьютера.</span><span class="sxs-lookup"><span data-stu-id="31886-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
-   <span data-ttu-id="31886-134">Локальное хранилище располагается в том месте, которое гарантированно не является перемещаемым (в Windows 2000 или более поздних версиях), даже если для пользователя включен режим перемещения данных.</span><span class="sxs-lookup"><span data-stu-id="31886-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
-   <span data-ttu-id="31886-135">Перемещаемое хранилище располагается в месте, которое можно переместить, но только если для пользователя включен режим перемещения с помощью средств администрирования Windows NT.</span><span class="sxs-lookup"><span data-stu-id="31886-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
-   <span data-ttu-id="31886-136">Хранилище компьютера является общим для всех пользователей данного компьютера и располагается в его общем каталоге.</span><span class="sxs-lookup"><span data-stu-id="31886-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31886-137">Поддержка хранилища компьютера является новой возможностью .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="31886-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="31886-138">Управление программой Storeadm.exe не зависит от того, включен ли режим перемещения для пользователя.</span><span class="sxs-lookup"><span data-stu-id="31886-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="31886-139">При запуске программы без параметров все действия применяются к локальному хранилищу.</span><span class="sxs-lookup"><span data-stu-id="31886-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="31886-140">При запуске программы с параметром **/roaming** все действия будут применяться к перемещаемому хранилищу.</span><span class="sxs-lookup"><span data-stu-id="31886-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="31886-141">При запуске программы с параметром **/machine** все действия применяются к хранилищу компьютера.</span><span class="sxs-lookup"><span data-stu-id="31886-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31886-142">См. также</span><span class="sxs-lookup"><span data-stu-id="31886-142">See also</span></span>

- [<span data-ttu-id="31886-143">Инструменты</span><span class="sxs-lookup"><span data-stu-id="31886-143">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="31886-144">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="31886-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="31886-145">Командные строки</span><span class="sxs-lookup"><span data-stu-id="31886-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
