---
title: Ограничения свойства Interval компонента Timer в Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: a9c4fda179e45ad2cf2ee2183e5881e97b763cdc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644929"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="1931a-102">Ограничения свойства Interval компонента Timer в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1931a-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="1931a-103">Windows Forms <xref:System.Windows.Forms.Timer> компонент имеет <xref:System.Windows.Forms.Timer.Interval%2A> свойство, которое указывает количество миллисекунд, которые проходят между событие одного таймера, а также следующие.</span><span class="sxs-lookup"><span data-stu-id="1931a-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="1931a-104">Если компонент отключен, таймер для получения <xref:System.Windows.Forms.Timer.Tick> событий через приблизительно равные интервалы времени.</span><span class="sxs-lookup"><span data-stu-id="1931a-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="1931a-105">Этот компонент предназначен для работы в среде Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1931a-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="1931a-106">Если вам требуется таймер, подходящий для серверной среды, см. раздел [Общие сведения о серверных таймерах](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1931a-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="1931a-107">Свойство «интервал»</span><span class="sxs-lookup"><span data-stu-id="1931a-107">The Interval Property</span></span>  
 <span data-ttu-id="1931a-108"><xref:System.Windows.Forms.Timer.Interval%2A> Свойство имеет несколько ограничений, которые следует учитывать при программировании <xref:System.Windows.Forms.Timer> компонента:</span><span class="sxs-lookup"><span data-stu-id="1931a-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="1931a-109">Если приложение или другое приложение интенсивно потребляет системы — например длинные циклы, с большим объемом вычислений, или диска, сети или доступа к портам — приложение не может получить события таймера так часто, как <xref:System.Windows.Forms.Timer.Interval%2A> указывает свойство.</span><span class="sxs-lookup"><span data-stu-id="1931a-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="1931a-110">Интервал истечет точно вовремя не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="1931a-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="1931a-111">Для обеспечения точности, таймер следует проверить системные часы, при необходимости, а не повторите для отслеживания накопленные временные внутренним образом.</span><span class="sxs-lookup"><span data-stu-id="1931a-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="1931a-112">Точность <xref:System.Windows.Forms.Timer.Interval%2A> свойство указывается в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="1931a-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="1931a-113">Некоторые компьютеры имеют счетчик высокого разрешения, более высокую точность разрешение.</span><span class="sxs-lookup"><span data-stu-id="1931a-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="1931a-114">Доступность такого счетчика зависит от оборудования процессора компьютера.</span><span class="sxs-lookup"><span data-stu-id="1931a-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1931a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1931a-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="1931a-116">Компонент Timer</span><span class="sxs-lookup"><span data-stu-id="1931a-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="1931a-117">Общие сведения о компоненте Timer</span><span class="sxs-lookup"><span data-stu-id="1931a-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
