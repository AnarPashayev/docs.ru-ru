---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802439"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="f4cc9-101">Обновления стека печати WPF</span><span class="sxs-lookup"><span data-stu-id="f4cc9-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f4cc9-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="f4cc9-102">Details</span></span>|<span data-ttu-id="f4cc9-103">API-интерфейсы WPF для печати, использующие <xref:System.Printing.PrintQueue?displayProperty=name>, теперь вызывают API пакета печати документа Windows вместо устаревшего API печати XPS.</span><span class="sxs-lookup"><span data-stu-id="f4cc9-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="f4cc9-104">Это изменение внесено в целях повышения удобства обслуживания. Ни пользователи, ни разработчики не должны заметить какие-либо изменения в поведении или использовании API.</span><span class="sxs-lookup"><span data-stu-id="f4cc9-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="f4cc9-105">Новый стек печати по умолчанию активируется при работе с обновлением Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="f4cc9-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="f4cc9-106">Старый стек печати по-прежнему будет работать в предыдущих версиях Windows, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="f4cc9-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="f4cc9-107">Предложение</span><span class="sxs-lookup"><span data-stu-id="f4cc9-107">Suggestion</span></span>|<span data-ttu-id="f4cc9-108">Чтобы использовать старый стек в Windows 10 Creators Update, задайте значение <code>UseXpsOMPrinting</code> REG_DWORD в разделе реестра <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> равным <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="f4cc9-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="f4cc9-109">Область</span><span class="sxs-lookup"><span data-stu-id="f4cc9-109">Scope</span></span>|<span data-ttu-id="f4cc9-110">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="f4cc9-110">Edge</span></span>|
|<span data-ttu-id="f4cc9-111">Версия</span><span class="sxs-lookup"><span data-stu-id="f4cc9-111">Version</span></span>|<span data-ttu-id="f4cc9-112">4.7</span><span class="sxs-lookup"><span data-stu-id="f4cc9-112">4.7</span></span>|
|<span data-ttu-id="f4cc9-113">Тип</span><span class="sxs-lookup"><span data-stu-id="f4cc9-113">Type</span></span>|<span data-ttu-id="f4cc9-114">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="f4cc9-114">Runtime</span></span>|

