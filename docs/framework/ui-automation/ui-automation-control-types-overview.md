---
title: Общие сведения о типах элементов управления автоматизации пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: e9cbff2ec6496cabe827e075b737a8c6f16fee93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147723"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="4c98f-102">Общие сведения о типах элементов управления автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="4c98f-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="4c98f-103">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="4c98f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4c98f-104">Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4c98f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="4c98f-105">типы элементов управления, хорошо известные идентификаторы, которые можно использовать для указания элемента управления определенного элемента вида, например поле со списком или кнопки.</span><span class="sxs-lookup"><span data-stu-id="4c98f-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="4c98f-106">Известный идентификатор упрощает для вспомогательных устройств определение типов элементов управления, доступных в [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , и способов взаимодействия с ними.</span><span class="sxs-lookup"><span data-stu-id="4c98f-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="4c98f-107">Необходимые компоненты элементов управления автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="4c98f-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="4c98f-108">типы элементов управления предоставляют набор условий, которым должны соответствовать поставщики.</span><span class="sxs-lookup"><span data-stu-id="4c98f-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="4c98f-109">При выполнении этих условий элемент управления может использовать имя типа определенного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="4c98f-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="4c98f-110">Каждый тип элемента управления использует следующие условия:</span><span class="sxs-lookup"><span data-stu-id="4c98f-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="4c98f-111">шаблоны элементов управления, какие шаблоны элементов управления должны поддерживаться, какой элемент управления шаблоны являются необязательными и какие шаблоны элементов управления не должны поддерживаться элементом управления.</span><span class="sxs-lookup"><span data-stu-id="4c98f-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="4c98f-112">значения свойств, какие значения свойств поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4c98f-112">property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="4c98f-113">древовидная структура, необходимая [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] древовидная структура для элемента управления.</span><span class="sxs-lookup"><span data-stu-id="4c98f-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="4c98f-114">Если элемент управления удовлетворяет условиям определенного типа элемента управления, значение свойства <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> указывает этот тип.</span><span class="sxs-lookup"><span data-stu-id="4c98f-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="4c98f-115">Текущие типы элементов управления автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="4c98f-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="4c98f-116">Следующий список содержит текущий набор типов элементов управления [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="4c98f-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="4c98f-117">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления кнопки</span><span class="sxs-lookup"><span data-stu-id="4c98f-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="4c98f-118">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Calendar</span><span class="sxs-lookup"><span data-stu-id="4c98f-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-119">Поддержка модели автоматизированного пользовательского интерфейса для элемента управления CheckBox</span><span class="sxs-lookup"><span data-stu-id="4c98f-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="4c98f-120">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ComboBox</span><span class="sxs-lookup"><span data-stu-id="4c98f-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="4c98f-121">Поддержка автоматизированного пользовательского интерфейса для типа элемента управления DataGrid</span><span class="sxs-lookup"><span data-stu-id="4c98f-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="4c98f-122">Поддержка автоматизации пользовательского интерфейса для элемента управления типа DataItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-123">Поддержка автоматизированного пользовательского интерфейса для типа элемента управления Document</span><span class="sxs-lookup"><span data-stu-id="4c98f-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="4c98f-124">Поддержка автоматизации пользовательского интерфейса для типа элемента управления "Поле вода"</span><span class="sxs-lookup"><span data-stu-id="4c98f-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="4c98f-125">Поддержка автоматизации пользовательского интерфейса для типа элемента управления Group</span><span class="sxs-lookup"><span data-stu-id="4c98f-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="4c98f-126">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления "Заголовок"</span><span class="sxs-lookup"><span data-stu-id="4c98f-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="4c98f-127">Поддержка модели автоматизации пользовательского интерфейса типа элемента управления HeaderItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-128">Поддержка автоматизированного пользовательского интерфейса для элемента управления типа Hyperlink</span><span class="sxs-lookup"><span data-stu-id="4c98f-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="4c98f-129">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления изображения</span><span class="sxs-lookup"><span data-stu-id="4c98f-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="4c98f-130">Поддержка модели автоматизации пользовательского интерфейса для элемента управления "Список"</span><span class="sxs-lookup"><span data-stu-id="4c98f-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="4c98f-131">Поддержка автоматизированного пользовательского интерфейса для типа элемента управления ListItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-132">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления меню</span><span class="sxs-lookup"><span data-stu-id="4c98f-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="4c98f-133">Поддержка автоматизации пользовательского интерфейса для типа элемента управления MenuBar</span><span class="sxs-lookup"><span data-stu-id="4c98f-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-134">Поддержка автоматизации пользовательского интерфейса для типа элемента управления MenuItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-135">Поддержка автоматизации пользовательского интерфейса для элемента управления Pane</span><span class="sxs-lookup"><span data-stu-id="4c98f-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="4c98f-136">Поддержка автоматизации пользовательского интерфейса для типа элемента управления ProgressBar</span><span class="sxs-lookup"><span data-stu-id="4c98f-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-137">Поддержка автоматизации пользовательского интерфейса для элемента управления типа RadioButton</span><span class="sxs-lookup"><span data-stu-id="4c98f-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="4c98f-138">Поддержка автоматизации пользовательского интерфейса для типа элемента управления ScrollBar</span><span class="sxs-lookup"><span data-stu-id="4c98f-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-139">Поддержка автоматизации пользовательского интерфейса для элемента управления Separator</span><span class="sxs-lookup"><span data-stu-id="4c98f-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="4c98f-140">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления ползунка</span><span class="sxs-lookup"><span data-stu-id="4c98f-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="4c98f-141">Поддержка Автоматизации Пользовательского Интерфейса для типа элемента управления "Счетчик"</span><span class="sxs-lookup"><span data-stu-id="4c98f-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="4c98f-142">Поддержка автоматизации пользовательского интерфейса для типа элемента управления SplitButton</span><span class="sxs-lookup"><span data-stu-id="4c98f-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="4c98f-143">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления StatusBar</span><span class="sxs-lookup"><span data-stu-id="4c98f-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-144">Поддержка UI Automation для типа элемента управления Tab</span><span class="sxs-lookup"><span data-stu-id="4c98f-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="4c98f-145">Поддержка автоматизации пользовательского интерфейса для типа элемента управления TabItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-146">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Table</span><span class="sxs-lookup"><span data-stu-id="4c98f-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="4c98f-147">Поддержка автоматизированного пользовательского интерфейса для текстовых элементов управления</span><span class="sxs-lookup"><span data-stu-id="4c98f-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="4c98f-148">Поддержка автоматизации пользовательского интерфейса для элемента управления типа Thumb</span><span class="sxs-lookup"><span data-stu-id="4c98f-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="4c98f-149">Поддержка Автоматизации Пользовательского Интерфейса для Элементов Управления Типа "Заголовок Окна"</span><span class="sxs-lookup"><span data-stu-id="4c98f-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-150">Поддержка автоматизации пользовательского интерфейса для типа элемента управления ToolBar</span><span class="sxs-lookup"><span data-stu-id="4c98f-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="4c98f-151">Поддержка автоматизации пользовательского интерфейса для типа элементов управления ToolTip</span><span class="sxs-lookup"><span data-stu-id="4c98f-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="4c98f-152">Поддержка автоматизации пользовательского интерфейса для древовидного типа элемента управления</span><span class="sxs-lookup"><span data-stu-id="4c98f-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="4c98f-153">Поддержка автоматизации пользовательского интерфейса для типа элемента управления TreeItem</span><span class="sxs-lookup"><span data-stu-id="4c98f-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="4c98f-154">Поддержка модели автоматизации пользовательского интерфейса для типа элемента управления Window</span><span class="sxs-lookup"><span data-stu-id="4c98f-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c98f-155">См. также</span><span class="sxs-lookup"><span data-stu-id="4c98f-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
