---
title: Поддержка SqlClient LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 200db3b1014278e711062bcbdff81be8d27c3351
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780790"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="e5eae-102">Поддержка SqlClient LocalDB</span><span class="sxs-lookup"><span data-stu-id="e5eae-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="e5eae-103">Начиная с SQL Server Code Name Denali, будет доступна упрощенная версия SQL Server, именуемая LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e5eae-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="e5eae-104">В этом разделе описывается, как установить подключение к базе данных LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e5eae-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5eae-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="e5eae-105">Remarks</span></span>  
 <span data-ttu-id="e5eae-106">Дополнительные сведения о LocalDB, в том числе Установка LocalDB и настройка экземпляра LocalDB, см. в разделе электронная документация на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e5eae-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e5eae-107">Обзор возможностей LocalDB:</span><span class="sxs-lookup"><span data-stu-id="e5eae-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="e5eae-108">Создание и запуск экземпляров LocalDB через sqllocaldb.exe или файл app.config.</span><span class="sxs-lookup"><span data-stu-id="e5eae-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="e5eae-109">Использование sqlcmd.exe для добавления и изменения базы данных в экземпляре LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e5eae-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="e5eae-110">Например, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="e5eae-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="e5eae-111">Чтобы добавить базу данных к своему экземпляру LocalDB, пользуйтесь ключевым словом строки подключения `AttachDBFilename` .</span><span class="sxs-lookup"><span data-stu-id="e5eae-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="e5eae-112">Если при использовании `AttachDBFilename`не указано имя базы данных ключевым словом строки подключения `Database` , то база данных удаляется из экземпляра LocalDB после завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="e5eae-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="e5eae-113">Укажите экземпляр LocalDB в строке подключения.</span><span class="sxs-lookup"><span data-stu-id="e5eae-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="e5eae-114">Например, если экземпляр имеет имя `myInstance`, то строка подключения включает следующее:</span><span class="sxs-lookup"><span data-stu-id="e5eae-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="e5eae-115">Указание`User Instance=True` недопустимо, если производится соединение с базой данных LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e5eae-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="e5eae-116">Базу данных LocalDB можно скачать из [пакета дополнительных компонентов Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="e5eae-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="e5eae-117">Если вы будете использовать sqlcmd. exe для изменения данных в экземпляре LocalDB, вам потребуется программа sqlcmd от SQL Server 2012, которую также можно получить из пакета дополнительных компонентов SQL Server 2012.</span><span class="sxs-lookup"><span data-stu-id="e5eae-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="e5eae-118">Создание именованного экземпляра программным путем</span><span class="sxs-lookup"><span data-stu-id="e5eae-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="e5eae-119">В приложении можно создать именованный экземпляр и определить базу данных следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e5eae-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="e5eae-120">Определите создаваемые экземпляры LocalDB в файле app.config, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="e5eae-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="e5eae-121">Номер версии экземпляра должен совпадать с номером версии установки LocalDB.</span><span class="sxs-lookup"><span data-stu-id="e5eae-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="e5eae-122">Укажите имя экземпляра с помощью ключевого слова строки подключения `server` .</span><span class="sxs-lookup"><span data-stu-id="e5eae-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="e5eae-123">Имя экземпляра, указанное в ключевом слове строки подключения `server` , должно соответствовать имени, указанному в файле app.config.</span><span class="sxs-lookup"><span data-stu-id="e5eae-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="e5eae-124">С помощью ключевого слова строки подключения `AttachDBFilename` укажите MDF-файл.</span><span class="sxs-lookup"><span data-stu-id="e5eae-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5eae-125">См. также</span><span class="sxs-lookup"><span data-stu-id="e5eae-125">See also</span></span>

- [<span data-ttu-id="e5eae-126">Возможности SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5eae-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="e5eae-127">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5eae-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
