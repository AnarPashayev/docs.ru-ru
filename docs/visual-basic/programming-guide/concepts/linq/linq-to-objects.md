---
title: LINQ to Objects
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 004198f61569d50b608d002ab752e7381bf1368e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549833"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="9bdf3-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="9bdf3-103">Термин "LINQ to Objects" означает использование запросов LINQ с любой коллекцией <xref:System.Collections.IEnumerable> или <xref:System.Collections.Generic.IEnumerable%601> напрямую, без привлечения промежуточного поставщика LINQ, API [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) или [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9bdf3-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="9bdf3-104">Вы можете выполнить запрос LINQ к любой перечислимой коллекции, такой как <xref:System.Collections.Generic.List%601>, <xref:System.Array> или <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="9bdf3-105">Коллекция может быть определена пользователем или возвращена API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="9bdf3-106">В общем смысле LINQ to Objects представляет собой новый подход к коллекциям.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="9bdf3-107">Раньше нужно было написать сложные циклы `For Each`, определяющие порядок извлечения данных из коллекции.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="9bdf3-108">При использовании LINQ пишется декларативный код, описывающий, какие данные необходимо извлечь.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="9bdf3-109">Кроме того, запросы LINQ предлагают три основных преимущества по сравнению с традиционными циклами `For Each`:</span><span class="sxs-lookup"><span data-stu-id="9bdf3-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="9bdf3-110">Они более краткие и удобочитаемые, особенно при фильтрации нескольких условий.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="9bdf3-111">Они предоставляют широкие возможности фильтрации, упорядочивания и группировки с минимумом кода приложения.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="9bdf3-112">Они могут переноситься в другие источники данных практически без изменений.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="9bdf3-113">В общем, чем сложнее операция, которую нужно выполнить с данными, тем больше преимуществ вы получаете при использовании LINQ вместо традиционных способов итерации.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="9bdf3-114">Целью этого раздела является демонстрация подхода LINQ с помощью нескольких примеров.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="9bdf3-115">Он не претендует на исчерпывающий характер.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bdf3-116">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="9bdf3-116">In This Section</span></span>  
 [<span data-ttu-id="9bdf3-117">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="9bdf3-118">Использование LINQ для запроса и преобразования строк и коллекций строк.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="9bdf3-119">Ссылки на разделы, демонстрирующие эти принципы.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="9bdf3-120">LINQ и отражение (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-120">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="9bdf3-121">Ссылки на пример, демонстрирующий, как LINQ использует отражение.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="9bdf3-122">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-122">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="9bdf3-123">Использование LINQ для взаимодействия с файловыми системами.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="9bdf3-124">Ссылки на разделы, демонстрирующие эти понятия.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="9bdf3-125">Как выполнить запрос к ArrayList с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="9bdf3-126">Выполнение запроса ArrayList в C#.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="9bdf3-127">Как добавить пользовательские методы для запросов LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="9bdf3-128">Расширение набора методов, которые можно использовать для запросов LINQ путем добавления методов расширения в интерфейс <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="9bdf3-129">LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdf3-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="9bdf3-130">Ссылки на разделы, рассказывающие LINQ и содержащие примеры кода выполнения запросов.</span><span class="sxs-lookup"><span data-stu-id="9bdf3-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
