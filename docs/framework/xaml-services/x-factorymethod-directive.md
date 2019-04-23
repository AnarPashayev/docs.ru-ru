---
title: Директива x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 8fff4d62e07bdfd4ecc27d2692c391251afdd6d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190695"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="8d0af-102">Директива x:FactoryMethod</span><span class="sxs-lookup"><span data-stu-id="8d0af-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="8d0af-103">Указывает метод, отличный от конструктора, который процессор XAML должен использовать для инициализации объекта после разрешения его резервного типа.</span><span class="sxs-lookup"><span data-stu-id="8d0af-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="8d0af-104">Использование атрибута XAML, не x: Arguments</span><span class="sxs-lookup"><span data-stu-id="8d0af-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="8d0af-105">Использование атрибута XAML, x: Arguments, как элементы</span><span class="sxs-lookup"><span data-stu-id="8d0af-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8d0af-106">Значения XAML</span><span class="sxs-lookup"><span data-stu-id="8d0af-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="8d0af-107">Метод строковое имя метода, который вызывают процессоры XAML для инициализации экземпляра, заданного как `object`.</span><span class="sxs-lookup"><span data-stu-id="8d0af-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="8d0af-108">См. заметки.</span><span class="sxs-lookup"><span data-stu-id="8d0af-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="8d0af-109">Один или несколько элементов объекта для объектов, которые указывают параметры метода фабрики.</span><span class="sxs-lookup"><span data-stu-id="8d0af-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="8d0af-110">Порядок имеет значение; обозначает порядок, в котором аргументы должны быть переданы в метод фабрики.</span><span class="sxs-lookup"><span data-stu-id="8d0af-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d0af-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="8d0af-111">Remarks</span></span>  
 <span data-ttu-id="8d0af-112">Если `methodname` является методом экземпляра не может быть задан.</span><span class="sxs-lookup"><span data-stu-id="8d0af-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="8d0af-113">Поддерживаются статические методы как фабричные методы.</span><span class="sxs-lookup"><span data-stu-id="8d0af-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="8d0af-114">Если `methodname` — это статический метод `methodname` предоставляется в качестве *typeName*. *имя_метода* сочетания, где *typeName* содержит класс, который определяет статический фабричный метод.</span><span class="sxs-lookup"><span data-stu-id="8d0af-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="8d0af-115">*typeName* может иметь префикс, если ссылается на тип в сопоставленных xmlns.</span><span class="sxs-lookup"><span data-stu-id="8d0af-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="8d0af-116">*typeName* может быть тип, отличный от `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="8d0af-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="8d0af-117">Метод фабрики должен быть объявлен открытым методом типа, который возвращает соответствующий элемент объекта.</span><span class="sxs-lookup"><span data-stu-id="8d0af-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="8d0af-118">Фабричный метод должен возвращать экземпляр, который может быть назначен соответствующего объекта.</span><span class="sxs-lookup"><span data-stu-id="8d0af-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="8d0af-119">Фабричные методы не должны возвращать значение null.</span><span class="sxs-lookup"><span data-stu-id="8d0af-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="8d0af-120">`x:Arguments` работает по принципу наилучшего соответствия для сигнатуры методов фабрики.</span><span class="sxs-lookup"><span data-stu-id="8d0af-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="8d0af-121">Сопоставление оценивается число параметров.</span><span class="sxs-lookup"><span data-stu-id="8d0af-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="8d0af-122">Если имеется более одного возможного соответствия для числа параметров, тип параметра — а затем определяется соответствие вычисляется и рекомендации.</span><span class="sxs-lookup"><span data-stu-id="8d0af-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="8d0af-123">Если после этого этапа оценки остается неоднозначность, поведение обработчика XAML не определено.</span><span class="sxs-lookup"><span data-stu-id="8d0af-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="8d0af-124">`x:FactoryMethod` Использование элемента не использование элемента свойства, в том смысле, типичный, так как директив разметки не ссылается на объект элемента, содержащего типа.</span><span class="sxs-lookup"><span data-stu-id="8d0af-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="8d0af-125">Предполагается, что элементы используются реже, чем использование атрибута.</span><span class="sxs-lookup"><span data-stu-id="8d0af-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="8d0af-126">`x:Arguments` (использование атрибута или элемента) можно использовать вместе с `x:FactoryMethod` использование элемента, но это не отображается в разделах об использовании.</span><span class="sxs-lookup"><span data-stu-id="8d0af-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="8d0af-127">`x:FactoryMethod` как элемент должен предшествовать любых других элементов свойств, должны указываться до любой `x:Arguments` также указанные в качестве элементов и должен предшествовать любой текст содержимого "и" внутренний текст/инициализации.</span><span class="sxs-lookup"><span data-stu-id="8d0af-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0af-128">См. также</span><span class="sxs-lookup"><span data-stu-id="8d0af-128">See also</span></span>

- [<span data-ttu-id="8d0af-129">x:Arguments - директива</span><span class="sxs-lookup"><span data-stu-id="8d0af-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
