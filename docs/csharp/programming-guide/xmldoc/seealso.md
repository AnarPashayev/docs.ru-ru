---
title: <seealso> — Руководство по программированию на C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587660"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="c6dee-102">\<seealso> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="c6dee-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c6dee-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6dee-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6dee-104">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6dee-104">Parameters</span></span>  
 <span data-ttu-id="c6dee-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="c6dee-105">cref = " `member`"</span></span>  
 <span data-ttu-id="c6dee-106">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="c6dee-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c6dee-107">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных. `member`</span><span class="sxs-lookup"><span data-stu-id="c6dee-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="c6dee-108">необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="c6dee-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="c6dee-109">Дополнительные сведения о создании ссылки cref на универсальный тип см. в разделе [\<see>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="c6dee-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6dee-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="c6dee-110">Remarks</span></span>  
 <span data-ttu-id="c6dee-111">Кроме того, с помощью тега \<seealso> можно указать текст, который должен отображаться в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="c6dee-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="c6dee-112">Тег [\<see>](./see.md) позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="c6dee-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="c6dee-113">Чтобы обработать и сохранить комментарии документации в файл, при компиляции необходимо использовать параметр [/doc](../../language-reference/compiler-options/doc-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c6dee-113">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6dee-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c6dee-114">Example</span></span>  
 <span data-ttu-id="c6dee-115">В разделе [\<summary>](./summary.md) можно найти пример использования тега \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="c6dee-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dee-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c6dee-116">See also</span></span>

- [<span data-ttu-id="c6dee-117">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="c6dee-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c6dee-118">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="c6dee-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
