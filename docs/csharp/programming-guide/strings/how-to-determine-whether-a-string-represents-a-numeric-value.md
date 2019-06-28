---
title: Практическое руководство. Как определить, представляет ли строка числовое значение (руководство по программированию на C#)
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: dcba1651c736b58b2c95bac21f086c46417629df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980754"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="05f70-102">Практическое руководство. Как определить, представляет ли строка числовое значение (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="05f70-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="05f70-103">Чтобы определить, является ли строка допустимым представлением указанного числового типа, воспользуйтесь статическим методом `TryParse`, реализуемым всеми простыми числовыми типами, например <xref:System.DateTime> и <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="05f70-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="05f70-104">В следующем примере показано, как определить, является ли число 108 допустимым типом [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="05f70-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="05f70-105">Если строка содержит нечисловые знаки либо числовое значение слишком велико или мало для указанного типа, `TryParse` возвращает значение "false" и задает выходному параметру значение "0".</span><span class="sxs-lookup"><span data-stu-id="05f70-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="05f70-106">В противном случае возвращается значение "true", а выходному параметру задается числовое значение строки.</span><span class="sxs-lookup"><span data-stu-id="05f70-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05f70-107">Строка может содержать только числовые знаки и оставаться недопустимой для типа, где используется метод `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="05f70-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="05f70-108">Например, "256" не является допустимым значением для `byte`, однако оно допустимо для `int`.</span><span class="sxs-lookup"><span data-stu-id="05f70-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="05f70-109">"98,6" не является допустимым значением для `int`, однако оно допустимо для `decimal`.</span><span class="sxs-lookup"><span data-stu-id="05f70-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05f70-110">Пример</span><span class="sxs-lookup"><span data-stu-id="05f70-110">Example</span></span>  
 <span data-ttu-id="05f70-111">В следующем примере показано использование `TryParse` со строковыми представлениями значений `long`, `byte` и `decimal`.</span><span class="sxs-lookup"><span data-stu-id="05f70-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="05f70-112">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="05f70-112">Robust Programming</span></span>  
 <span data-ttu-id="05f70-113">Простые числовые типы также реализуют статический метод `Parse`, который вызывает исключение, если строка не является допустимым числом.</span><span class="sxs-lookup"><span data-stu-id="05f70-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="05f70-114">В целом оператор `TryParse` более эффективен, поскольку если число не является допустимым, он просто возвращает значение "false".</span><span class="sxs-lookup"><span data-stu-id="05f70-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="05f70-115">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05f70-115">.NET Framework Security</span></span>  
 <span data-ttu-id="05f70-116">Для проверки данных, введенных пользователем в такие элементы управления, как текстовые поля и поля со списком, всегда следует использовать метод `TryParse` или `Parse`.</span><span class="sxs-lookup"><span data-stu-id="05f70-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f70-117">См. также</span><span class="sxs-lookup"><span data-stu-id="05f70-117">See also</span></span>

- [<span data-ttu-id="05f70-118">Практическое руководство. Преобразование массива байтов в значение типа int</span><span class="sxs-lookup"><span data-stu-id="05f70-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="05f70-119">Практическое руководство. Преобразование строки в число</span><span class="sxs-lookup"><span data-stu-id="05f70-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="05f70-120">Практическое руководство. Преобразование из шестнадцатеричных строк в числовые типы</span><span class="sxs-lookup"><span data-stu-id="05f70-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="05f70-121">Анализ числовых строк</span><span class="sxs-lookup"><span data-stu-id="05f70-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="05f70-122">Типы форматирования</span><span class="sxs-lookup"><span data-stu-id="05f70-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
