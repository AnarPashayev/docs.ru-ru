---
title: Практическое руководство. Объединение данных с помощью LINQ с использованием соединений (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 127e1afa7707f31584e93f3d4b08e865d7fcedf6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319603"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="3b0ca-102">Практическое руководство. Объединение данных с помощью LINQ с использованием соединений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b0ca-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="3b0ca-103">Visual Basic предоставляет `Join` и `Group Join` для объединения содержимого нескольких коллекций на основе общих значений между коллекциями предложения запроса.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="3b0ca-104">Эти значения называются *ключ* значения.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-104">These values are known as *key* values.</span></span> <span data-ttu-id="3b0ca-105">Разработчикам, знакомым с понятиями реляционной базы данных будет распознавать `Join` предложение INNER JOIN и `Group Join` предложение as, фактически, ЛЕВОЕ ВНЕШНЕЕ соединение.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="3b0ca-106">В примерах в этом разделе показано несколько способов объединения данных с помощью `Join` и `Group Join` предложения запроса.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="3b0ca-107">Создание проекта и добавление демонстрационных данных</span><span class="sxs-lookup"><span data-stu-id="3b0ca-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="3b0ca-108">Чтобы создать проект, содержащий образец данных и типы</span><span class="sxs-lookup"><span data-stu-id="3b0ca-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="3b0ca-109">Для выполнения примеров этого раздела, откройте Visual Studio и добавьте новый проект консольного приложения Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="3b0ca-110">Дважды щелкните файл Module1.vb, созданными Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="3b0ca-111">Примеры в этом разделе используется `Person` и `Pet` типы и данные из следующего примера кода.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="3b0ca-112">Скопируйте этот код в значение по умолчанию `Module1` модуля, созданного с Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="3b0ca-113">Выполнение внутреннего соединения с помощью предложения Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="3b0ca-114">ВНУТРЕННЕЕ соединение объединяет данные из двух коллекций.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="3b0ca-115">Включены элементы, для которых соответствует указанных значений ключа.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="3b0ca-116">Все элементы из любой коллекции, у которых нет соответствующего элемента в другой коллекции, исключаются.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="3b0ca-117">В Visual Basic LINQ предоставляет два параметра для выполнения внутреннего СОЕДИНЕНИЯ: неявное соединение и явное соединение.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="3b0ca-118">Неявное соединение задает коллекции для объединения в `From` предложение и определяет соответствующие ключевые поля в `Where` предложение.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="3b0ca-119">Visual Basic неявно объединяет две коллекции, на основе указанного ключа полей.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="3b0ca-120">Явное соединение можно указать с помощью `Join` предложение, если вы хотите явно указать, какие ключевые поля для использования в соединении.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="3b0ca-121">В этом случае `Where` предложение по-прежнему может использоваться для фильтрации результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="3b0ca-122">Для выполнения Inner Join с помощью предложения Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="3b0ca-123">Добавьте следующий код, чтобы `Module1` модуля в проект, чтобы ознакомиться с примерами явные и неявные внутреннее соединение.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="3b0ca-124">Выполнить левое внешнее соединение, используя предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="3b0ca-125">ЛЕВОЕ ВНЕШНЕЕ соединение включает в себя все элементы из коллекции слева от оператора соединения и только совпадающие значения из коллекции правой стороны соединения.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="3b0ca-126">Все элементы из коллекции правой части соединения, у которых нет соответствующего элемента в коллекции слева от оператора, исключаются из результата запроса.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="3b0ca-127">`Group Join` Предложение выполняет, по сути, LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="3b0ca-128">Разница между обычно называемое ЛЕВОЕ ВНЕШНЕЕ соединение и что `Group Join` предложение возвращает, является то, что `Group Join` результаты предложения группы из коллекции правой стороны соединения для каждого элемента коллекции слева от оператора.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="3b0ca-129">В реляционной базе данных ЛЕВОЕ ВНЕШНЕЕ соединение возвращает результат без группировки, в котором каждый элемент в запросе привести содержит совпадающие элементы из обеих коллекций в соединении.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="3b0ca-130">В этом случае элементы из коллекции слева от оператора соединения повторяются для каждого соответствующего элемента из коллекции справа.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="3b0ca-131">Вы увидите, как это выглядит после завершения следующей процедуры.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="3b0ca-132">Результаты можно получить `Group Join` запроса в виде результата без группировки, расширяя запрос для возврата элемента для каждого сгруппированного результата запроса.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="3b0ca-133">Чтобы выполнить это, необходимо убедиться, что выполняется запрос для `DefaultIfEmpty` метод сгруппированных коллекции.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="3b0ca-134">Это гарантирует, что элементы из коллекции слева от оператора соединения по-прежнему включены в результат запроса, даже если они не имеют совпадающих из коллекции справа.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="3b0ca-135">Можно добавить код к запросу для предоставления результирующее значение по умолчанию при отсутствии совпадающих значений из коллекции правой стороны соединения.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="3b0ca-136">Чтобы выполнить левое внешнее соединение, используя предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="3b0ca-137">Добавьте следующий код, чтобы `Module1` модуля проекта, чтобы просмотреть примеры сгруппированного левого внешнего соединения и несгруппированные левого внешнего соединения.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="3b0ca-138">Выполнение соединения с помощью составного ключа</span><span class="sxs-lookup"><span data-stu-id="3b0ca-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="3b0ca-139">Можно использовать `And` ключевое слово в `Join` или `Group Join` предложение, чтобы определить несколько ключевых полей для использования при сопоставлении значения из соединяемых коллекций.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="3b0ca-140">`And` Ключевое слово указывает, что все указанные ключевые поля должны соответствовать элементам для объединения.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="3b0ca-141">Для соединения с помощью составного ключа</span><span class="sxs-lookup"><span data-stu-id="3b0ca-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="3b0ca-142">Добавьте следующий код, чтобы `Module1` модуль проекта, чтобы просмотреть примеры соединения, в которых используется составной ключ.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="3b0ca-143">Выполните код</span><span class="sxs-lookup"><span data-stu-id="3b0ca-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="3b0ca-144">Добавление кода для выполнения примеров</span><span class="sxs-lookup"><span data-stu-id="3b0ca-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="3b0ca-145">Замените `Sub Main` в `Module1` модуля в проекте следующим кодом, чтобы выполнить примеры в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="3b0ca-146">Нажмите клавишу F5 для запуска примеров.</span><span class="sxs-lookup"><span data-stu-id="3b0ca-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0ca-147">См. также</span><span class="sxs-lookup"><span data-stu-id="3b0ca-147">See also</span></span>

- [<span data-ttu-id="3b0ca-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="3b0ca-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3b0ca-149">Знакомство с LINQ в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b0ca-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3b0ca-150">Предложение Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="3b0ca-151">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="3b0ca-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="3b0ca-152">Предложение From</span><span class="sxs-lookup"><span data-stu-id="3b0ca-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3b0ca-153">Предложение Where</span><span class="sxs-lookup"><span data-stu-id="3b0ca-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="3b0ca-154">Запросы</span><span class="sxs-lookup"><span data-stu-id="3b0ca-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3b0ca-155">Преобразования данных с помощью LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3b0ca-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
