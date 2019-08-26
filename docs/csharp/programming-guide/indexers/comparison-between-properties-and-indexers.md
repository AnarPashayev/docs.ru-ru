---
title: Руководство по программированию на C#. Сравнение свойств и индексаторов
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589471"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="51b2b-102">Сравнение свойств и индексаторов (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="51b2b-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="51b2b-103">Индексаторы подобны свойствам.</span><span class="sxs-lookup"><span data-stu-id="51b2b-103">Indexers are like properties.</span></span> <span data-ttu-id="51b2b-104">К методам доступа индексаторов применяются те же правила, которые определены для методов доступа к свойствам, за исключением различий, показанных в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="51b2b-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="51b2b-105">Свойство.</span><span class="sxs-lookup"><span data-stu-id="51b2b-105">Property</span></span>|<span data-ttu-id="51b2b-106">Индексатор</span><span class="sxs-lookup"><span data-stu-id="51b2b-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="51b2b-107">Позволяет вызывать методы как открытые члены данных.</span><span class="sxs-lookup"><span data-stu-id="51b2b-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="51b2b-108">Обеспечивает доступ к элементам внутренней коллекции объекта с использованием нотации массива для самого объекта.</span><span class="sxs-lookup"><span data-stu-id="51b2b-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="51b2b-109">Доступ по простому имени.</span><span class="sxs-lookup"><span data-stu-id="51b2b-109">Accessed through a simple name.</span></span>|<span data-ttu-id="51b2b-110">Доступ посредством индекса.</span><span class="sxs-lookup"><span data-stu-id="51b2b-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="51b2b-111">Может быть статическим членом или членом экземпляра.</span><span class="sxs-lookup"><span data-stu-id="51b2b-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="51b2b-112">Должен быть членом экземпляра.</span><span class="sxs-lookup"><span data-stu-id="51b2b-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="51b2b-113">Метод доступа [get](../../language-reference/keywords/get.md) свойства не имеет параметров.</span><span class="sxs-lookup"><span data-stu-id="51b2b-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="51b2b-114">Метод доступа `get` индексатора имеет тот же список формальных параметров, что и сам индексатор.</span><span class="sxs-lookup"><span data-stu-id="51b2b-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="51b2b-115">Метод доступа [set](../../language-reference/keywords/set.md) свойства содержит неявный параметр `value`.</span><span class="sxs-lookup"><span data-stu-id="51b2b-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="51b2b-116">Метод доступа `set` индексатора имеет тот же список формальных параметров, что и сам индексатор, и также должен содержать параметр [value](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="51b2b-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="51b2b-117">Поддерживает сокращенный синтаксис с использованием [автоматически реализуемых свойств](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="51b2b-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="51b2b-118">Поддерживает элементы в виде выражения для индексаторов только для получения.</span><span class="sxs-lookup"><span data-stu-id="51b2b-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51b2b-119">См. также</span><span class="sxs-lookup"><span data-stu-id="51b2b-119">See also</span></span>

- [<span data-ttu-id="51b2b-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="51b2b-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51b2b-121">Индексаторы</span><span class="sxs-lookup"><span data-stu-id="51b2b-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="51b2b-122">Свойства</span><span class="sxs-lookup"><span data-stu-id="51b2b-122">Properties</span></span>](../classes-and-structs/properties.md)
