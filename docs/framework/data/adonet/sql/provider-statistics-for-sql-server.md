---
title: Статистика поставщика для SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: e13c4df87909629a45830e3b7950551434ed5ab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946586"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="441df-102">Статистика поставщика для SQL Server</span><span class="sxs-lookup"><span data-stu-id="441df-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="441df-103">Начиная с .NET Framework 2.0, поставщик данных .NET Framework для SQL Server поддерживает получение статистики во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="441df-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="441df-104">После создания допустимого объекта соединения необходимо включить статистику путем присвоения свойству <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> объекта <xref:System.Data.SqlClient.SqlConnection> значения `True`.</span><span class="sxs-lookup"><span data-stu-id="441df-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="441df-105">После включения статистики ее можно просмотреть в виде «моментального снимка во времени» путем получения ссылки <xref:System.Collections.IDictionary> через метод <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> объекта <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="441df-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="441df-106">Для обработки списка может использоваться набор элементов словаря, представленных в виде пар «имя/значение».</span><span class="sxs-lookup"><span data-stu-id="441df-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="441df-107">Эти пары «имя/значение» являются неупорядоченными.</span><span class="sxs-lookup"><span data-stu-id="441df-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="441df-108">Для сброса счетчиков можно в любое время вызвать метод <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> объекта <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="441df-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="441df-109">Если сбор статистики не был включен, исключение не формируется.</span><span class="sxs-lookup"><span data-stu-id="441df-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="441df-110">Кроме того, если <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> вызывается перед вызовом <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A>, полученные значения являются первоначальными для каждой записи.</span><span class="sxs-lookup"><span data-stu-id="441df-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="441df-111">Если статистика включена, запустите приложение и через некоторое время отключите статистику. Полученные значения будут отражать значения, собранные до момента отключения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="441df-112">Все собранные статистические значения относятся к конкретному соединению.</span><span class="sxs-lookup"><span data-stu-id="441df-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="441df-113">Доступные статистические значения</span><span class="sxs-lookup"><span data-stu-id="441df-113">Statistical Values Available</span></span>  
 <span data-ttu-id="441df-114">На данный момент существует 18 различных элементов, доступ к которым предоставляется поставщиком Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="441df-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="441df-115">Доступное число доступных элементов можно получить с помощью <xref:System.Collections.IDictionary> свойства **Count** ссылки на интерфейс, возвращаемой методом <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="441df-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="441df-116">Все счетчики для статистики поставщика используют тип среды <xref:System.Int64> CLR (**Long** в и Visual Basic) C# , что составляет 64 бит в ширину.</span><span class="sxs-lookup"><span data-stu-id="441df-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="441df-117">Максимальное значение типа данных **Int64** в соответствии с определением **Int64. Поле MaxValue** , имеет ((2 ^ 63)-1)).</span><span class="sxs-lookup"><span data-stu-id="441df-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="441df-118">После достижения значениями счетчиков этого максимального значения их больше нельзя считать точными.</span><span class="sxs-lookup"><span data-stu-id="441df-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="441df-119">Это означает, что **Int64. Значение MaxValue**-1 ((2 ^ 63)-2) фактически является максимальным допустимым значением для статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="441df-120">Для возврата статистики поставщика используется словарь, поскольку количество, имена и последовательность возвращаемых статистических данных в будущем может измениться.</span><span class="sxs-lookup"><span data-stu-id="441df-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="441df-121">Функционирование приложений не должно зависеть от того, будет ли найдено в словаре какое-то определенное значение; вместо этого следует проверять наличие значения и с учетом результатов этой проверки переходить в ту или иную часть приложения.</span><span class="sxs-lookup"><span data-stu-id="441df-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="441df-122">В следующей таблице описаны доступные текущие статистические значения.</span><span class="sxs-lookup"><span data-stu-id="441df-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="441df-123">Обратите внимание, что имена ключей для отдельных значений в региональных версиях Microsoft .NET Framework не локализованы.</span><span class="sxs-lookup"><span data-stu-id="441df-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="441df-124">Имя ключа</span><span class="sxs-lookup"><span data-stu-id="441df-124">Key Name</span></span>|<span data-ttu-id="441df-125">Описание</span><span class="sxs-lookup"><span data-stu-id="441df-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="441df-126">Возвращает число пакетов TDS, полученных поставщиком от SQL Server после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="441df-127">Возвращает число пакетов TDS, отправленных на SQL Server поставщиком после включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="441df-128">Для больших по размеру команд может потребоваться несколько буферов.</span><span class="sxs-lookup"><span data-stu-id="441df-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="441df-129">Например, если на сервер отправляется команда, состоящая из большого объема текста, и для ее передачи требуется шесть пакетов, то значение `ServerRoundtrips` увеличивается на единицу, а значение `BuffersSent` - на шесть.</span><span class="sxs-lookup"><span data-stu-id="441df-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="441df-130">Возвращает число байтов данных в пакетах TDS, полученных поставщиком от SQL Server после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="441df-131">Возвращает число байтов данных, отправленных на SQL Server в пакетах TDS после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="441df-132">Время (в миллисекундах), в течение которого было открыто соединение после включения статистики (или полное время соединения, если статистика была включена до открытия соединения).</span><span class="sxs-lookup"><span data-stu-id="441df-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="441df-133">Возвращает число операций открытия курсора в соединении после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="441df-134">Обратите внимание, что однопроходные результаты только для чтения, возвращаемые инструкциями SELECT, не рассматриваются как курсоры, поэтому не влияют на значение этого счетчика.</span><span class="sxs-lookup"><span data-stu-id="441df-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="441df-135">Возвращает совокупное количество времени (в миллисекундах), которое поставщик потратил на обработку после включения статистики, с учетом того времени, которое потрачено на ожидание ответов от сервера, а также времени, потраченного на выполнение кода самим поставщиком.</span><span class="sxs-lookup"><span data-stu-id="441df-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="441df-136">Код учета времени входит в следующие классы:</span><span class="sxs-lookup"><span data-stu-id="441df-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="441df-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="441df-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="441df-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="441df-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="441df-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="441df-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="441df-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="441df-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="441df-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="441df-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="441df-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="441df-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="441df-143">Для следующих членов учет времени не предусмотрен, что позволяет свести к минимуму число членов, функционирование которых может быть нарушено в условиях низкой производительности:</span><span class="sxs-lookup"><span data-stu-id="441df-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="441df-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="441df-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="441df-145">оператор this[] (все перегруженные варианты)</span><span class="sxs-lookup"><span data-stu-id="441df-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="441df-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="441df-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="441df-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="441df-147">GetChar</span></span><br /><br /> <span data-ttu-id="441df-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="441df-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="441df-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="441df-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="441df-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="441df-150">GetDouble</span></span><br /><br /> <span data-ttu-id="441df-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="441df-151">GetFloat</span></span><br /><br /> <span data-ttu-id="441df-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="441df-152">GetGuid</span></span><br /><br /> <span data-ttu-id="441df-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="441df-153">GetInt16</span></span><br /><br /> <span data-ttu-id="441df-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="441df-154">GetInt32</span></span><br /><br /> <span data-ttu-id="441df-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="441df-155">GetInt64</span></span><br /><br /> <span data-ttu-id="441df-156">GetName</span><span class="sxs-lookup"><span data-stu-id="441df-156">GetName</span></span><br /><br /> <span data-ttu-id="441df-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="441df-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="441df-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="441df-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="441df-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="441df-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="441df-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="441df-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="441df-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="441df-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="441df-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="441df-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="441df-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="441df-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="441df-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="441df-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="441df-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="441df-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="441df-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="441df-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="441df-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="441df-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="441df-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="441df-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="441df-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="441df-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="441df-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="441df-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="441df-171">GetString</span><span class="sxs-lookup"><span data-stu-id="441df-171">GetString</span></span><br /><br /> <span data-ttu-id="441df-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="441df-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="441df-173">Возвращает общее число инструкций INSERT, DELETE и UPDATE, выполненных в составе соединения после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="441df-174">Возвращает общее число строк, затронутых инструкциями INSERT, DELETE и UPDATE, которые выполнены в составе соединения после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="441df-175">Возвращает совокупное количество времени (в миллисекундах), которое поставщик потратил на ожидание ответов от сервера после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="441df-176">Возвращает число подготовленных команд, выполненных в соединении после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="441df-177">Возвращает число инструкций, подготовленных в соединении после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="441df-178">Возвращает число инструкций SELECT, выполненных в соединении после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="441df-179">Это число включает инструкции FETCH, применявшиеся для получения строк из курсоров, причем данные о количестве инструкций SELECT обновляются по достижении конца данных в объекте <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="441df-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="441df-180">Возвращает число строк, выбранных после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="441df-181">Данный счетчик отражает все строки, созданные инструкциями SQL, даже те, которые фактически не использовались вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="441df-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="441df-182">Например, значение этого счетчика не изменилось бы и после закрытия модуля чтения данных до чтения всего результирующего набора.</span><span class="sxs-lookup"><span data-stu-id="441df-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="441df-183">Сюда входят строки, полученные из курсоров с помощью инструкций FETCH.</span><span class="sxs-lookup"><span data-stu-id="441df-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="441df-184">Возвращает данные о том, сколько раз в соединении были отправлены команды на сервер и получен ответ после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="441df-185">Возвращает число результирующих наборов, использованных после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="441df-186">Например, в это число входит любой результирующий набор, возвращенный клиенту.</span><span class="sxs-lookup"><span data-stu-id="441df-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="441df-187">Применительно к курсорам результат каждой операции выборки строк или блоков рассматривается как независимый результирующий набор.</span><span class="sxs-lookup"><span data-stu-id="441df-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="441df-188">Возвращает число пользовательских транзакций, запущенных после начала использования приложением поставщика и включения статистики, с учетом откатов.</span><span class="sxs-lookup"><span data-stu-id="441df-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="441df-189">Если соединение выполняется в режиме автоматической фиксации, каждая команда считается транзакцией.</span><span class="sxs-lookup"><span data-stu-id="441df-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="441df-190">Данный счетчик увеличивает счетчик транзакций, как только выполняется инструкция BEGIN TRAN, независимо от того, была ли зафиксирована транзакция или в последующем произошел ее откат.</span><span class="sxs-lookup"><span data-stu-id="441df-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="441df-191">Возвращает число неподготовленных инструкций, выполненных в соединении после начала использования приложением поставщика и включения статистики.</span><span class="sxs-lookup"><span data-stu-id="441df-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="441df-192">Получение значения</span><span class="sxs-lookup"><span data-stu-id="441df-192">Retrieving a Value</span></span>  
 <span data-ttu-id="441df-193">Следующее приложение командной строки показывает включение статистики при соединении, получение четырех отдельных статистических значений и их запись в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="441df-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="441df-194">В следующем примере используется образец базы данных **AdventureWorks** , входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="441df-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="441df-195">Представленная в образце кода строка соединения предполагает, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="441df-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="441df-196">Измените строку соединения при необходимости в соответствии с вашей средой.</span><span class="sxs-lookup"><span data-stu-id="441df-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="441df-197">Получение всех значений</span><span class="sxs-lookup"><span data-stu-id="441df-197">Retrieving All Values</span></span>  
 <span data-ttu-id="441df-198">Следующее приложение командной строки показывает включение статистики при соединении, получение всех доступных статистических значений с помощью перечислителя и их запись в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="441df-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="441df-199">В следующем примере используется образец базы данных **AdventureWorks** , входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="441df-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="441df-200">Представленная в образце кода строка соединения предполагает, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="441df-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="441df-201">Измените строку соединения при необходимости в соответствии с вашей средой.</span><span class="sxs-lookup"><span data-stu-id="441df-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="441df-202">См. также</span><span class="sxs-lookup"><span data-stu-id="441df-202">See also</span></span>

- [<span data-ttu-id="441df-203">SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="441df-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="441df-204">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="441df-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
