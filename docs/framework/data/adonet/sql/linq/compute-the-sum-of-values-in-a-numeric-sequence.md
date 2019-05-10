---
title: Вычисление суммы значений в числовой последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 978b02e9363a89c5bd007afc1960bd2a2d0ca0d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592550"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="a4da8-102">Вычисление суммы значений в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="a4da8-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="a4da8-103">Для вычисления суммы значений в последовательности чисел используется оператор <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4da8-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="a4da8-104">Обратите внимание на следующие характеристики оператора `Sum` в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4da8-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="a4da8-105">Для пустой последовательности или последовательности, содержащей только значения NULL, значением агрегатного оператора стандартного оператора запроса `Sum` является ноль.</span><span class="sxs-lookup"><span data-stu-id="a4da8-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="a4da8-106">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] семантики SQL остаются неизменными.</span><span class="sxs-lookup"><span data-stu-id="a4da8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="a4da8-107">Поэтому для пустой последовательности или последовательности, содержащей только значения NULL, значением`Sum` является NULL.</span><span class="sxs-lookup"><span data-stu-id="a4da8-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="a4da8-108">Ограничения SQL для промежуточных результатов применяются к агрегатным выражениям в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4da8-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a4da8-109">Сумма 32-разрядных целых чисел не вычисляется с помощью 64-разрядных вычислений и может произойти переполнение для [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] перевод `Sum`.</span><span class="sxs-lookup"><span data-stu-id="a4da8-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="a4da8-110">Такая возможность существует, даже если реализация стандартного оператора запроса не вызывает переполнения для соответствующей последовательности в памяти.</span><span class="sxs-lookup"><span data-stu-id="a4da8-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4da8-111">Пример</span><span class="sxs-lookup"><span data-stu-id="a4da8-111">Example</span></span>  
 <span data-ttu-id="a4da8-112">В следующем примере вычисляется общая стоимость доставки всех заказов в таблице `Order`.</span><span class="sxs-lookup"><span data-stu-id="a4da8-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="a4da8-113">Если выполнить этот запрос в образце базы данных Northwind, то будут получены следующие выходные данные: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="a4da8-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="a4da8-114">Пример</span><span class="sxs-lookup"><span data-stu-id="a4da8-114">Example</span></span>  
 <span data-ttu-id="a4da8-115">В следующем примере вычисляется общее число заказанных элементов для всех продуктов.</span><span class="sxs-lookup"><span data-stu-id="a4da8-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="a4da8-116">Если выполнить этот запрос в образце базы данных Northwind, то будут получены следующие выходные данные: `780`.</span><span class="sxs-lookup"><span data-stu-id="a4da8-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="a4da8-117">Обратите внимание на необходимость приведения типов `short` (например, `UnitsOnOrder`), поскольку `Sum` не имеет перегрузки для коротких типов.</span><span class="sxs-lookup"><span data-stu-id="a4da8-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="a4da8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a4da8-118">See also</span></span>

- [<span data-ttu-id="a4da8-119">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="a4da8-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="a4da8-120">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="a4da8-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
