---
title: Соглашения о написании прописными буквами
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: KrzysztofCwalina
ms.openlocfilehash: e0da4cd747846921d170d9c07d6f1fb91dbd4ed7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615257"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="2ac3a-102">Соглашения о написании прописными буквами</span><span class="sxs-lookup"><span data-stu-id="2ac3a-102">Capitalization Conventions</span></span>
<span data-ttu-id="2ac3a-103">Рекомендации в этой главе размещать простой метод с помощью варианта, когда применяется последовательно, делать идентификаторы для типов, членов и параметров, удобном для чтения.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="2ac3a-104">Регистр букв правилам для идентификаторов</span><span class="sxs-lookup"><span data-stu-id="2ac3a-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="2ac3a-105">Для разделения слов в идентификаторе, преобразование первой буквы каждого слова в идентификаторе.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="2ac3a-106">Не используйте символы подчеркивания для разделения слов, или для того, где угодно в идентификаторах.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="2ac3a-107">Существует два способа соответствующие прописной идентификаторов, в зависимости от использования идентификатора:</span><span class="sxs-lookup"><span data-stu-id="2ac3a-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
- <span data-ttu-id="2ac3a-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="2ac3a-108">PascalCasing</span></span>  
  
- <span data-ttu-id="2ac3a-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="2ac3a-109">camelCasing</span></span>  
  
 <span data-ttu-id="2ac3a-110">Соглашение PascalCasing, применяется для всех идентификаторов, за исключением имен параметров, первая буква каждого слова (включая акронимов через двух букв), как показано в следующих примерах:</span><span class="sxs-lookup"><span data-stu-id="2ac3a-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="2ac3a-111">Особый случай выполняется для двухбуквенный акронимов, в которых заданы оба буквы, как показано в следующий идентификатор:</span><span class="sxs-lookup"><span data-stu-id="2ac3a-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="2ac3a-112">Соглашение camelCasing, применяется только для имен параметров, первая буква каждого слова, кроме первого, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="2ac3a-113">В примере также показано, как строчные, двухбуквенный сокращений, которые начинаются с идентификатора Camel.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="2ac3a-114">**✓ DO** использовать PascalCasing для всех открытых элемента, типа и пространство имен имен, состоящих из нескольких слов.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="2ac3a-115">**✓ DO** использовать camelCasing для имен параметров.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="2ac3a-116">Следующая таблица описывает правила использования прописных букв для различных типов идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="2ac3a-117">Идентификатор</span><span class="sxs-lookup"><span data-stu-id="2ac3a-117">Identifier</span></span>|<span data-ttu-id="2ac3a-118">Регистр</span><span class="sxs-lookup"><span data-stu-id="2ac3a-118">Casing</span></span>|<span data-ttu-id="2ac3a-119">Пример</span><span class="sxs-lookup"><span data-stu-id="2ac3a-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="2ac3a-120">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="2ac3a-120">Namespace</span></span>|<span data-ttu-id="2ac3a-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="2ac3a-122">Тип</span><span class="sxs-lookup"><span data-stu-id="2ac3a-122">Type</span></span>|<span data-ttu-id="2ac3a-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="2ac3a-124">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="2ac3a-124">Interface</span></span>|<span data-ttu-id="2ac3a-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="2ac3a-126">Метод</span><span class="sxs-lookup"><span data-stu-id="2ac3a-126">Method</span></span>|<span data-ttu-id="2ac3a-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="2ac3a-128">Свойство</span><span class="sxs-lookup"><span data-stu-id="2ac3a-128">Property</span></span>|<span data-ttu-id="2ac3a-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="2ac3a-130">событие</span><span class="sxs-lookup"><span data-stu-id="2ac3a-130">Event</span></span>|<span data-ttu-id="2ac3a-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="2ac3a-132">Поле</span><span class="sxs-lookup"><span data-stu-id="2ac3a-132">Field</span></span>|<span data-ttu-id="2ac3a-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="2ac3a-134">Значение перечисления</span><span class="sxs-lookup"><span data-stu-id="2ac3a-134">Enum value</span></span>|<span data-ttu-id="2ac3a-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="2ac3a-136">Параметр</span><span class="sxs-lookup"><span data-stu-id="2ac3a-136">Parameter</span></span>|<span data-ttu-id="2ac3a-137">Camel</span><span class="sxs-lookup"><span data-stu-id="2ac3a-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="2ac3a-138">Составные слова в прописную букву и распространенные термины</span><span class="sxs-lookup"><span data-stu-id="2ac3a-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="2ac3a-139">Большинство составные термины рассматриваются как отдельные слова в рамках регистр букв.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="2ac3a-140">**X DO NOT** прописных так называемые единым составные слова.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="2ac3a-141">Это сложные слова, записываются в одно слово, например конечной точки.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="2ac3a-142">Целью правила учета регистра обрабатывать составное слово единым как одно слово.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="2ac3a-143">Используйте текущий словарь для определения того, если составное слово записывается в закрытой формой.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="2ac3a-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="2ac3a-144">Pascal</span></span>|<span data-ttu-id="2ac3a-145">Camel</span><span class="sxs-lookup"><span data-stu-id="2ac3a-145">Camel</span></span>|<span data-ttu-id="2ac3a-146">not</span><span class="sxs-lookup"><span data-stu-id="2ac3a-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="2ac3a-147">Учет регистра</span><span class="sxs-lookup"><span data-stu-id="2ac3a-147">Case Sensitivity</span></span>  
 <span data-ttu-id="2ac3a-148">Языки, которые могут выполняться в среде CLR не требуются для поддержки учета регистра, несмотря на то, что некоторые делают.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="2ac3a-149">Даже если ваш язык поддерживает такую возможность, другими языками, может получить доступ к вашей платформы — нет.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="2ac3a-150">Любой API, которые будут доступны извне, таким образом, нельзя полагаться на случай отдельно, чтобы различать два имени, в том же контексте.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="2ac3a-151">**X DO NOT** предполагается, что все языки программирования чувствительны к регистру.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="2ac3a-152">Это не так.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-152">They are not.</span></span> <span data-ttu-id="2ac3a-153">Имена не могут различаться только регистром.</span><span class="sxs-lookup"><span data-stu-id="2ac3a-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="2ac3a-154">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="2ac3a-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2ac3a-155">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2ac3a-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac3a-156">См. также</span><span class="sxs-lookup"><span data-stu-id="2ac3a-156">See also</span></span>

- [<span data-ttu-id="2ac3a-157">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="2ac3a-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="2ac3a-158">Правила именования</span><span class="sxs-lookup"><span data-stu-id="2ac3a-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
