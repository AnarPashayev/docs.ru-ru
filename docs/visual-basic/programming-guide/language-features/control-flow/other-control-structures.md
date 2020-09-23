---
title: Другие структуры управления
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 8e7ca699e532ac7cfbe7918d850e7a28d1b27bcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058616"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="81f9e-102">Другие структуры управления (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f9e-102">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="81f9e-103">Visual Basic предоставляет управляющие структуры, которые помогают удалить ресурс или сократить количество повторных ссылок на объект.</span><span class="sxs-lookup"><span data-stu-id="81f9e-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="81f9e-104">Использование... Завершить с помощью конструкции</span><span class="sxs-lookup"><span data-stu-id="81f9e-104">Using...End Using Construction</span></span>  

 <span data-ttu-id="81f9e-105">`Using...End Using`Конструкция устанавливает блок инструкций, в рамках которого используется ресурс, например соединение SQL.</span><span class="sxs-lookup"><span data-stu-id="81f9e-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="81f9e-106">При необходимости можно получить ресурс с помощью `Using` инструкции.</span><span class="sxs-lookup"><span data-stu-id="81f9e-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="81f9e-107">При выходе из `Using` блока Visual Basic автоматически уничтожает ресурс, чтобы он был доступен для использования другим кодом.</span><span class="sxs-lookup"><span data-stu-id="81f9e-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="81f9e-108">Ресурс должен быть локальным и удаляемым.</span><span class="sxs-lookup"><span data-stu-id="81f9e-108">The resource must be local and disposable.</span></span> <span data-ttu-id="81f9e-109">Дополнительные сведения см. в разделе [оператор using](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="81f9e-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="81f9e-110">С помощью... Завершить конструкцию</span><span class="sxs-lookup"><span data-stu-id="81f9e-110">With...End With Construction</span></span>  

 <span data-ttu-id="81f9e-111">`With...End With`Конструкция позволяет указать ссылку на объект один раз, а затем выполнить последовательность инструкций, обращающихся к ее членам.</span><span class="sxs-lookup"><span data-stu-id="81f9e-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="81f9e-112">Это может упростить код и повысить производительность, поскольку Visual Basic не придется повторно устанавливать ссылку для каждой инструкции, которая обращается к ней.</span><span class="sxs-lookup"><span data-stu-id="81f9e-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="81f9e-113">Дополнительные сведения см [. в разделе with... Конец оператора](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="81f9e-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f9e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="81f9e-114">See also</span></span>

- [<span data-ttu-id="81f9e-115">Поток управления</span><span class="sxs-lookup"><span data-stu-id="81f9e-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="81f9e-116">Структуры решений</span><span class="sxs-lookup"><span data-stu-id="81f9e-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="81f9e-117">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="81f9e-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="81f9e-118">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="81f9e-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="81f9e-119">Оператор using</span><span class="sxs-lookup"><span data-stu-id="81f9e-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="81f9e-120">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="81f9e-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
