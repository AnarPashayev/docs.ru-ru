---
title: Практическое руководство. Вызов перегруженной процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 68b8a9898cba846b63ed8ce9d8329516f12e90cb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075178"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="62b9e-102">Практическое руководство. Вызов перегруженной процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62b9e-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>

<span data-ttu-id="62b9e-103">Преимущество перегрузки процедуры заключается в гибкости вызова.</span><span class="sxs-lookup"><span data-stu-id="62b9e-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="62b9e-104">Вызывающий код может получить сведения, необходимые для передачи в процедуру, а затем вызвать одно имя процедуры независимо от передаваемых аргументов.</span><span class="sxs-lookup"><span data-stu-id="62b9e-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="62b9e-105">Вызов процедуры, для которой определено более одной версии</span><span class="sxs-lookup"><span data-stu-id="62b9e-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="62b9e-106">В вызывающем коде определите, какие данные должны быть переданы в процедуру.</span><span class="sxs-lookup"><span data-stu-id="62b9e-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="62b9e-107">Напишите вызов процедуры обычным способом, предоставляя данные в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="62b9e-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="62b9e-108">Убедитесь, что аргументы соответствуют списку параметров в одной из версий, определенных для процедуры.</span><span class="sxs-lookup"><span data-stu-id="62b9e-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="62b9e-109">Не нужно определять, какую версию процедуры нужно вызвать.</span><span class="sxs-lookup"><span data-stu-id="62b9e-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="62b9e-110">Visual Basic передает управление версии, соответствующей списку аргументов.</span><span class="sxs-lookup"><span data-stu-id="62b9e-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="62b9e-111">В следующем примере вызывается `post` процедура, объявленная в разделе [как определить несколько версий процедуры](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="62b9e-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="62b9e-112">Он получает идентификатор клиента, определяет, является ли он `String` или `Integer` , а затем в любом случае вызывает одну и ту же процедуру.</span><span class="sxs-lookup"><span data-stu-id="62b9e-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="62b9e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="62b9e-113">See also</span></span>

- [<span data-ttu-id="62b9e-114">Процедуры</span><span class="sxs-lookup"><span data-stu-id="62b9e-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="62b9e-115">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="62b9e-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="62b9e-116">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="62b9e-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="62b9e-117">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="62b9e-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="62b9e-118">Практическое руководство. Определение различных версий процедуры</span><span class="sxs-lookup"><span data-stu-id="62b9e-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="62b9e-119">Практическое руководство. Перегрузка процедуры, которая принимает необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="62b9e-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="62b9e-120">Практическое руководство. Перегрузка процедуры, принимающей неопределенное число параметров</span><span class="sxs-lookup"><span data-stu-id="62b9e-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="62b9e-121">Вопросы, связанные с перегрузкой процедур</span><span class="sxs-lookup"><span data-stu-id="62b9e-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="62b9e-122">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="62b9e-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="62b9e-123">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="62b9e-123">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
