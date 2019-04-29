---
title: Практическое руководство. Поиск сборок с помощью DEVPATH
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775834"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="388e4-102">Практическое руководство. Поиск сборок с помощью DEVPATH</span><span class="sxs-lookup"><span data-stu-id="388e4-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="388e4-103">Разработчикам может потребоваться, общая сборка, которую они создадут правильно работает с несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="388e4-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="388e4-104">Вместо постоянно помещать сборку в глобальный кэш сборок во время цикла разработки, разработчик может создать переменной среды DEVPATH, которая указывает выходной каталог сборки для сборки.</span><span class="sxs-lookup"><span data-stu-id="388e4-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="388e4-105">Например предположим, что вы создаете вызывается MySharedAssembly общей сборки и в выходной каталог C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="388e4-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="388e4-106">C:\MySharedAssembly\Debug можно поместить в переменную DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="388e4-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="388e4-107">Необходимо указать [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) элемент в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="388e4-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="388e4-108">Этот элемент указывает среда CLR нужно использовать DEVPATH для поиска сборок.</span><span class="sxs-lookup"><span data-stu-id="388e4-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="388e4-109">Общая сборка должна быть обнаруживаема среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="388e4-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="388e4-110">Для указания закрытого каталога для разрешения использования ссылок на сборки [ \<codeBase > элемент](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) или [ \<probing > элемент](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) в файле конфигурации, как описано в разделе [Указание расположения сборки](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="388e4-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="388e4-111">Можно также поместить сборку в подкаталоге каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="388e4-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="388e4-112">Дополнительные сведения см. в разделе [Обнаружение сборок в среде выполнения](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="388e4-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="388e4-113">Это расширенная функция, предназначенная только для разработки.</span><span class="sxs-lookup"><span data-stu-id="388e4-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="388e4-114">В следующем примере показано, как среда выполнения для поиска сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="388e4-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="388e4-115">Пример</span><span class="sxs-lookup"><span data-stu-id="388e4-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="388e4-116">Этот параметр по умолчанию false.</span><span class="sxs-lookup"><span data-stu-id="388e4-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="388e4-117">Используйте этот параметр только во время разработки.</span><span class="sxs-lookup"><span data-stu-id="388e4-117">Use this setting only at development time.</span></span> <span data-ttu-id="388e4-118">Среда выполнения не проверяет версии на в DEVPATH сборок со строгим именем.</span><span class="sxs-lookup"><span data-stu-id="388e4-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="388e4-119">Он просто использует первый найденную сборку.</span><span class="sxs-lookup"><span data-stu-id="388e4-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388e4-120">См. также</span><span class="sxs-lookup"><span data-stu-id="388e4-120">See also</span></span>

- [<span data-ttu-id="388e4-121">Настройка приложений с помощью файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="388e4-121">Configuring Apps by using Configuration Files</span></span>](index.md)
