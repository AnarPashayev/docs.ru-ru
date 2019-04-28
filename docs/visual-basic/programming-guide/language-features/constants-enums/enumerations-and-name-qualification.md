---
title: Перечисления и уточнение имен (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907443"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="d38c7-102">Перечисления и уточнение имен (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d38c7-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="d38c7-103">Как правило при ссылке на член перечисления, необходимо уточнить имя члена перечисления.</span><span class="sxs-lookup"><span data-stu-id="d38c7-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="d38c7-104">Например, для ссылки на `Sunday` членом вашей `Days` перечисления, используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="d38c7-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="d38c7-105">Используя оператор Imports</span><span class="sxs-lookup"><span data-stu-id="d38c7-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="d38c7-106">Можно избежать с помощью полных имен, добавив `Imports` инструкцию, чтобы раздел объявлений пространства имен кода, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d38c7-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="d38c7-107">`Imports` Инструкция импортирует имена пространств имен из указанных проектов и сборок, а также из того же проекта модуля, в котором находится данный оператор.</span><span class="sxs-lookup"><span data-stu-id="d38c7-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="d38c7-108">После добавления этой инструкции можно ссылаться к членам перечисления без квалификации, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d38c7-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="d38c7-109">Организуя наборами связанных констант в перечислениях, можно использовать то же имя константы в различных контекстах.</span><span class="sxs-lookup"><span data-stu-id="d38c7-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="d38c7-110">Например, можно использовать те же имена констант дней недели в `Days` и `WorkDays` перечисления.</span><span class="sxs-lookup"><span data-stu-id="d38c7-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="d38c7-111">Если вы используете `Imports` инструкции с перечислениями, необходимо быть осторожным, чтобы избежать неоднозначности.</span><span class="sxs-lookup"><span data-stu-id="d38c7-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="d38c7-112">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="d38c7-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="d38c7-113">Предположим, что `Monday` является одновременно членом групп `Days` перечисления и `Workdays` перечисления, этот код создает ошибку компилятора.</span><span class="sxs-lookup"><span data-stu-id="d38c7-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="d38c7-114">Чтобы избежать неоднозначности при ссылке на отдельную константу, уточните имя константы перечисления.</span><span class="sxs-lookup"><span data-stu-id="d38c7-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="d38c7-115">Приведенный ниже код относится к `Saturday` константы в `Days` и `WorkDays` перечисления.</span><span class="sxs-lookup"><span data-stu-id="d38c7-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="d38c7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d38c7-116">See also</span></span>

- [<span data-ttu-id="d38c7-117">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="d38c7-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="d38c7-118">Практическое руководство. Объявления перечисления</span><span class="sxs-lookup"><span data-stu-id="d38c7-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="d38c7-119">Практическое руководство. Ссылка на член перечисления</span><span class="sxs-lookup"><span data-stu-id="d38c7-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="d38c7-120">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d38c7-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="d38c7-121">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="d38c7-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="d38c7-122">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="d38c7-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="d38c7-123">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="d38c7-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="d38c7-124">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="d38c7-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="d38c7-125">Оператор Imports (пространство имен и тип .NET)</span><span class="sxs-lookup"><span data-stu-id="d38c7-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d38c7-126">Типы данных</span><span class="sxs-lookup"><span data-stu-id="d38c7-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
