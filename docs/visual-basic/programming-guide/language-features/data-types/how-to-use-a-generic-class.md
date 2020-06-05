---
title: Практическое руководство. Использование универсального класса
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393848"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="6f473-102">Практическое руководство. Использование универсального класса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f473-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="6f473-103">Класс, принимающий *параметры типа*, называется *универсальным*.</span><span class="sxs-lookup"><span data-stu-id="6f473-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="6f473-104">При использовании универсального класса из него можно создать *сконструированный класс*, указав *аргумент типа* для каждого из этих параметров.</span><span class="sxs-lookup"><span data-stu-id="6f473-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="6f473-105">После этого можно объявить переменную типа сконструированного класса, а также создать экземпляр такого класса и присвоить его этой переменной.</span><span class="sxs-lookup"><span data-stu-id="6f473-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="6f473-106">Помимо классов, можно определять и использовать универсальные структуры, интерфейсы, процедуры и делегаты.</span><span class="sxs-lookup"><span data-stu-id="6f473-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="6f473-107">Следующая процедура принимает универсальный класс, определенный в .NET Framework, и создает из него экземпляр.</span><span class="sxs-lookup"><span data-stu-id="6f473-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="6f473-108">Использование класса, который принимает параметр типа</span><span class="sxs-lookup"><span data-stu-id="6f473-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="6f473-109">В начале исходного файла включите [оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) для импорта <xref:System.Collections.Generic?displayProperty=nameWithType> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="6f473-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6f473-110">Это позволяет ссылаться на класс <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> без полного определения, чтобы его можно отличить от других классов очереди, таких как <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f473-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="6f473-111">Создайте объект обычным способом, но добавьте `(Of type)` сразу после имени класса.</span><span class="sxs-lookup"><span data-stu-id="6f473-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="6f473-112">Следующий пример использует тот же класс (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) для создания двух объектов очереди, содержащих элементы различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="6f473-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="6f473-113">Он добавляет элементы в конец каждой очереди и затем удаляет и отображает элементы из начала каждой очереди.</span><span class="sxs-lookup"><span data-stu-id="6f473-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="6f473-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6f473-114">See also</span></span>

- [<span data-ttu-id="6f473-115">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6f473-115">Data Types</span></span>](index.md)
- [<span data-ttu-id="6f473-116">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f473-116">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="6f473-117">Независимость от языка и независимые от языка компоненты</span><span class="sxs-lookup"><span data-stu-id="6f473-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="6f473-118">Окна</span><span class="sxs-lookup"><span data-stu-id="6f473-118">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="6f473-119">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="6f473-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="6f473-120">Практическое руководство. Определение класса, реализующего одинаковую функциональность для разных типов данных</span><span class="sxs-lookup"><span data-stu-id="6f473-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="6f473-121">Итераторы</span><span class="sxs-lookup"><span data-stu-id="6f473-121">Iterators</span></span>](../../concepts/iterators.md)
