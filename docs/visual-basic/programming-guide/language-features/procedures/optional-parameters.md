---
title: Необязательные параметры
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4e07b75c94b4aea681e6e862e161bda80b2833fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364335"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="58622-102">Необязательные параметры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58622-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="58622-103">Некоторые аргументы процедуры можно задать как необязательные, тем самым указывая, что их можно не задавать при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="58622-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="58622-104">*Необязательные параметры* указываются с помощью `Optional` ключевого слова в определении процедуры.</span><span class="sxs-lookup"><span data-stu-id="58622-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="58622-105">Применяются следующие правила.</span><span class="sxs-lookup"><span data-stu-id="58622-105">The following rules apply:</span></span>  
  
- <span data-ttu-id="58622-106">Для каждого необязательного параметра в определении процедуры должно быть указано значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="58622-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
- <span data-ttu-id="58622-107">Значение по умолчанию для необязательного параметра следует задавать в виде константного выражения.</span><span class="sxs-lookup"><span data-stu-id="58622-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
- <span data-ttu-id="58622-108">Каждый параметр, идущий в определении процедуры после необязательного, также должен быть необязательным.</span><span class="sxs-lookup"><span data-stu-id="58622-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="58622-109">Ниже приведен синтаксис объявления процедуры с необязательным параметром:</span><span class="sxs-lookup"><span data-stu-id="58622-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="58622-110">Вызов процедур с необязательными параметрами</span><span class="sxs-lookup"><span data-stu-id="58622-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="58622-111">При вызове процедуры с необязательным параметром можно опускать этот аргумент.</span><span class="sxs-lookup"><span data-stu-id="58622-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="58622-112">Если он не задан, процедура будет использовать значение по умолчанию, объявленное для параметра.</span><span class="sxs-lookup"><span data-stu-id="58622-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="58622-113">Можно опустить сразу несколько необязательных аргументов в списке аргументов, ставя несколько запятых подряд для обозначения их позиций.</span><span class="sxs-lookup"><span data-stu-id="58622-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="58622-114">Ниже приводится пример вызова процедуры, при котором задаются первый и четвертый аргументы, а второй и третий пропускаются.</span><span class="sxs-lookup"><span data-stu-id="58622-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="58622-115">В следующем примере происходит несколько вызовов функции `MsgBox`.</span><span class="sxs-lookup"><span data-stu-id="58622-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="58622-116">У функции `MsgBox` есть один обязательный параметр и два необязательных параметра.</span><span class="sxs-lookup"><span data-stu-id="58622-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="58622-117">При первом вызове `MsgBox` указываются все три аргумента в том порядке, в котором они определены в `MsgBox`.</span><span class="sxs-lookup"><span data-stu-id="58622-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="58622-118">При втором вызове указывается только обязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="58622-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="58622-119">При третьем и четвертом вызове указываются первый и третий аргументы.</span><span class="sxs-lookup"><span data-stu-id="58622-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="58622-120">Третий вызов указывает аргумент по позиции, а четвертый — по имени.</span><span class="sxs-lookup"><span data-stu-id="58622-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="58622-121">Определение наличия необязательного аргумента</span><span class="sxs-lookup"><span data-stu-id="58622-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="58622-122">Процедура во время выполнения не может отличить пропущенный аргумент от аргумента, для которого в вызывающем коде явным образом задано значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="58622-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="58622-123">Если такое различение существенно, можно задать в качестве значения по умолчанию значение, которое вряд ли будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="58622-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="58622-124">Следующая процедура определяет необязательный параметр `office` и проверяет его значение по умолчанию, `QJZ` чтобы определить, пропущен ли он в вызове:</span><span class="sxs-lookup"><span data-stu-id="58622-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 <span data-ttu-id="58622-125">Если необязательный параметр имеет ссылочный тип, например, `String`, то можно использовать `Nothing` в качестве значения по умолчанию, при условии, что это не является ожидаемым значением аргумента.</span><span class="sxs-lookup"><span data-stu-id="58622-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="58622-126">Необязательные параметры и перегрузка</span><span class="sxs-lookup"><span data-stu-id="58622-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="58622-127">Другой способ определения процедуры с необязательными параметрами состоит в использовании перегрузки.</span><span class="sxs-lookup"><span data-stu-id="58622-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="58622-128">Если имеется один необязательный параметр, то можно определить две перегруженные версии процедуры, одна принимает параметр, а другая — нет.</span><span class="sxs-lookup"><span data-stu-id="58622-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="58622-129">Такой подход становится более сложным с увеличением числа необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="58622-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="58622-130">Однако, его преимущество заключается в том, что он позволяет точно знать, все ли необязательные аргументы заданы в вызывающей программе.</span><span class="sxs-lookup"><span data-stu-id="58622-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58622-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="58622-131">See also</span></span>

- [<span data-ttu-id="58622-132">Процедуры</span><span class="sxs-lookup"><span data-stu-id="58622-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="58622-133">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="58622-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="58622-134">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="58622-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="58622-135">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="58622-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="58622-136">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="58622-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="58622-137">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="58622-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="58622-138">Необязательно</span><span class="sxs-lookup"><span data-stu-id="58622-138">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="58622-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="58622-139">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
