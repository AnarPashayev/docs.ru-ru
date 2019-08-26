---
title: Руководство по программированию на C#. Свойства интерфейса
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596450"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="a3b63-102">Свойства интерфейса (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="a3b63-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="a3b63-103">Свойства можно объявлять для [интерфейса](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="a3b63-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="a3b63-104">Ниже показан пример метода доступа к свойству интерфейса:</span><span class="sxs-lookup"><span data-stu-id="a3b63-104">The following is an example of an interface property accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 <span data-ttu-id="a3b63-105">Метод доступа свойства интерфейса не имеет тела.</span><span class="sxs-lookup"><span data-stu-id="a3b63-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="a3b63-106">Таким образом, методы доступа нужны, чтобы указать, доступно ли свойство для чтения и записи, только для чтения или только для записи.</span><span class="sxs-lookup"><span data-stu-id="a3b63-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3b63-107">Пример</span><span class="sxs-lookup"><span data-stu-id="a3b63-107">Example</span></span>  
 <span data-ttu-id="a3b63-108">В этом примере интерфейс `IEmployee` содержит доступное для чтения и записи свойство `Name`, а также свойство `Counter`, предназначенное только для чтения.</span><span class="sxs-lookup"><span data-stu-id="a3b63-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="a3b63-109">Класс `Employee` реализует интерфейс `IEmployee` и использует эти два свойства.</span><span class="sxs-lookup"><span data-stu-id="a3b63-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="a3b63-110">Программа считывает имя нового сотрудника и текущее число сотрудников, после чего отображает имя сотрудника и его рассчитанный номер.</span><span class="sxs-lookup"><span data-stu-id="a3b63-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="a3b63-111">Вы можете использовать полное имя свойства, которое ссылается на интерфейс, где был объявлен член.</span><span class="sxs-lookup"><span data-stu-id="a3b63-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="a3b63-112">Например:</span><span class="sxs-lookup"><span data-stu-id="a3b63-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="a3b63-113">Это называется [явной реализацией интерфейса](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="a3b63-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="a3b63-114">Например, если класс `Employee` реализует два интерфейса (`ICitizen` и `IEmployee`), оба из которых содержат свойство `Name`, потребуется явная реализация члена интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a3b63-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="a3b63-115">Это значит, что потребуется следующее объявление свойства:</span><span class="sxs-lookup"><span data-stu-id="a3b63-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="a3b63-116">реализует свойство `Name` в интерфейсе `IEmployee`, тогда как следующее объявление:</span><span class="sxs-lookup"><span data-stu-id="a3b63-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 <span data-ttu-id="a3b63-117">реализует свойство `Name` в интерфейсе `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="a3b63-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="a3b63-118">Пример результатов выполнения</span><span class="sxs-lookup"><span data-stu-id="a3b63-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="a3b63-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a3b63-119">See also</span></span>

- [<span data-ttu-id="a3b63-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="a3b63-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a3b63-121">Свойства</span><span class="sxs-lookup"><span data-stu-id="a3b63-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a3b63-122">Использование свойств</span><span class="sxs-lookup"><span data-stu-id="a3b63-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="a3b63-123">Сравнение свойств и индексаторов</span><span class="sxs-lookup"><span data-stu-id="a3b63-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="a3b63-124">Индексаторы</span><span class="sxs-lookup"><span data-stu-id="a3b63-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="a3b63-125">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a3b63-125">Interfaces</span></span>](../interfaces/index.md)
