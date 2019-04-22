---
title: Практическое руководство. Создание строк с помощью StringBuilder в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834196"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="89cfc-102">Практическое руководство. Создание строк с помощью StringBuilder в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89cfc-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="89cfc-103">В этом примере создается длинная строка из множества маленьких строк с помощью <xref:System.Text.StringBuilder> класса.</span><span class="sxs-lookup"><span data-stu-id="89cfc-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="89cfc-104"><xref:System.Text.StringBuilder> Класс является более эффективным, чем `&=` оператор для объединения большого количества строк.</span><span class="sxs-lookup"><span data-stu-id="89cfc-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89cfc-105">Пример</span><span class="sxs-lookup"><span data-stu-id="89cfc-105">Example</span></span>  
 <span data-ttu-id="89cfc-106">В следующем примере создается экземпляр <xref:System.Text.StringBuilder> класс, прибавляется 1 000 строк к этому экземпляру, а затем возвращает его строковое представление.</span><span class="sxs-lookup"><span data-stu-id="89cfc-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="89cfc-107">См. также</span><span class="sxs-lookup"><span data-stu-id="89cfc-107">See also</span></span>

- <span data-ttu-id="89cfc-108">[Using the StringBuilder class](../../../../standard/base-types/stringbuilder.md) (Использование класса StringBuilder)</span><span class="sxs-lookup"><span data-stu-id="89cfc-108">[Using the StringBuilder Class](../../../../standard/base-types/stringbuilder.md)</span></span>
- [<span data-ttu-id="89cfc-109">Оператор &=</span><span class="sxs-lookup"><span data-stu-id="89cfc-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="89cfc-110">Строки</span><span class="sxs-lookup"><span data-stu-id="89cfc-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="89cfc-111">Создание строк</span><span class="sxs-lookup"><span data-stu-id="89cfc-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="89cfc-112">Операции со строками</span><span class="sxs-lookup"><span data-stu-id="89cfc-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
