---
title: Практическое руководство. Перебор элементов перечисления в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 63597145e96b04affc5f0e80e05a56b3fdf27278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907040"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="22047-102">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22047-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="22047-103">Перечисления — это удобный способ работать с наборами связанных констант и связывать постоянные значения с именами.</span><span class="sxs-lookup"><span data-stu-id="22047-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="22047-104">Для перебора элементов перечисления, его можно переместить в массив с помощью <xref:System.Enum.GetValues%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="22047-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="22047-105">Также можно последовательно пройти по перечисления с помощью `For...Each` инструкции, с помощью <xref:System.Enum.GetNames%2A> или <xref:System.Enum.GetValues%2A> метод, чтобы извлечь строковое или числовое значение.</span><span class="sxs-lookup"><span data-stu-id="22047-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="22047-106">Для выполнения итерации по перечисления</span><span class="sxs-lookup"><span data-stu-id="22047-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="22047-107">Чтобы объявить массив и преобразуйте перечисление к нему с помощью <xref:System.Enum.GetValues%2A> метод перед передачей массива, как вы бы любая другая переменная.</span><span class="sxs-lookup"><span data-stu-id="22047-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="22047-108">В следующем примере отображается каждый член перечисления <xref:Microsoft.VisualBasic.FirstDayOfWeek> мере перечисления.</span><span class="sxs-lookup"><span data-stu-id="22047-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="22047-109">См. также</span><span class="sxs-lookup"><span data-stu-id="22047-109">See also</span></span>

- [<span data-ttu-id="22047-110">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="22047-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="22047-111">Практическое руководство. Объявления перечисления</span><span class="sxs-lookup"><span data-stu-id="22047-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="22047-112">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="22047-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="22047-113">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="22047-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="22047-114">Практическое руководство. Ссылка на член перечисления</span><span class="sxs-lookup"><span data-stu-id="22047-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="22047-115">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="22047-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="22047-116">Массивы</span><span class="sxs-lookup"><span data-stu-id="22047-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
