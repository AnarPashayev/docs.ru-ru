---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522694"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="7a255-101">Microsoft.VisualBasic.Constants.vbNewLine устарела</span><span class="sxs-lookup"><span data-stu-id="7a255-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="7a255-102">Начиная с .NET Core 3.0 (предварительная версия 8), константа <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> помечена как [Obsolete](xref:System.ObsoleteAttribute).</span><span class="sxs-lookup"><span data-stu-id="7a255-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a255-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7a255-103">Version introduced</span></span>

<span data-ttu-id="7a255-104">3.0 (предварительная версия 8)</span><span class="sxs-lookup"><span data-stu-id="7a255-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="7a255-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="7a255-105">Change description</span></span>

<span data-ttu-id="7a255-106">Начиная с .NET Core 3.0 (предварительная версия 8), к константе <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> применяется атрибут [Obsolete](xref:System.ObsoleteAttribute).</span><span class="sxs-lookup"><span data-stu-id="7a255-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="7a255-107">При использовании константы выдается предупреждение компилятора.</span><span class="sxs-lookup"><span data-stu-id="7a255-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="7a255-108">В предыдущих версиях .NET Core и .NET Framework она не была помечена как нерекомендуемая.</span><span class="sxs-lookup"><span data-stu-id="7a255-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="7a255-109">Это изменение было внесено для поддержки Visual Basic в качестве языка для разработки на нескольких платформах.</span><span class="sxs-lookup"><span data-stu-id="7a255-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="7a255-110">Константа `vbNewLine` эквивалентна `\r\n`, последовательности символов новой строки в Windows.</span><span class="sxs-lookup"><span data-stu-id="7a255-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="7a255-111">В системах на основе Unix символ новой строки — `\n`.</span><span class="sxs-lookup"><span data-stu-id="7a255-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a255-112">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="7a255-112">Recommended action</span></span>

<span data-ttu-id="7a255-113">Сообщение атрибута [Obsolete](xref:System.ObsoleteAttribute) для `vbNewLine` включает следующие рекомендации:</span><span class="sxs-lookup"><span data-stu-id="7a255-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="7a255-114">Для возврата каретки и перевода строки используйте [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="7a255-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="7a255-115">Для новой строки на текущей платформе используйте <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a255-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="7a255-116">Категория</span><span class="sxs-lookup"><span data-stu-id="7a255-116">Category</span></span>

<span data-ttu-id="7a255-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a255-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a255-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7a255-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
