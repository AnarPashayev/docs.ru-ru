---
title: Практическое руководство. Создание и определение пользовательского средства визуализации для элемента управления ToolStrip в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: d8a85edf8c001b19191fdfd74d1f9ebdf87024ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195492"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="54106-102">Практическое руководство. Создание и определение пользовательского средства визуализации для элемента управления ToolStrip в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54106-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<xref:System.Windows.Forms.ToolStrip> <span data-ttu-id="54106-103">элементы управления обеспечивают удобную поддержку тем и стилей.</span><span class="sxs-lookup"><span data-stu-id="54106-103">controls give easy support to themes and styles.</span></span> <span data-ttu-id="54106-104">Полностью настраиваемый внешний вид и поведение (оформление) можно добиться путем задания либо <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> свойство или <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> свойства для пользовательского средства визуализации.</span><span class="sxs-lookup"><span data-stu-id="54106-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="54106-105">Модули подготовки отчетов можно назначить для каждого отдельного <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, или <xref:System.Windows.Forms.StatusStrip> элемента управления, или же можно использовать <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> свойства влияют на все объекты, задав <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> свойства <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54106-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <span data-ttu-id="54106-106">Возвращает <xref:System.Windows.Forms.ToolStripRenderMode.Custom> только если значение <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> не `null`.</span><span class="sxs-lookup"><span data-stu-id="54106-106">returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="54106-107">Чтобы создать пользовательское средство отрисовки</span><span class="sxs-lookup"><span data-stu-id="54106-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="54106-108">Расширить <xref:System.Windows.Forms.ToolStripRenderer> класса.</span><span class="sxs-lookup"><span data-stu-id="54106-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="54106-109">Реализуйте требуемого пользовательской отрисовки путем переопределения соответствующих *на...*</span><span class="sxs-lookup"><span data-stu-id="54106-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="54106-110">члены</span><span class="sxs-lookup"><span data-stu-id="54106-110">members</span></span>  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="54106-111">Чтобы задать пользовательское средство отрисовки к быть текущий модуль подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="54106-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="54106-112">Чтобы задать пользовательское средство отрисовки для одного <xref:System.Windows.Forms.ToolStrip>, задайте <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> свойство пользовательского средства визуализации.</span><span class="sxs-lookup"><span data-stu-id="54106-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="54106-113">Или задать пользовательское средство отрисовки для всех <xref:System.Windows.Forms.ToolStrip> классов, содержащихся в приложении: Задайте <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> свойства в пользовательское средство отрисовки и задайте <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> свойства <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="54106-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="54106-114">См. также</span><span class="sxs-lookup"><span data-stu-id="54106-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="54106-115">Общие сведения об элементе управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="54106-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="54106-116">Архитектура элемента управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="54106-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="54106-117">Технологии, положенные в основу работы элемента управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="54106-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
