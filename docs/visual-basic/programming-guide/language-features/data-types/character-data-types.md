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
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840982"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="ffb25-102">Символьные типы данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffb25-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="ffb25-103">Visual Basic предоставляет *символьные типы данных* для работы с символами печати и отображения.</span><span class="sxs-lookup"><span data-stu-id="ffb25-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="ffb25-104">Оба они работают с символами Юникода, `Char` содержит один символ, тогда как `String` содержит неопределенное число символов.</span><span class="sxs-lookup"><span data-stu-id="ffb25-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="ffb25-105">Таблицу, отображающую side-by-side сравнение типов данных Visual Basic, см. в разделе [типы данных](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="ffb25-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="ffb25-106">Тип char</span><span class="sxs-lookup"><span data-stu-id="ffb25-106">Char Type</span></span>  
 <span data-ttu-id="ffb25-107">`Char` Тип данных — это символ Юникода (16-разрядная версия) размером 2 байта.</span><span class="sxs-lookup"><span data-stu-id="ffb25-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="ffb25-108">Если переменная всегда хранит ровно один символ, он объявляется как `Char`.</span><span class="sxs-lookup"><span data-stu-id="ffb25-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="ffb25-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="ffb25-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="ffb25-110">Каждое возможное значение в `Char` или `String` переменная является *кодовую точку*, или код знака в кодировке Юникод.</span><span class="sxs-lookup"><span data-stu-id="ffb25-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="ffb25-111">Символы Юникода включают базовый набор символов ASCII, различные другие буквы алфавита, диакритические знаки, символы валют, дроби, диакритические знаки и математические и технические символы.</span><span class="sxs-lookup"><span data-stu-id="ffb25-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffb25-112">Набор символов Юникода кодовые точки от D800 до DFFF (55296 до 55551) для Резервы *суррогатные пары*, который требует два 16-разрядных значений для представления одну кодовую точку.</span><span class="sxs-lookup"><span data-stu-id="ffb25-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="ffb25-113">Объект `Char` переменной не может удерживать суррогатную пару и `String` использует две позиции для хранения таких пар.</span><span class="sxs-lookup"><span data-stu-id="ffb25-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="ffb25-114">Дополнительные сведения см. в разделе [тип данных Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ffb25-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="ffb25-115">Тип строки</span><span class="sxs-lookup"><span data-stu-id="ffb25-115">String Type</span></span>  
 <span data-ttu-id="ffb25-116">`String` Тип данных представляет собой последовательность из нуля или более символов Юникода (16-разрядная версия) размером 2 байта.</span><span class="sxs-lookup"><span data-stu-id="ffb25-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="ffb25-117">Если переменная может содержать неограниченное количество символов, объявите его как `String`.</span><span class="sxs-lookup"><span data-stu-id="ffb25-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="ffb25-118">Пример:</span><span class="sxs-lookup"><span data-stu-id="ffb25-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="ffb25-119">Дополнительные сведения см. в разделе [строковый тип данных](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ffb25-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb25-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ffb25-120">See also</span></span>

- [<span data-ttu-id="ffb25-121">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="ffb25-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="ffb25-122">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="ffb25-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="ffb25-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ffb25-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ffb25-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="ffb25-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="ffb25-125">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ffb25-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="ffb25-126">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="ffb25-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="ffb25-127">Знаки типов</span><span class="sxs-lookup"><span data-stu-id="ffb25-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
