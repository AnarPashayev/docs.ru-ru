---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614895"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="9ada7-101">Стек сенсорного управления WPF на основе указателя</span><span class="sxs-lookup"><span data-stu-id="9ada7-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="9ada7-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="9ada7-102">Details</span></span>

<span data-ttu-id="9ada7-103">Это изменение добавляет возможность включать необязательный стек сенсорного управления или пера WPF на основе WM_POINTER.</span><span class="sxs-lookup"><span data-stu-id="9ada7-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="9ada7-104">Разработчики, которые явно не включают эту поддержку, не должны заметить изменений в поведении сенсорного управления или пера WPF. Известные на данный момент проблемы с необязательным стеком сенсорного управления или пера на основе WM_POINTER:</span><span class="sxs-lookup"><span data-stu-id="9ada7-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="9ada7-105">Не поддерживается рукописный ввод в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="9ada7-105">No support for real-time inking.</span></span>
- <span data-ttu-id="9ada7-106">Хотя подключаемые модули рукописного ввода и пера продолжают работать, они обрабатываются в потоке пользовательского интерфейса, что может вести к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="9ada7-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="9ada7-107">Изменения поведения из-за изменений в переходе от событий сенсорного управления или пера к событиям мыши.</span><span class="sxs-lookup"><span data-stu-id="9ada7-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="9ada7-108">Обработка может выполняться по-разному.</span><span class="sxs-lookup"><span data-stu-id="9ada7-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="9ada7-109">При перетаскивании не будет показана соответствующая реакция на сенсорный ввод</span><span class="sxs-lookup"><span data-stu-id="9ada7-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="9ada7-110">(это не влияет на ввод с помощью пера).</span><span class="sxs-lookup"><span data-stu-id="9ada7-110">This does not affect stylus input</span></span>
- <span data-ttu-id="9ada7-111">Перетаскивание больше нельзя инициировать при событиях сенсорного управления или пера.</span><span class="sxs-lookup"><span data-stu-id="9ada7-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="9ada7-112">Это потенциально может вызвать зависание приложения до обнаружения ввода с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="9ada7-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="9ada7-113">Вместо этого разработчикам следует инициировать перетаскивание с помощью событий мыши.</span><span class="sxs-lookup"><span data-stu-id="9ada7-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9ada7-114">Предложение</span><span class="sxs-lookup"><span data-stu-id="9ada7-114">Suggestion</span></span>

<span data-ttu-id="9ada7-115">Разработчики, желающие включить этот стек, могут добавить следующую информацию в файл app.config своего приложения:</span><span class="sxs-lookup"><span data-stu-id="9ada7-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="9ada7-116">Удаление этого параметра или присвоение ему значения false позволяет отключить этот необязательный стек. Обратите внимание, что этот стек доступен только в Windows 10 Creators Update и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="9ada7-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="9ada7-117">name</span><span class="sxs-lookup"><span data-stu-id="9ada7-117">Name</span></span>    | <span data-ttu-id="9ada7-118">Значение</span><span class="sxs-lookup"><span data-stu-id="9ada7-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9ada7-119">Область</span><span class="sxs-lookup"><span data-stu-id="9ada7-119">Scope</span></span>   | <span data-ttu-id="9ada7-120">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="9ada7-120">Edge</span></span>        |
| <span data-ttu-id="9ada7-121">Version</span><span class="sxs-lookup"><span data-stu-id="9ada7-121">Version</span></span> | <span data-ttu-id="9ada7-122">4.7</span><span class="sxs-lookup"><span data-stu-id="9ada7-122">4.7</span></span>         |
| <span data-ttu-id="9ada7-123">Type</span><span class="sxs-lookup"><span data-stu-id="9ada7-123">Type</span></span>    | <span data-ttu-id="9ada7-124">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="9ada7-124">Retargeting</span></span> |
