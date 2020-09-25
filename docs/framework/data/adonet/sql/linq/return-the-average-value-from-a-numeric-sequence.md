---
title: Возврат среднего значения из числовой последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 1f113a475bb350640aef7a6b4d7a70b32509d1e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200411"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="58d5a-102">Возврат среднего значения из числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="58d5a-102">Return the Average Value From a Numeric Sequence</span></span>

<span data-ttu-id="58d5a-103">Оператор <xref:System.Linq.Enumerable.Average%2A> вычисляет среднее последовательности числовых значений.</span><span class="sxs-lookup"><span data-stu-id="58d5a-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58d5a-104">Преобразование [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для оператора `Average`, вычисляющего среднее значение целых чисел, возвращает целое число, а не число двойной точности.</span><span class="sxs-lookup"><span data-stu-id="58d5a-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58d5a-105">Пример</span><span class="sxs-lookup"><span data-stu-id="58d5a-105">Example</span></span>  

 <span data-ttu-id="58d5a-106">В следующем примере вычисляется среднее для значений `Freight` из таблицы `Orders`.</span><span class="sxs-lookup"><span data-stu-id="58d5a-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="58d5a-107">Для образца базы данных Northwind результатом будет `78.2442`.</span><span class="sxs-lookup"><span data-stu-id="58d5a-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="58d5a-108">Пример</span><span class="sxs-lookup"><span data-stu-id="58d5a-108">Example</span></span>  

 <span data-ttu-id="58d5a-109">Следующий пример возвращает среднее значение цены единицы для всех `Products` в таблице `Products`.</span><span class="sxs-lookup"><span data-stu-id="58d5a-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="58d5a-110">Для образца базы данных Northwind результатом будет `28.8663`.</span><span class="sxs-lookup"><span data-stu-id="58d5a-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="58d5a-111">Пример</span><span class="sxs-lookup"><span data-stu-id="58d5a-111">Example</span></span>  

 <span data-ttu-id="58d5a-112">В следующем примере используется оператор `Average` для поиска тех продуктов `Products`, цена единицы товара для которых выше среднего значения цены единицы товара для содержащей их категории.</span><span class="sxs-lookup"><span data-stu-id="58d5a-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="58d5a-113">Затем выполняется отображение групп результатов.</span><span class="sxs-lookup"><span data-stu-id="58d5a-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="58d5a-114">Обратите внимание, что в этом примере требуется использовать ключевое слово `var` языка C#, поскольку тип возвращаемого значения является анонимным.</span><span class="sxs-lookup"><span data-stu-id="58d5a-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="58d5a-115">Если выполнить этот пример для учебной базы данных "Northwind, результаты должны выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="58d5a-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="58d5a-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="58d5a-116">See also</span></span>

- [<span data-ttu-id="58d5a-117">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="58d5a-117">Aggregate Queries</span></span>](aggregate-queries.md)
