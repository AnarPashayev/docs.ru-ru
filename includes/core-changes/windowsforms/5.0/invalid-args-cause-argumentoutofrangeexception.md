---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702454"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="a0bda-101">Теперь свойства WinForms вызывают исключение ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="a0bda-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="a0bda-102">Некоторые свойства Windows Forms теперь вызывают <xref:System.ArgumentOutOfRangeException> для недопустимых аргументов в ситуациях, где ранее не делали этого.</span><span class="sxs-lookup"><span data-stu-id="a0bda-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a0bda-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="a0bda-103">Change description</span></span>

<span data-ttu-id="a0bda-104">Ранее эти свойства вызывали различные исключения, такие как <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException> или <xref:System.ArgumentException> при передаче аргументов вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="a0bda-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="a0bda-105">Начиная с .NET 5.0, эти свойства вызывают <xref:System.ArgumentOutOfRangeException> при передаче аргументов, которые выходят за пределы диапазона.</span><span class="sxs-lookup"><span data-stu-id="a0bda-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="a0bda-106">Вызов <xref:System.ArgumentOutOfRangeException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="a0bda-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="a0bda-107">Это также улучшает процесс отладки, четко указывая, какой аргумент недопустим.</span><span class="sxs-lookup"><span data-stu-id="a0bda-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a0bda-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a0bda-108">Version introduced</span></span>

<span data-ttu-id="a0bda-109">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a0bda-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a0bda-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a0bda-110">Recommended action</span></span>

- <span data-ttu-id="a0bda-111">Измените код, чтобы предотвратить передачу недопустимых аргументов.</span><span class="sxs-lookup"><span data-stu-id="a0bda-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="a0bda-112">При необходимости обработайте <xref:System.ArgumentOutOfRangeException> при указании свойства.</span><span class="sxs-lookup"><span data-stu-id="a0bda-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="a0bda-113">Категория</span><span class="sxs-lookup"><span data-stu-id="a0bda-113">Category</span></span>

<span data-ttu-id="a0bda-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0bda-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0bda-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a0bda-115">Affected APIs</span></span>

<span data-ttu-id="a0bda-116">В следующей таблице перечислены затронутые свойства и параметры.</span><span class="sxs-lookup"><span data-stu-id="a0bda-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="a0bda-117">Свойство.</span><span class="sxs-lookup"><span data-stu-id="a0bda-117">Property</span></span> | <span data-ttu-id="a0bda-118">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="a0bda-118">Parameter name</span></span> | <span data-ttu-id="a0bda-119">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="a0bda-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="a0bda-120">5.0, предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="a0bda-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="a0bda-121">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="a0bda-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="a0bda-122">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="a0bda-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
