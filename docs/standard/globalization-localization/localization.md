---
title: Локализация
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 68e877088c5c3d17b368561b563b4cb17d004e75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278029"
---
# <a name="localization"></a><span data-ttu-id="f22d1-102">Локализация</span><span class="sxs-lookup"><span data-stu-id="f22d1-102">Localization</span></span>

<span data-ttu-id="f22d1-103">Локализацией называется процесс преобразования ресурсов приложения в локализованные версии для конкретных языков и региональных параметров, которые приложение должно поддерживать.</span><span class="sxs-lookup"><span data-stu-id="f22d1-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="f22d1-104">К этапу локализации следует приступать только после [проверки локализуемости](localizability-review.md), которая позволяет проверить готовность глобализованного приложения к локализации.</span><span class="sxs-lookup"><span data-stu-id="f22d1-104">You should proceed to the localization step only after completing the [Localizability Review](localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="f22d1-105">Готовое к локализации приложение разделяется на два логических блока. Один из них содержит все элементы пользовательского интерфейса, а другой — исполняемый код.</span><span class="sxs-lookup"><span data-stu-id="f22d1-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="f22d1-106">Блок пользовательского интерфейса содержит только локализуемые элементы, например строки, сообщения об ошибках, диалоговые окна, пункты меню, внедренные объектные ресурсы и т. д. для нейтрального языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="f22d1-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="f22d1-107">Блок кода содержит только код приложения, который будет одинаковым для всех поддерживаемых языков и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="f22d1-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="f22d1-108">Общеязыковая среда выполнения поддерживает модель ресурсов вспомогательной сборки, в которой исполняемый код приложения отделен от его ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f22d1-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="f22d1-109">Более подробную информацию о реализации этой модели см. в статье [Ресурсы в .NET](../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="f22d1-109">For more information about implementing this model, see [Resources in .NET](../../framework/resources/index.md).</span></span>

<span data-ttu-id="f22d1-110">Для каждой локализованной версии приложения добавьте новую вспомогательную сборку, которая содержит локализованный блок пользовательского интерфейса, учитывающий все требования целевого языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="f22d1-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="f22d1-111">Блок кода должен оставаться одинаковым для всех языков и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="f22d1-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="f22d1-112">Объединение локализованной версии блока пользовательского интерфейса с блоком кода создает новую локализованную версию приложения.</span><span class="sxs-lookup"><span data-stu-id="f22d1-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="f22d1-113">В пакете средств разработки (SDK) Windows предоставляется редактор ресурсов Windows Forms (Winres.exe), позволяющий быстро локализовать ресурсы Windows Forms для целевых языков и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="f22d1-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="f22d1-114">Сведения об использовании этого инструмента см. в статье [Winres.exe (редактор ресурсов Windows Forms)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="f22d1-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f22d1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f22d1-115">See also</span></span>

- [<span data-ttu-id="f22d1-116">Глобализация и локализация</span><span class="sxs-lookup"><span data-stu-id="f22d1-116">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="f22d1-117">Анализ локализуемости</span><span class="sxs-lookup"><span data-stu-id="f22d1-117">Localizability Review</span></span>](localizability-review.md)
- [<span data-ttu-id="f22d1-118">Глобализация</span><span class="sxs-lookup"><span data-stu-id="f22d1-118">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="f22d1-119">Ресурсы в приложениях для настольных систем</span><span class="sxs-lookup"><span data-stu-id="f22d1-119">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
