---
title: Начало работы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 6f9592ecebdaaac7cdec60ce12e99b910275d553
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490054"
---
# <a name="getting-started"></a><span data-ttu-id="96ffb-102">Начало работы</span><span class="sxs-lookup"><span data-stu-id="96ffb-102">Getting Started</span></span>
<span data-ttu-id="96ffb-103">С помощью [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], можно использовать [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] технологии для доступа к SQL базы данных, так же, как вы к коллекции в памяти.</span><span class="sxs-lookup"><span data-stu-id="96ffb-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="96ffb-104">В следующем примере кода создается объект `nw` для представления базы данных `Northwind`, выполняется запрос к таблице `Customers`, фильтруются строки для поиска клиентов (`Customers`) из Лондона (`London`) и выбирается строка `CompanyName` для извлечения.</span><span class="sxs-lookup"><span data-stu-id="96ffb-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="96ffb-105">При выполнении цикла извлекается коллекция значений `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="96ffb-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="96ffb-106">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="96ffb-106">Next Steps</span></span>  
 <span data-ttu-id="96ffb-107">Дополнительные примеры, включая вставки и обновления, см. в разделе [что вам можно делать с помощью LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="96ffb-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="96ffb-108">Далее ознакомьтесь с некоторыми пошаговыми руководствами и учебниками, чтобы получить практический навык работы с [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96ffb-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="96ffb-109">См. в разделе [обучения с использованием пошаговых руководств](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="96ffb-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="96ffb-110">Наконец, узнайте, как приступить к разработке собственных [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] проекта путем чтения [стандартная последовательность действий с помощью LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="96ffb-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ffb-111">См. также</span><span class="sxs-lookup"><span data-stu-id="96ffb-111">See also</span></span>

- [<span data-ttu-id="96ffb-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="96ffb-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="96ffb-113">Введение в LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="96ffb-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="96ffb-114">Знакомство с LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96ffb-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="96ffb-115">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="96ffb-115">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
