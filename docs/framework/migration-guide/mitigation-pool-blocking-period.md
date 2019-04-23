---
title: Устранение рисков. Период блокировки пула
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97650099aed0be7e1983f759cd0f38fc568f857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082767"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="8c026-102">Устранение рисков. Период блокировки пула</span><span class="sxs-lookup"><span data-stu-id="8c026-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="8c026-103">Период блокировки пула подключений был удален для подключений к базам данных Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="8c026-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="8c026-104">Дополнительное описание</span><span class="sxs-lookup"><span data-stu-id="8c026-104">Additional description</span></span>  
 <span data-ttu-id="8c026-105">В [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] и более ранних версиях, когда приложение обнаруживает временный сбой соединения при подключении к базе данных, невозможно быстро повторять попытки подключения, так как пул подключений кэширует ошибку и повторно создает ее в периоде от 5 секунд до 1 минуты. Дополнительные сведения см. в разделе [Пулы подключений SQL Server (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="8c026-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="8c026-106">Такое поведение является проблемным для подключений к базам данных Azure SQL, так как они часто завершаются временными ошибками, которые обычно устраняются через несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="8c026-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="8c026-107">Функция блокировки пула соединений означает, что приложение не может подключиться к базе данных в течение продолжительного периода даже несмотря на доступность базы данных.</span><span class="sxs-lookup"><span data-stu-id="8c026-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="8c026-108">Это вызывает особые сложности для веб-приложений, которые подключаются к базам данных Azure SQL и должны отображаться через несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="8c026-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="8c026-109">Начиная с [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], в открытых запросах подключения к известным базам данных Azure SQL (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de) открытые ошибки подключения не кэшируются.</span><span class="sxs-lookup"><span data-stu-id="8c026-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="8c026-110">Для всех остальных попыток подключений период блокировки пула подключений продолжает действовать и далее.</span><span class="sxs-lookup"><span data-stu-id="8c026-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8c026-111">Последствия</span><span class="sxs-lookup"><span data-stu-id="8c026-111">Impact</span></span>  
 <span data-ttu-id="8c026-112">Это изменение позволяет немедленно повторять попытку открытого подключения к базам данных Azure SQL, повышая тем самым производительность облачных приложений.</span><span class="sxs-lookup"><span data-stu-id="8c026-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="8c026-113">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="8c026-113">Mitigation</span></span>  
 <span data-ttu-id="8c026-114">Для приложений, на которые это изменение оказывает существенное влияние, можно отдельно настроить интервал блокировки пула подключений, задав новое свойство <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c026-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="8c026-115">Значение этого свойства является членом перечисления <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType>, которое принимает одно из трех значений:</span><span class="sxs-lookup"><span data-stu-id="8c026-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="8c026-116">Чтобы восстановить прежнее поведение, задайте свойству <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> значение <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c026-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c026-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8c026-117">See also</span></span>

- [<span data-ttu-id="8c026-118">Изменения среды выполнения</span><span class="sxs-lookup"><span data-stu-id="8c026-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
