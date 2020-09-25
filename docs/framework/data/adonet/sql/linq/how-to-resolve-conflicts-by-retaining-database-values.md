---
title: Практическое руководство. Как разрешать конфликты параллелизма путем сохранения значений базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191701"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="c1050-102">Практическое руководство. Как разрешать конфликты параллелизма путем сохранения значений базы данных</span><span class="sxs-lookup"><span data-stu-id="c1050-102">How to: Resolve Conflicts by Retaining Database Values</span></span>

<span data-ttu-id="c1050-103">Чтобы согласовать различия между ожидаемыми и фактическими значениями базы данных до повторной отправки изменений, можно воспользоваться <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> для сохранения значений, найденных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="c1050-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="c1050-104">Текущие значения в объектной модели при этом перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="c1050-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="c1050-105">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1050-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1050-106">Во всех случаях запись на клиенте сначала обновляется путем извлечения обновленных данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="c1050-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="c1050-107">Это действие гарантирует успешное выполнение следующей попытки обновления при тех же проверках параллелизма.</span><span class="sxs-lookup"><span data-stu-id="c1050-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1050-108">Пример</span><span class="sxs-lookup"><span data-stu-id="c1050-108">Example</span></span>  

 <span data-ttu-id="c1050-109">В данном сценарии, когда Пользователь1 пытается отправить изменения, возникает исключение <xref:System.Data.Linq.ChangeConflictException>, поскольку Пользователь2 в это время изменил столбцы "Помощник" и "Отдел".</span><span class="sxs-lookup"><span data-stu-id="c1050-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="c1050-110">Эта ситуация представлена в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="c1050-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="c1050-111">Manager</span><span class="sxs-lookup"><span data-stu-id="c1050-111">Manager</span></span>|<span data-ttu-id="c1050-112">Помощник</span><span class="sxs-lookup"><span data-stu-id="c1050-112">Assistant</span></span>|<span data-ttu-id="c1050-113">отдел;</span><span class="sxs-lookup"><span data-stu-id="c1050-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c1050-114">Исходное состояние базы данных при отправке запросов Пользователем1 и Пользователем2.</span><span class="sxs-lookup"><span data-stu-id="c1050-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="c1050-115">Алексеи</span><span class="sxs-lookup"><span data-stu-id="c1050-115">Alfreds</span></span>|<span data-ttu-id="c1050-116">Мария</span><span class="sxs-lookup"><span data-stu-id="c1050-116">Maria</span></span>|<span data-ttu-id="c1050-117">Sales</span><span class="sxs-lookup"><span data-stu-id="c1050-117">Sales</span></span>|  
|<span data-ttu-id="c1050-118">Пользователь1 готовится отправить изменения.</span><span class="sxs-lookup"><span data-stu-id="c1050-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="c1050-119">Алексей</span><span class="sxs-lookup"><span data-stu-id="c1050-119">Alfred</span></span>||<span data-ttu-id="c1050-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="c1050-120">Marketing</span></span>|  
|<span data-ttu-id="c1050-121">Пользователь2 уже отправил изменения.</span><span class="sxs-lookup"><span data-stu-id="c1050-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="c1050-122">Инна</span><span class="sxs-lookup"><span data-stu-id="c1050-122">Mary</span></span>|<span data-ttu-id="c1050-123">Служба</span><span class="sxs-lookup"><span data-stu-id="c1050-123">Service</span></span>|  
  
 <span data-ttu-id="c1050-124">Пользователь1 решает устранить этот конфликт путем перезаписи текущих значений из объектной модели более новыми значениями базы данных.</span><span class="sxs-lookup"><span data-stu-id="c1050-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="c1050-125">При устранении Пользователем1 конфликта с помощью <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> результат в базе данных будет соответствовать данным в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="c1050-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="c1050-126">Manager</span><span class="sxs-lookup"><span data-stu-id="c1050-126">Manager</span></span>|<span data-ttu-id="c1050-127">Помощник</span><span class="sxs-lookup"><span data-stu-id="c1050-127">Assistant</span></span>|<span data-ttu-id="c1050-128">отдел;</span><span class="sxs-lookup"><span data-stu-id="c1050-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c1050-129">Новое состояние после устранения конфликта.</span><span class="sxs-lookup"><span data-stu-id="c1050-129">New state after conflict resolution.</span></span>|<span data-ttu-id="c1050-130">Алексеи</span><span class="sxs-lookup"><span data-stu-id="c1050-130">Alfreds</span></span><br /><br /> <span data-ttu-id="c1050-131">(исходное значение)</span><span class="sxs-lookup"><span data-stu-id="c1050-131">(original)</span></span>|<span data-ttu-id="c1050-132">Инна</span><span class="sxs-lookup"><span data-stu-id="c1050-132">Mary</span></span><br /><br /> <span data-ttu-id="c1050-133">(от Пользователя2)</span><span class="sxs-lookup"><span data-stu-id="c1050-133">(from User2)</span></span>|<span data-ttu-id="c1050-134">Служба</span><span class="sxs-lookup"><span data-stu-id="c1050-134">Service</span></span><br /><br /> <span data-ttu-id="c1050-135">(от Пользователя2)</span><span class="sxs-lookup"><span data-stu-id="c1050-135">(from User2)</span></span>|  
  
 <span data-ttu-id="c1050-136">В следующем примере кода показано, как перезаписать текущие значения из объектной модели значениями базы данных</span><span class="sxs-lookup"><span data-stu-id="c1050-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="c1050-137">(проверка или пользовательская обработка конфликтов отдельных членов не выполняется).</span><span class="sxs-lookup"><span data-stu-id="c1050-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c1050-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c1050-138">See also</span></span>

- [<span data-ttu-id="c1050-139">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="c1050-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
