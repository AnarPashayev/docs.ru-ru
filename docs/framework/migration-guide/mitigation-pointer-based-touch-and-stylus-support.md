---
title: Устранение рисков. Поддержка сенсорного управления и пера на основе указателя
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9264d8eb7923663061f9bccfffe5b8f5254549f0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379891"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="fc074-102">Устранение рисков. Поддержка сенсорного управления и пера на основе указателя</span><span class="sxs-lookup"><span data-stu-id="fc074-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="fc074-103">В приложениях WPF, предназначенных 4.7 .NET Framework и выполняемых в системах Windows, начиная с версии Windows 10 Creators Update, можно включить дополнительный стек сенсорного управления и пера WPF на основе `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="fc074-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="fc074-104">Последствия</span><span class="sxs-lookup"><span data-stu-id="fc074-104">Impact</span></span>

<span data-ttu-id="fc074-105">Разработчики, которые явно не включают поддержку сенсорного управления или пера на основе указателя, не должны заметить изменений в поведении сенсорного управления или пера WPF.</span><span class="sxs-lookup"><span data-stu-id="fc074-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="fc074-106">Ниже перечислены текущие известные проблемы с дополнительным стеком сенсорного управления и пера на основе `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="fc074-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="fc074-107">Не поддерживается рукописный ввод в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="fc074-107">No support for real-time inking.</span></span>

   <span data-ttu-id="fc074-108">Хотя подключаемые модули рукописного ввода и пера продолжают работать, они обрабатываются в потоке пользовательского интерфейса, что может вести к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="fc074-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="fc074-109">Изменения поведения из-за изменений в переходе от событий сенсорного управления или пера к событиям мыши.</span><span class="sxs-lookup"><span data-stu-id="fc074-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="fc074-110">Обработка может выполняться по-разному.</span><span class="sxs-lookup"><span data-stu-id="fc074-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="fc074-111">При перетаскивании не будет показана соответствующая реакция на сенсорный ввод.</span><span class="sxs-lookup"><span data-stu-id="fc074-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="fc074-112">(Это не влияет на ввод с помощью пера).</span><span class="sxs-lookup"><span data-stu-id="fc074-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="fc074-113">Перетаскивание больше нельзя инициировать при событиях сенсорного управления или пера.</span><span class="sxs-lookup"><span data-stu-id="fc074-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="fc074-114">Это потенциально может вызвать зависание приложения до обнаружения ввода с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="fc074-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="fc074-115">Вместо этого разработчикам следует инициировать перетаскивание с помощью событий мыши.</span><span class="sxs-lookup"><span data-stu-id="fc074-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="fc074-116">Выбор поддержки сенсорного управления и пера на основе WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="fc074-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="fc074-117">Разработчики, желающие включить этот стек, могут добавить следующую информацию в файл app.config своего приложения:</span><span class="sxs-lookup"><span data-stu-id="fc074-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="fc074-118">Удаление этой записи или присвоение ей значения `false` отключает данный дополнительный стек.</span><span class="sxs-lookup"><span data-stu-id="fc074-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc074-119">См. также</span><span class="sxs-lookup"><span data-stu-id="fc074-119">See also</span></span>

- [<span data-ttu-id="fc074-120">Изменения целевой платформы в .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fc074-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
