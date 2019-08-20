---
title: Руководство по программированию на C#. Комментарии XML-документации
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: 46dd947ac6ff5a45c7d952acaa55e25c3a46969c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588056"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="a5104-102">Комментарии XML-документации (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="a5104-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="a5104-103">В Visual C# можно создавать документацию для кода путем включения XML-элементов в специальные поля комментариев (начинающиеся с трех символов косой черты) в исходном коде непосредственно перед блоком кода, к которому относятся комментарии. Например:</span><span class="sxs-lookup"><span data-stu-id="a5104-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="a5104-104">При выполнении компиляции с параметром [/doc](../../language-reference/compiler-options/doc-compiler-option.md) компилятор осуществляет поиск всех тегов XML в исходном коде и создает XML-файл документации.</span><span class="sxs-lookup"><span data-stu-id="a5104-104">When you compile with the [/doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="a5104-105">Для создания окончательной документации на основе сгенерированного компилятором файла можно создать пользовательское средство или применить такие средства, как [DocFX](https://dotnet.github.io/docfx/) или [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="a5104-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="a5104-106">Для ссылки на XML-элементы (например, если функция обрабатывает определенные XML-элементы, которые требуется включить в комментарии XML-документации) можно использовать стандартный механизм заключения в скобки (`<` и `>`).</span><span class="sxs-lookup"><span data-stu-id="a5104-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="a5104-107">Для ссылки на универсальные идентификаторы в элементах ссылок кода (`cref`) можно использовать escape-символы (например, `cref="List&lt;T&gt;"`) или фигурные скобки (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="a5104-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="a5104-108">В особом случае компилятор анализирует фигурные скобки, как угловые, чтобы при ссылке на универсальные идентификаторы сделать комментарий документации менее громоздким.</span><span class="sxs-lookup"><span data-stu-id="a5104-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5104-109">Комментарии XML-документации не являются метаданными. Они не включаются в скомпилированную сборку, и поэтому не доступны посредством отражения.</span><span class="sxs-lookup"><span data-stu-id="a5104-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5104-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a5104-110">In This Section</span></span>  
  
- [<span data-ttu-id="a5104-111">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="a5104-111">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)  
  
- [<span data-ttu-id="a5104-112">Обработка XML-файла</span><span class="sxs-lookup"><span data-stu-id="a5104-112">Processing the XML File</span></span>](./processing-the-xml-file.md)  
  
- [<span data-ttu-id="a5104-113">Разделители для тегов документации</span><span class="sxs-lookup"><span data-stu-id="a5104-113">Delimiters for Documentation Tags</span></span>](./delimiters-for-documentation-tags.md)  
  
- [<span data-ttu-id="a5104-114">Практическое руководство. Использование XML-документации</span><span class="sxs-lookup"><span data-stu-id="a5104-114">How to: Use the XML Documentation Features</span></span>](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="a5104-115">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="a5104-115">Related Sections</span></span>  
 <span data-ttu-id="a5104-116">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="a5104-116">For more information, see:</span></span>  
  
- [<span data-ttu-id="a5104-117">/doc (обработка комментариев документации)</span><span class="sxs-lookup"><span data-stu-id="a5104-117">/doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a5104-118">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="a5104-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a5104-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a5104-119">See also</span></span>

- [<span data-ttu-id="a5104-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="a5104-120">C# Programming Guide</span></span>](../index.md)
