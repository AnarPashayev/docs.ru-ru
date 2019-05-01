---
title: Именование параметров
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026315"
---
# <a name="naming-parameters"></a><span data-ttu-id="8ce8f-102">Именование параметров</span><span class="sxs-lookup"><span data-stu-id="8ce8f-102">Naming Parameters</span></span>
<span data-ttu-id="8ce8f-103">Помимо очевидная причина восприятия очень важно следовать рекомендациям для имен параметров, так как параметры отображаются в документации и в конструкторе, когда средства визуального проектирования предоставляют Intellisense и функции просмотра классов.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="8ce8f-104">**✓ DO** использовать camelCasing в именах параметров.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="8ce8f-105">**✓ DO** использовать описательные имена параметров.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="8ce8f-106">**✓ CONSIDER** с помощью имен, основываясь на назначение параметра, а не тип параметра.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="8ce8f-107">Именование параметров перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="8ce8f-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="8ce8f-108">**✓ DO** использовать `left` и `right` для имен параметров перегрузку бинарного оператора, если нет никакого значения для параметров.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="8ce8f-109">**✓ DO** использовать `value` унарный оператор перегрузка для имен параметров при наличии не значения для параметров.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="8ce8f-110">**✓ CONSIDER** значимые имена для оператора перегружать параметров, если это добавляет особого значения.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="8ce8f-111">**X DO NOT** использования сокращений и числовые индексы для оператора перегрузки имена параметров.</span><span class="sxs-lookup"><span data-stu-id="8ce8f-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="8ce8f-112">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="8ce8f-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8ce8f-113">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8ce8f-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce8f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8ce8f-114">See also</span></span>

- [<span data-ttu-id="8ce8f-115">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="8ce8f-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8ce8f-116">Правила именования</span><span class="sxs-lookup"><span data-stu-id="8ce8f-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
