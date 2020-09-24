---
title: Параметры (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 759452902461e1a460b69774bb33f92bbd532ed0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177523"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="f4478-102">Параметры (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f4478-102">Parameters (Entity SQL)</span></span>

<span data-ttu-id="f4478-103">Параметры - это переменные, определенные вне [!INCLUDE[esql](../../../../../../includes/esql-md.md)] обычно через привязку API, используемую базовым языком.</span><span class="sxs-lookup"><span data-stu-id="f4478-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="f4478-104">Каждый параметр имеет имя и тип.</span><span class="sxs-lookup"><span data-stu-id="f4478-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="f4478-105">Имена параметров определены в выражениях запросов с символом (@) в качестве префикса.</span><span class="sxs-lookup"><span data-stu-id="f4478-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="f4478-106">Так они отличаются от имен свойств или других имен, определенных в запросе.</span><span class="sxs-lookup"><span data-stu-id="f4478-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="f4478-107">API-привязки базового языка предоставляет API для параметров привязки.</span><span class="sxs-lookup"><span data-stu-id="f4478-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4478-108">Пример</span><span class="sxs-lookup"><span data-stu-id="f4478-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4478-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f4478-109">See also</span></span>

- [<span data-ttu-id="f4478-110">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4478-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f4478-111">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4478-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
