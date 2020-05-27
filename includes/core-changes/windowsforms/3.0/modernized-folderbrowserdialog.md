---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721170"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="0f01a-101">Модернизация FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="0f01a-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="0f01a-102">В приложениях Windows Forms для .NET Core в элемент управления <xref:System.Windows.Forms.FolderBrowserDialog> внесены изменения.</span><span class="sxs-lookup"><span data-stu-id="0f01a-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f01a-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0f01a-103">Change description</span></span>

<span data-ttu-id="0f01a-104">В Windows Forms в .NET Framework для элемента управления <xref:System.Windows.Forms.FolderBrowserDialog> используется следующее диалоговое окно:</span><span class="sxs-lookup"><span data-stu-id="0f01a-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl в .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="0f01a-106">В .NET Core 3.0 в Windows Forms используется более новый элемент управления на основе COM, появившийся в Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="0f01a-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl в .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="0f01a-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0f01a-108">Version introduced</span></span>

<span data-ttu-id="0f01a-109">3,0</span><span class="sxs-lookup"><span data-stu-id="0f01a-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f01a-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0f01a-110">Recommended action</span></span>

<span data-ttu-id="0f01a-111">Диалоговое окно будет обновлено автоматически.</span><span class="sxs-lookup"><span data-stu-id="0f01a-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="0f01a-112">Если вы хотите оставить исходное диалоговое окно, перед отображением диалогового окна задайте для свойства <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> значение `false`, как показано в следующем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="0f01a-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="0f01a-113">Категория</span><span class="sxs-lookup"><span data-stu-id="0f01a-113">Category</span></span>

<span data-ttu-id="0f01a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f01a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f01a-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0f01a-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
