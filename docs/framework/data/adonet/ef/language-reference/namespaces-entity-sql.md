---
title: Пространства имен (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7a53f8e7e70dbc9fa505f7f8619af10a0e44c331
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197811"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="30717-102">Пространства имен (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="30717-102">Namespaces (Entity SQL)</span></span>

<span data-ttu-id="30717-103">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] были введены пространства имен, чтобы избежать возникновения конфликтов с именами глобальных идентификаторов, например именами типов, наборов сущностей, функций и т. д.</span><span class="sxs-lookup"><span data-stu-id="30717-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="30717-104">Поддержка пространства имен в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] аналогична поддержке пространства имен в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30717-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="30717-105">предоставляет две формы предложения USING: полные пространства имен (для пространства имен предоставляется короткий псевдоним) и неполные пространства имен, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="30717-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="30717-106">Правила разрешения имен</span><span class="sxs-lookup"><span data-stu-id="30717-106">Name Resolution Rules</span></span>  

 <span data-ttu-id="30717-107">Если идентификатор не может быть разрешен в локальных областях, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается определить имя в глобальных областях (пространства имен).</span><span class="sxs-lookup"><span data-stu-id="30717-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="30717-108">вначале пытается сопоставить идентификатор (префикс) с одним из полных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="30717-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="30717-109">При наличии совпадения [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается разрешить оставшуюся часть идентификатора в указанном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="30717-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="30717-110">Если совпадение не найдено, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="30717-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="30717-111">Затем [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается выполнить поиск идентификатора в всех неполных пространствах имен (указанных в прологе).</span><span class="sxs-lookup"><span data-stu-id="30717-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="30717-112">Если идентификатор удается найти только в одном пространстве имен, возвращается расположение.</span><span class="sxs-lookup"><span data-stu-id="30717-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="30717-113">Если для идентификатора обнаружены совпадения в нескольких пространствах имен, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="30717-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="30717-114">Если для идентификатора не может быть определено пространство имен, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] передает имя в следующую внешную область ( <xref:System.Data.Common.DbCommand> объект или <xref:System.Data.Common.DbConnection> ), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="30717-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="30717-115">Отличия от платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30717-115">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="30717-116">В .NET Framework можно использовать частично определенные пространства имен.</span><span class="sxs-lookup"><span data-stu-id="30717-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> <span data-ttu-id="30717-117">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] это недопустимо.</span><span class="sxs-lookup"><span data-stu-id="30717-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="30717-118">Использование ADO.NET</span><span class="sxs-lookup"><span data-stu-id="30717-118">ADO.NET Usage</span></span>  

 <span data-ttu-id="30717-119">Запросы выражаются посредством объектов <xref:System.Data.Common.DbCommand> ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="30717-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="30717-120">Объекты <xref:System.Data.Common.DbCommand> могут быть построены на основе объектов <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="30717-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="30717-121">Пространства имен также могут быть указаны как часть объектов <xref:System.Data.Common.DbCommand> и <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="30717-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="30717-122">Если [!INCLUDE[esql](../../../../../../includes/esql-md.md)] не может разрешить идентификатор внутри самого запроса, внешние пространства имен проходят проверку (на основе аналогичных правил).</span><span class="sxs-lookup"><span data-stu-id="30717-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30717-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="30717-123">See also</span></span>

- [<span data-ttu-id="30717-124">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="30717-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="30717-125">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="30717-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
