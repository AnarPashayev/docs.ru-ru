---
title: Общие сведения об элементе управления ToolStripPanel
ms.date: 03/30/2017
f1_keywords:
- ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
ms.openlocfilehash: 694cb88807f718a1f3122ae8cd9d7d4af4e576e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009374"
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="807e8-102">Общие сведения об элементе управления ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="807e8-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="807e8-103">Объект <xref:System.Windows.Forms.ToolStripPanel> предоставляет одну область для размещения и нависания <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, и <xref:System.Windows.Forms.StatusStrip> элементов управления.</span><span class="sxs-lookup"><span data-stu-id="807e8-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="807e8-104">Несколько <xref:System.Windows.Forms.ToolStrip> стека элементов управления по вертикали или по горизонтали в зависимости от <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> из <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="807e8-105">ToolStripPanel важные члены</span><span class="sxs-lookup"><span data-stu-id="807e8-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="807e8-106">name</span><span class="sxs-lookup"><span data-stu-id="807e8-106">Name</span></span>|<span data-ttu-id="807e8-107">Описание</span><span class="sxs-lookup"><span data-stu-id="807e8-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="807e8-108">Возвращает или задает значение, указывающее горизонтальную или вертикальную ориентацию <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="807e8-109">Возвращает или задает <xref:System.Windows.Forms.ToolStripRenderer> используется для настройки внешнего вида <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="807e8-110">Возвращает или задает стили оформления элемента управления для применения к <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="807e8-111">Возвращает или задает расстояние в пикселях между <xref:System.Windows.Forms.ToolStripPanelRow> и <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="807e8-112">Получает <xref:System.Windows.Forms.ToolStripPanelRow> в этом <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="807e8-113">Добавляет объект <xref:System.Windows.Forms.ToolStrip> в <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="807e8-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="807e8-114">См. также</span><span class="sxs-lookup"><span data-stu-id="807e8-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
- <span data-ttu-id="807e8-115">[Пример элемента управления ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms181005(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="807e8-115">[ToolStrip Sample](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms181005(v=vs.90))</span></span>
