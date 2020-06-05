---
title: Возвращаемые значения функции CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406392"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="c64ad-102">Возвращаемые значения функции CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c64ad-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="c64ad-103">В следующей таблице описаны возвращаемые значения для `CStr` для различных типов данных `expression` .</span><span class="sxs-lookup"><span data-stu-id="c64ad-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="c64ad-104">Если `expression` тип —</span><span class="sxs-lookup"><span data-stu-id="c64ad-104">If `expression` type is</span></span>|<span data-ttu-id="c64ad-105">Возвращаемые значения `CStr`</span><span class="sxs-lookup"><span data-stu-id="c64ad-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="c64ad-106">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="c64ad-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="c64ad-107">Строка, содержащая "true" или "false".</span><span class="sxs-lookup"><span data-stu-id="c64ad-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="c64ad-108">Тип данных Date</span><span class="sxs-lookup"><span data-stu-id="c64ad-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="c64ad-109">Строка, содержащая `Date` значение (Дата и время) в кратком формате даты системы.</span><span class="sxs-lookup"><span data-stu-id="c64ad-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="c64ad-110">Числовые типы данных</span><span class="sxs-lookup"><span data-stu-id="c64ad-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="c64ad-111">Строка, представляющая число.</span><span class="sxs-lookup"><span data-stu-id="c64ad-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="c64ad-112">Функция CStr и Дата</span><span class="sxs-lookup"><span data-stu-id="c64ad-112">CStr and Date</span></span>  
 <span data-ttu-id="c64ad-113">`Date`Тип всегда содержит сведения о дате и времени.</span><span class="sxs-lookup"><span data-stu-id="c64ad-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="c64ad-114">В целях преобразования типов Visual Basic учитывает 1/1/0001 (1 января 1 года) как *нейтральное значение* для даты, а 00:00:00 (полночь) — как нейтральное значение времени.</span><span class="sxs-lookup"><span data-stu-id="c64ad-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="c64ad-115">`CStr`не включает нейтральные значения в результирующую строку.</span><span class="sxs-lookup"><span data-stu-id="c64ad-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="c64ad-116">Например, если преобразовать `#January 1, 0001 9:30:00#` в строку, то результатом будет "9:30:00 AM"; сведения о дате подавляются.</span><span class="sxs-lookup"><span data-stu-id="c64ad-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="c64ad-117">Однако сведения о дате по-прежнему содержатся в исходном `Date` значении и могут быть восстановлены с помощью таких функций, как <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="c64ad-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c64ad-118">`CStr`Функция выполняет преобразование на основе текущих настроек языка и региональных параметров для приложения.</span><span class="sxs-lookup"><span data-stu-id="c64ad-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="c64ad-119">Чтобы получить строковое представление числа в определенном языке и региональных параметрах, используйте `ToString(IFormatProvider)` метод числа.</span><span class="sxs-lookup"><span data-stu-id="c64ad-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="c64ad-120">Например, используйте <xref:System.Double.ToString%2A?displayProperty=nameWithType> при преобразовании значения типа `Double` в `String` .</span><span class="sxs-lookup"><span data-stu-id="c64ad-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c64ad-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c64ad-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="c64ad-122">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="c64ad-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="c64ad-123">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="c64ad-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="c64ad-124">Тип данных Date</span><span class="sxs-lookup"><span data-stu-id="c64ad-124">Date Data Type</span></span>](../data-types/date-data-type.md)
