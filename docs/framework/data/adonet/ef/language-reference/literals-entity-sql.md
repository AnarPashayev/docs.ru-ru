---
title: Литералы (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 4402f4c6ee38432a0f606e39dd4a18639076ce04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161780"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="ac7d1-102">Литералы (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ac7d1-102">Literals (Entity SQL)</span></span>

<span data-ttu-id="ac7d1-103">В этом разделе рассматривается поддержка литералов в [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac7d1-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="ac7d1-104">NULL</span><span class="sxs-lookup"><span data-stu-id="ac7d1-104">Null</span></span>  

 <span data-ttu-id="ac7d1-105">Литерал null используется для представления значения NULL применительно к любому типу.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="ac7d1-106">Литерал null является совместимым с любым типом.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="ac7d1-107">Типизированные значения null могут быть созданы путем применения операции приведения к типу по отношению к литералу NULL.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="ac7d1-108">Дополнительные сведения см. в разделе [Cast](cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ac7d1-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ac7d1-109">Правила того, где можно использовать свободные плавающие литералы NULL, см. в разделе [литералы NULL и определение типа](null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ac7d1-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="ac7d1-110">Логическое</span><span class="sxs-lookup"><span data-stu-id="ac7d1-110">Boolean</span></span>  

 <span data-ttu-id="ac7d1-111">Логические литералы могут быть представлены с помощью ключевых слов `true` и `false`.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="ac7d1-112">Целое число</span><span class="sxs-lookup"><span data-stu-id="ac7d1-112">Integer</span></span>  

 <span data-ttu-id="ac7d1-113">Целочисленные литералы могут иметь тип <xref:System.Int32> или <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="ac7d1-114">Литерал <xref:System.Int32> представляет собой ряд цифр.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="ac7d1-115">Литерал <xref:System.Int64> представляет собой ряд цифр, за которыми следует прописная буква L.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="ac7d1-116">Decimal</span><span class="sxs-lookup"><span data-stu-id="ac7d1-116">Decimal</span></span>  

 <span data-ttu-id="ac7d1-117">Число с фиксированной запятой (десятичное) представляет собой последовательность цифр, запятую (,) и еще одну последовательность цифр, за которой следует прописная буква «М».</span><span class="sxs-lookup"><span data-stu-id="ac7d1-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="ac7d1-118">С плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="ac7d1-118">Float, Double</span></span>  

 <span data-ttu-id="ac7d1-119">Число с плавающей запятой двойной точности представляет собой ряд цифр, запятую (,) и еще один ряд цифр, за которыми может следовать показатель степени.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="ac7d1-120">Число с плавающей запятой одинарной точности (или просто число с плавающей запятой) представляет собой число с синтаксисом числа с плавающей запятой двойной точности, за которым следует строчная буква f.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="ac7d1-121">Строка</span><span class="sxs-lookup"><span data-stu-id="ac7d1-121">String</span></span>  

 <span data-ttu-id="ac7d1-122">Строка - это ряд символов, заключенных в кавычки.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="ac7d1-123">Кавычки могут быть либо одинарными (`'`), либо двойными (").</span><span class="sxs-lookup"><span data-stu-id="ac7d1-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="ac7d1-124">Символьные строковые литералы могут быть представлены либо в Юникоде, либо в кодировке, отличной от Юникода.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="ac7d1-125">Чтобы объявить символьный строковый литерал как представленный в Юникоде, необходимо обозначить литерал префиксом в виде прописной буквы «N».</span><span class="sxs-lookup"><span data-stu-id="ac7d1-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="ac7d1-126">По умолчанию символьные строковые литералы рассматриваются как имеющие кодировку, отличную от Юникода.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="ac7d1-127">Не должно быть пробелов между буквой N и полезными данными строкового литерала, а буква N должна быть прописной.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="ac7d1-128">Дата и время</span><span class="sxs-lookup"><span data-stu-id="ac7d1-128">DateTime</span></span>  

 <span data-ttu-id="ac7d1-129">Литерал даты-времени является не зависимым от языкового стандарта и состоит из части даты и части времени.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="ac7d1-130">Обе части - и даты, и времени - являются обязательными, и какие-либо значения по умолчанию не предусмотрены.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="ac7d1-131">Часть даты должна иметь следующий формат: `YYYY` - `MM` - `DD` , где `YYYY` — это четырехзначное значение года в диапазоне от 0001 до 9999, `MM` равно месяцу от 1 до 12 и `DD` является значением дня, допустимым для данного месяца `MM` .</span><span class="sxs-lookup"><span data-stu-id="ac7d1-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="ac7d1-132">Часть времени должна иметь формат: `HH`:`MM`[:`SS`, где `HH` представляет собой значение часа от 0 до 23 включительно, `MM` - значение минут от 0 до 59 включительно, `SS` - значение секунд от 0 до 59 включительно, а fffffff - значение долей секунд от 0 до 9999999 включительно.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="ac7d1-133">Все диапазоны значений являются включительными.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-133">All value ranges are inclusive.</span></span> <span data-ttu-id="ac7d1-134">Часть, содержащая доли секунды, является необязательной.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-134">Fractional seconds are optional.</span></span> <span data-ttu-id="ac7d1-135">Часть, содержащая секунды, является необязательной, если не была задана часть с долями секунды. В последнем случае часть с секундами обязательна.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="ac7d1-136">Если секунды или доли секунд не заданы, то по умолчанию используется значение ноль.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="ac7d1-137">Между символом DATETIME и полезными данными литерала может быть любое количество пробелов, но не должно быть новых строк.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="ac7d1-138">Time</span><span class="sxs-lookup"><span data-stu-id="ac7d1-138">Time</span></span>  

 <span data-ttu-id="ac7d1-139">Литерал time является независимым от языкового стандарта и состоит только из части времени.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="ac7d1-140">Часть времени является обязательной, и для нее не существует значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="ac7d1-141">Она должна иметь формат HH:MM[:SS[.fffffff]], где HH представляет собой значение часа от 0 до 23 включительно, MM - значение минут от 0 до 59 включительно, SS - значение секунд от 0 до 59 включительно, а fffffff - значение долей секунд от 0 до 9999999 включительно.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="ac7d1-142">Все диапазоны значений являются включительными.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-142">All value ranges are inclusive.</span></span> <span data-ttu-id="ac7d1-143">Часть, содержащая доли секунды, является необязательной.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-143">Fractional seconds are optional.</span></span> <span data-ttu-id="ac7d1-144">Часть, содержащая секунды, является необязательной, если не была задана часть с долями секунды. В последнем случае часть с секундами обязательна.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="ac7d1-145">Если секунды или доли секунды не заданы, то по умолчанию используется значение ноль.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="ac7d1-146">Между символом TIME и полезными данными литерала может быть любое количество пробелов, но не должно быть новых строк.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="ac7d1-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac7d1-147">DateTimeOffset</span></span>  

 <span data-ttu-id="ac7d1-148">Литерал datetimeoffset является независимым от языкового стандарта и состоит из части даты и части времени.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="ac7d1-149">Части даты, времени и смещения являются обязательными, и какие-либо значения по умолчанию не предусмотрены.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="ac7d1-150">Часть даты должна иметь формат YYYY-MM-DD, где YYYY представляет собой значение года из четырех цифр между 0001 и 9999, MM - месяц со значением от 1 до 12, а DD - значение суток, допустимое для данного месяца.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="ac7d1-151">Часть времени должна иметь формат HH:MM[:SS[.fffffff]], где HH представляет собой значение часа от 0 до 23 включительно, MM - значение минут от 0 до 59 включительно, SS - значение секунд от 0 до 59 включительно, а fffffff - значение долей секунды от 0 до 9999999 включительно.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="ac7d1-152">Все диапазоны значений являются включительными.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-152">All value ranges are inclusive.</span></span> <span data-ttu-id="ac7d1-153">Часть, содержащая доли секунды, является необязательной.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-153">Fractional seconds are optional.</span></span> <span data-ttu-id="ac7d1-154">Часть, содержащая секунды, является необязательной, если не была задана часть с долями секунды. В последнем случае часть с секундами обязательна.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="ac7d1-155">Если секунды или доли секунды не заданы, то по умолчанию используется значение ноль.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="ac7d1-156">Часть смещения должна иметь формат {+&#124;-} чч: мм, где HH и MM имеют то же значение, что и в части времени.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="ac7d1-157">Значение смещения, однако, должно находиться в пределах от -14:00 до +14:00</span><span class="sxs-lookup"><span data-stu-id="ac7d1-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="ac7d1-158">Между символом DATETIMEOFFSET и полезными данными литерала может быть любое количество пробелов, но не должно быть новых строк.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="ac7d1-159">Допустимое значение литерала Entity SQL может находиться вне допустимого диапазона CLR или источника данных.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="ac7d1-160">В этом случае может возникнуть исключение.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="ac7d1-161">Двоичные данные</span><span class="sxs-lookup"><span data-stu-id="ac7d1-161">Binary</span></span>  

 <span data-ttu-id="ac7d1-162">Двоичный строковый литерал представляет собой последовательность шестнадцатеричных цифр, заключенную в одинарные кавычки, следующую за ключевым словом binary или символом сокращения `X` или `x`.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="ac7d1-163">Символ сокращения `X` без учета регистра.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="ac7d1-164">Допускается наличие нуля и более пробелов между ключевым словом `binary` и двоичным строковым значением.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="ac7d1-165">Шестнадцатеричные символы также являются нечувствительными к регистру.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="ac7d1-166">Если литерал состоит из нечетного количества шестнадцатеричных цифр, то литерал выравнивается вправо к следующей четной шестнадцатеричной цифре путем применения к нему префикса в виде шестнадцатеричной цифры ноль.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="ac7d1-167">На размер двоичной строки не распространяются какие-либо ограничения, определяемые форматом.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="ac7d1-168">Guid</span><span class="sxs-lookup"><span data-stu-id="ac7d1-168">Guid</span></span>  

 <span data-ttu-id="ac7d1-169">Литерал `GUID` представляет собой идентификатор GUID.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="ac7d1-170">Это последовательность, сформированная с помощью ключевого слова, `GUID` за которым следуют шестнадцатеричные цифры в форме, известной как формат *реестра* : 8-4-4-4-12, заключенные в одинарные кавычки.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="ac7d1-171">Шестнадцатеричные цифры являются нечувствительными к регистру.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="ac7d1-172">Между символом GUID и полезными данными литерала может быть любое количество пробелов, но не должно быть новых строк.</span><span class="sxs-lookup"><span data-stu-id="ac7d1-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac7d1-173">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ac7d1-173">See also</span></span>

- [<span data-ttu-id="ac7d1-174">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ac7d1-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
