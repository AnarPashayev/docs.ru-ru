---
title: Руководство по программированию на C#. <c>
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287471"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="f89ef-102">\<c> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="f89ef-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f89ef-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f89ef-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="f89ef-104">Параметры</span><span class="sxs-lookup"><span data-stu-id="f89ef-104">Parameters</span></span>

- `text`

  <span data-ttu-id="f89ef-105">Текст, который нужно указать в качестве кода.</span><span class="sxs-lookup"><span data-stu-id="f89ef-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f89ef-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="f89ef-106">Remarks</span></span>

<span data-ttu-id="f89ef-107">С помощью тега `<c>` можно указать, что текст в описании необходимо пометить как код.</span><span class="sxs-lookup"><span data-stu-id="f89ef-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="f89ef-108">Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](./code.md).</span><span class="sxs-lookup"><span data-stu-id="f89ef-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="f89ef-109">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../language-reference/compiler-options/doc-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f89ef-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f89ef-110">Пример</span><span class="sxs-lookup"><span data-stu-id="f89ef-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="f89ef-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f89ef-111">See also</span></span>

- [<span data-ttu-id="f89ef-112">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="f89ef-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f89ef-113">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="f89ef-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
