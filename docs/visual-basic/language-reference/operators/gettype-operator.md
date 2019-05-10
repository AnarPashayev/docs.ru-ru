---
title: Оператор GetType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 3366a0d1a90667cf1d9b58b211892ad264849c59
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633231"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="fa115-102">Оператор GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa115-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="fa115-103">Возвращает <xref:System.Type> объекта для указанного типа.</span><span class="sxs-lookup"><span data-stu-id="fa115-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="fa115-104"><xref:System.Type> Объект предоставляет сведения о типе, например его свойства, методы и события.</span><span class="sxs-lookup"><span data-stu-id="fa115-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa115-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa115-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa115-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fa115-106">Parameters</span></span>  
  
|<span data-ttu-id="fa115-107">Параметр</span><span class="sxs-lookup"><span data-stu-id="fa115-107">Parameter</span></span>|<span data-ttu-id="fa115-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fa115-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="fa115-109">Имя типа, для которого необходимы сведения.</span><span class="sxs-lookup"><span data-stu-id="fa115-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa115-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="fa115-110">Remarks</span></span>  
 <span data-ttu-id="fa115-111">`GetType` Оператор возвращает <xref:System.Type> для указанного `typename`.</span><span class="sxs-lookup"><span data-stu-id="fa115-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="fa115-112">Можно передать имя любого типа в `typename`.</span><span class="sxs-lookup"><span data-stu-id="fa115-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="fa115-113">Это поведение характеризуется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fa115-113">This includes the following:</span></span>  
  
- <span data-ttu-id="fa115-114">Любой Visual Basic тип данных, таких как `Boolean` или `Date`.</span><span class="sxs-lookup"><span data-stu-id="fa115-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="fa115-115">Любой платформы .NET Framework класс, структура, модуль или интерфейс, такие как <xref:System.ArgumentException?displayProperty=nameWithType> или <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa115-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="fa115-116">Любой класс, структура, модуль или интерфейс, определяемый приложением.</span><span class="sxs-lookup"><span data-stu-id="fa115-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="fa115-117">Любой массив, определяемый приложением.</span><span class="sxs-lookup"><span data-stu-id="fa115-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="fa115-118">Любому делегату, заданных вашим приложением.</span><span class="sxs-lookup"><span data-stu-id="fa115-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="fa115-119">Любое перечисление, определенное в Visual Basic, .NET Framework или приложения.</span><span class="sxs-lookup"><span data-stu-id="fa115-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="fa115-120">Если вы хотите получить объект типа переменной объекта, используйте <xref:System.Type.GetType%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="fa115-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fa115-121">`GetType` Оператор может быть полезно в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="fa115-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="fa115-122">Доступ к метаданным для типа необходимо во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa115-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="fa115-123"><xref:System.Type> Предоставляет метаданные, такие как члены типа и сведения о развертывании.</span><span class="sxs-lookup"><span data-stu-id="fa115-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="fa115-124">Это необходимо, например, чтобы отобразить сборку.</span><span class="sxs-lookup"><span data-stu-id="fa115-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="fa115-125">Дополнительные сведения см. в разделе <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa115-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="fa115-126">Вы хотите сравнить две объектные ссылки, чтобы увидеть, если они относятся к экземплярам того же типа.</span><span class="sxs-lookup"><span data-stu-id="fa115-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="fa115-127">Если это так, `GetType` возвращает ссылки на один и тот же <xref:System.Type> объекта.</span><span class="sxs-lookup"><span data-stu-id="fa115-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa115-128">Пример</span><span class="sxs-lookup"><span data-stu-id="fa115-128">Example</span></span>  
 <span data-ttu-id="fa115-129">В приведенных ниже примерах `GetType` оператор используется.</span><span class="sxs-lookup"><span data-stu-id="fa115-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="fa115-130">См. также</span><span class="sxs-lookup"><span data-stu-id="fa115-130">See also</span></span>

- [<span data-ttu-id="fa115-131">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa115-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="fa115-132">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="fa115-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="fa115-133">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="fa115-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
