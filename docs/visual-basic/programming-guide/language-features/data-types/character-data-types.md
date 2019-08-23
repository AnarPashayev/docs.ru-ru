---
title: Символьные типы данных (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965679"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="394b0-102">Символьные типы данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="394b0-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="394b0-103">Visual Basic предоставляет *символьные типы данных* для работы с печатными и отображаемыми символами.</span><span class="sxs-lookup"><span data-stu-id="394b0-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="394b0-104">Несмотря на то, что они работают с `Char` символами Юникода, содержит один `String` символ, тогда как содержит неопределенное число символов.</span><span class="sxs-lookup"><span data-stu-id="394b0-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="394b0-105">Для таблицы, отображающей параллельное сравнение типов данных Visual Basic, см. в разделе [типы данных](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="394b0-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="394b0-106">Тип char</span><span class="sxs-lookup"><span data-stu-id="394b0-106">Char Type</span></span>  
 <span data-ttu-id="394b0-107">Тип `Char` данных — это один двухбайтовый (16-разрядный) символ Юникода.</span><span class="sxs-lookup"><span data-stu-id="394b0-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="394b0-108">Если переменная всегда хранит ровно один символ, объявите ее как `Char`.</span><span class="sxs-lookup"><span data-stu-id="394b0-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="394b0-109">Например:</span><span class="sxs-lookup"><span data-stu-id="394b0-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="394b0-110">Каждое возможное значение в `Char` переменной или `String` является кодовой *точкой*или кодом символа в кодировке Юникода.</span><span class="sxs-lookup"><span data-stu-id="394b0-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="394b0-111">Символы Юникода включают в себя основную кодировку ASCII, различные буквы, цифры, символы валют, дроби, диакритические знаки, математические и технические символы.</span><span class="sxs-lookup"><span data-stu-id="394b0-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="394b0-112">Набор символов Юникода резервирует кодовые точки D800 до DFFF (от 55296 до 55551 десятичного) для *пар символов*-заместителей, для которых требуются 2 16-разрядные значения для представления одной кодовой точки.</span><span class="sxs-lookup"><span data-stu-id="394b0-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="394b0-113">Переменная не может содержать суррогатную пару, `String` а для хранения такой пары используется две позиции. `Char`</span><span class="sxs-lookup"><span data-stu-id="394b0-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="394b0-114">Дополнительные сведения см. в разделе [тип данных char](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="394b0-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="394b0-115">Тип строки</span><span class="sxs-lookup"><span data-stu-id="394b0-115">String Type</span></span>  
 <span data-ttu-id="394b0-116">Тип `String` данных — это последовательность из нуля или более двухбайтовых (16-разрядных) символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="394b0-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="394b0-117">Если переменная может содержать неопределенное число символов, объявите ее как `String`.</span><span class="sxs-lookup"><span data-stu-id="394b0-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="394b0-118">Например:</span><span class="sxs-lookup"><span data-stu-id="394b0-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="394b0-119">Дополнительные сведения см. в разделе [тип данных String](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="394b0-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394b0-120">См. также</span><span class="sxs-lookup"><span data-stu-id="394b0-120">See also</span></span>

- [<span data-ttu-id="394b0-121">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="394b0-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="394b0-122">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="394b0-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="394b0-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="394b0-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="394b0-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="394b0-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="394b0-125">Преобразования типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="394b0-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="394b0-126">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="394b0-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="394b0-127">Знаки типов</span><span class="sxs-lookup"><span data-stu-id="394b0-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
