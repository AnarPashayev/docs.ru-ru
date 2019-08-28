---
title: Руководство по программированию на C#. Закрытые конструкторы
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: faa5132845a2d463d3b7d74dc0e0cce21dca61aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596210"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="85e98-102">Закрытые конструкторы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="85e98-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="85e98-103">Закрытый конструктор — это особый конструктор экземпляров.</span><span class="sxs-lookup"><span data-stu-id="85e98-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="85e98-104">Обычно он используется в классах, содержащих только статические элементы.</span><span class="sxs-lookup"><span data-stu-id="85e98-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="85e98-105">Если в классе один или несколько закрытых конструкторов и ни одного открытого конструктора, то прочие классы (за исключением вложенных классов) не смогут создавать экземпляры этого класса.</span><span class="sxs-lookup"><span data-stu-id="85e98-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="85e98-106">Например:</span><span class="sxs-lookup"><span data-stu-id="85e98-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="85e98-107">Объявление пустого конструктора запрещает автоматическое создание конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="85e98-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="85e98-108">Обратите внимание, что если не использовать с конструктором модификатор доступа, то по умолчанию он все равно будет закрытым.</span><span class="sxs-lookup"><span data-stu-id="85e98-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="85e98-109">Однако обычно используется модификатор [private](../../language-reference/keywords/private.md), чтобы явно обозначить невозможность создания экземпляров этого класса.</span><span class="sxs-lookup"><span data-stu-id="85e98-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="85e98-110">Закрытые конструкторы используются, чтобы не допустить создания экземпляров класса при отсутствии полей или методов экземпляра, например для класса <xref:System.Math>, или когда осуществляется вызов метода для получения экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="85e98-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="85e98-111">Если все методы в классе являются статическими, имеет смысл сделать статическим весь класс.</span><span class="sxs-lookup"><span data-stu-id="85e98-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="85e98-112">Дополнительные сведения см. в разделе [Статические классы и члены статических классов](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="85e98-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85e98-113">Пример</span><span class="sxs-lookup"><span data-stu-id="85e98-113">Example</span></span>  
 <span data-ttu-id="85e98-114">Ниже приведен пример класса с закрытым конструктором.</span><span class="sxs-lookup"><span data-stu-id="85e98-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="85e98-115">Обратите внимание, что если в примере раскомментировать следующий оператор, возникнет ошибка, так как конструктор недоступен из-за уровня защиты:</span><span class="sxs-lookup"><span data-stu-id="85e98-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="85e98-116">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="85e98-116">C# Language Specification</span></span>  

<span data-ttu-id="85e98-117">Дополнительные сведения см. в разделе [Закрытые конструкторы](~/_csharplang/spec/classes.md#private-constructors) в [Спецификации языка C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="85e98-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="85e98-118">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="85e98-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85e98-119">См. также</span><span class="sxs-lookup"><span data-stu-id="85e98-119">See also</span></span>

- [<span data-ttu-id="85e98-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="85e98-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="85e98-121">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="85e98-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="85e98-122">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="85e98-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="85e98-123">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="85e98-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="85e98-124">private</span><span class="sxs-lookup"><span data-stu-id="85e98-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="85e98-125">public</span><span class="sxs-lookup"><span data-stu-id="85e98-125">public</span></span>](../../language-reference/keywords/public.md)
