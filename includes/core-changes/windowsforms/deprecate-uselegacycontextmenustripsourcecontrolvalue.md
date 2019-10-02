---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181781"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="69eab-101">Параметр совместимости Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue не поддерживается</span><span class="sxs-lookup"><span data-stu-id="69eab-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="69eab-102">Параметр совместимости `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, появившийся в .NET Framework 4.7.2, не поддерживается в Windows Forms в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="69eab-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="69eab-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="69eab-103">Change description</span></span>

<span data-ttu-id="69eab-104">Начиная с версии .NET Framework 4.7.2, параметр совместимости `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` позволяет разработчикам отказаться от нового поведения свойства <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, которое теперь возвращает ссылку на систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="69eab-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="69eab-105">Ранее это свойство возвращало `null`.</span><span class="sxs-lookup"><span data-stu-id="69eab-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="69eab-106">Дополнительные сведения см. в статье [Элемент \<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="69eab-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="69eab-107">В .NET Core параметр `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="69eab-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="69eab-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="69eab-108">Version introduced</span></span>

<span data-ttu-id="69eab-109">3.0, предварительная версия 9</span><span class="sxs-lookup"><span data-stu-id="69eab-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69eab-110">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="69eab-110">Recommended action</span></span>

<span data-ttu-id="69eab-111">Удалите параметр.</span><span class="sxs-lookup"><span data-stu-id="69eab-111">Remove the switch.</span></span> <span data-ttu-id="69eab-112">Он не поддерживается, и альтернативного варианта нет.</span><span class="sxs-lookup"><span data-stu-id="69eab-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="69eab-113">Категория</span><span class="sxs-lookup"><span data-stu-id="69eab-113">Category</span></span>

<span data-ttu-id="69eab-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69eab-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69eab-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="69eab-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
