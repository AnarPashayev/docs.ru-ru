---
title: Статистические функции (SqlClient для Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204519"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="ceeed-102">Статистические функции (SqlClient для Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="ceeed-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="ceeed-103">Поставщик данных .NET Framework для SQL Server (SqlClient) предоставляет агрегатные функции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="ceeed-104">Агрегатные функции выполняют вычисления на наборе входных значений и возвращают значение.</span><span class="sxs-lookup"><span data-stu-id="ceeed-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="ceeed-105">Эти функции находятся в пространстве имен SqlServer, которое доступно при использовании SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ceeed-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="ceeed-106">Свойство пространства имен поставщика позволяет платформе Entity Framework узнать, какой префикс используется поставщиком для конкретных конструкций, таких как типы или функции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="ceeed-107">Ниже приведены агрегатные функции SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ceeed-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="ceeed-108">AVG (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-108">AVG(expression)</span></span>

<span data-ttu-id="ceeed-109">Возвращает среднее значение для значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="ceeed-110">Значения NULL пропускаются.</span><span class="sxs-lookup"><span data-stu-id="ceeed-110">Null values are ignored.</span></span>

<span data-ttu-id="ceeed-111">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-111">**Arguments**</span></span>

<span data-ttu-id="ceeed-112">`Int32`,, `Int64` `Double` И `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ceeed-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="ceeed-113">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-113">**Return Value**</span></span>

<span data-ttu-id="ceeed-114">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-114">The type of `expression`.</span></span>

<span data-ttu-id="ceeed-115">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="ceeed-116">CHECKSUM_AGG (коллекция)</span><span class="sxs-lookup"><span data-stu-id="ceeed-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="ceeed-117">Возвращает контрольную сумму значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="ceeed-118">Значения NULL пропускаются.</span><span class="sxs-lookup"><span data-stu-id="ceeed-118">Null values are ignored.</span></span>

 <span data-ttu-id="ceeed-119">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-119">**Arguments**</span></span>

 <span data-ttu-id="ceeed-120">Коллекция ( `Int32` ).</span><span class="sxs-lookup"><span data-stu-id="ceeed-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="ceeed-121">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-121">**Return Value**</span></span>

 <span data-ttu-id="ceeed-122">Объект `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-122">An `Int32`.</span></span>

 <span data-ttu-id="ceeed-123">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="ceeed-124">COUNT (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-124">COUNT(expression)</span></span>

<span data-ttu-id="ceeed-125">Возвращает число элементов в коллекции в виде `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="ceeed-126">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-126">**Arguments**</span></span>

<span data-ttu-id="ceeed-127">Коллекция \<T> , где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="ceeed-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="ceeed-128">`Guid` (не возвращается в SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="ceeed-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="ceeed-129">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-129">**Return Value**</span></span>

<span data-ttu-id="ceeed-130">Объект `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-130">An `Int32`.</span></span>

<span data-ttu-id="ceeed-131">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="ceeed-132">COUNT_BIG (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="ceeed-133">Возвращает число элементов в коллекции в виде `bigint`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="ceeed-134">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-134">**Arguments**</span></span>

 <span data-ttu-id="ceeed-135">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="ceeed-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="ceeed-136">`Guid` (не возвращается в SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="ceeed-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="ceeed-137">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-137">**Return Value**</span></span>

<span data-ttu-id="ceeed-138">Объект `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-138">An `Int64`.</span></span>

<span data-ttu-id="ceeed-139">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="ceeed-140">MAX (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-140">MAX(expression)</span></span>

<span data-ttu-id="ceeed-141">Возвращает максимальное значение, содержащееся в коллекции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="ceeed-142">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-142">**Arguments**</span></span>

<span data-ttu-id="ceeed-143">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="ceeed-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="ceeed-144">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-144">**Return Value**</span></span>

<span data-ttu-id="ceeed-145">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-145">The type of `expression`.</span></span>

<span data-ttu-id="ceeed-146">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="ceeed-147">MIN (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-147">MIN(expression)</span></span>

<span data-ttu-id="ceeed-148">Возвращает минимальное значение в коллекции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="ceeed-149">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-149">**Arguments**</span></span>

<span data-ttu-id="ceeed-150">Коллекция (T), где T — один из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="ceeed-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="ceeed-151">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-151">**Return Value**</span></span>

<span data-ttu-id="ceeed-152">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-152">The type of `expression`.</span></span>

<span data-ttu-id="ceeed-153">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="ceeed-154">STDEV (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-154">STDEV(expression)</span></span>

<span data-ttu-id="ceeed-155">Возвращает статистическое стандартное отклонение всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="ceeed-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="ceeed-156">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-156">**Arguments**</span></span>

<span data-ttu-id="ceeed-157">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="ceeed-157">A Collection(`Double`).</span></span>

<span data-ttu-id="ceeed-158">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-158">**Return Value**</span></span>

<span data-ttu-id="ceeed-159">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-159">A `Double`.</span></span>

<span data-ttu-id="ceeed-160">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="ceeed-161">STDEVP (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-161">STDEVP(expression)</span></span>

<span data-ttu-id="ceeed-162">Возвращает статистическое стандартное отклонение совокупности всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="ceeed-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="ceeed-163">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-163">**Arguments**</span></span>

<span data-ttu-id="ceeed-164">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="ceeed-164">A Collection(`Double`).</span></span>

<span data-ttu-id="ceeed-165">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-165">**Return Value**</span></span>

<span data-ttu-id="ceeed-166">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-166">A `Double`.</span></span>

<span data-ttu-id="ceeed-167">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="ceeed-168">SUM (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-168">SUM(expression)</span></span>

<span data-ttu-id="ceeed-169">Возвращает сумму всех значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="ceeed-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="ceeed-170">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-170">**Arguments**</span></span>

<span data-ttu-id="ceeed-171">Коллекция (T), где T — один из следующих типов: `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ceeed-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="ceeed-172">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-172">**Return Value**</span></span>

<span data-ttu-id="ceeed-173">Тип параметра `expression`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-173">The type of `expression`.</span></span>

<span data-ttu-id="ceeed-174">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="ceeed-175">VAR (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-175">VAR(expression)</span></span>

<span data-ttu-id="ceeed-176">Возвращает статистическую дисперсию всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="ceeed-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="ceeed-177">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-177">**Arguments**</span></span>

<span data-ttu-id="ceeed-178">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="ceeed-178">A Collection(`Double`).</span></span>

<span data-ttu-id="ceeed-179">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-179">**Return Value**</span></span>

<span data-ttu-id="ceeed-180">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-180">A `Double`.</span></span>

<span data-ttu-id="ceeed-181">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="ceeed-182">VARP (выражение)</span><span class="sxs-lookup"><span data-stu-id="ceeed-182">VARP(expression)</span></span>

<span data-ttu-id="ceeed-183">Возвращает статистическую дисперсию для заполнения всех значений в указанном выражении.</span><span class="sxs-lookup"><span data-stu-id="ceeed-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="ceeed-184">**Аргументы**</span><span class="sxs-lookup"><span data-stu-id="ceeed-184">**Arguments**</span></span>

<span data-ttu-id="ceeed-185">Коллекция ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="ceeed-185">A Collection(`Double`).</span></span>

<span data-ttu-id="ceeed-186">**Возвращаемое значение**</span><span class="sxs-lookup"><span data-stu-id="ceeed-186">**Return Value**</span></span>

<span data-ttu-id="ceeed-187">Объект `Double`.</span><span class="sxs-lookup"><span data-stu-id="ceeed-187">A `Double`.</span></span>

<span data-ttu-id="ceeed-188">**Пример**</span><span class="sxs-lookup"><span data-stu-id="ceeed-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="ceeed-189">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ceeed-189">See also</span></span>

- [<span data-ttu-id="ceeed-190">Агрегатные функции (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ceeed-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="ceeed-191">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ceeed-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="ceeed-192">Статистические канонические функции</span><span class="sxs-lookup"><span data-stu-id="ceeed-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
