---
title: События изменения свойств
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105773"
---
# <a name="property-changed-events"></a><span data-ttu-id="cc73b-102">События изменения свойств</span><span class="sxs-lookup"><span data-stu-id="cc73b-102">Property-Changed Events</span></span>
<span data-ttu-id="cc73b-103">Если требуется, чтобы элемент управления для отправки уведомлений, когда свойство с именем *PropertyName* изменения, определите событие с именем *PropertyName* `Changed` и метод с именем `On` *PropertyName* `Changed` , генерирующий данное событие.</span><span class="sxs-lookup"><span data-stu-id="cc73b-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="cc73b-104">Соглашение об именовании в Windows Forms — добавить слово *Changed* к имени свойства.</span><span class="sxs-lookup"><span data-stu-id="cc73b-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="cc73b-105">Связанный тип делегата события для события изменения свойств является <xref:System.EventHandler>, и типом данных события является <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="cc73b-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="cc73b-106">Базовый класс <xref:System.Windows.Forms.Control> определяет много событий изменения свойств, таких как <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>и другие.</span><span class="sxs-lookup"><span data-stu-id="cc73b-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="cc73b-107">Общие сведения о событиях, см. в разделе [события](../../../standard/events/index.md) и [события элементов управления Windows Forms](events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cc73b-107">For background information about events, see [Events](../../../standard/events/index.md) and [Events in Windows Forms Controls](events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="cc73b-108">События изменения свойств полезны, так как они позволяют пользователям элемента управления для присоединения обработчиков событий, которые реагируют на изменения.</span><span class="sxs-lookup"><span data-stu-id="cc73b-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="cc73b-109">Если элемент управления должен реагировать на событие изменения свойства, которое, переопределите соответствующие `On` *PropertyName* `Changed` метод вместо присоединения делегата к событию.</span><span class="sxs-lookup"><span data-stu-id="cc73b-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="cc73b-110">Элемент управления обычно отвечает на событие изменения свойства, обновляя другие свойства, либо некоторые или все его поверхности рисования.</span><span class="sxs-lookup"><span data-stu-id="cc73b-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="cc73b-111">В следующем примере показан как `FlashTrackBar` пользовательский элемент управления отвечает на некоторые события изменения свойств, которые он наследует от <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="cc73b-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="cc73b-112">Полный пример см. в разделе [как: Создание элемента управления Windows Forms, показывающего прогресс](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="cc73b-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cc73b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="cc73b-113">See also</span></span>

- [<span data-ttu-id="cc73b-114">События</span><span class="sxs-lookup"><span data-stu-id="cc73b-114">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="cc73b-115">События элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc73b-115">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="cc73b-116">Свойства элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc73b-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
