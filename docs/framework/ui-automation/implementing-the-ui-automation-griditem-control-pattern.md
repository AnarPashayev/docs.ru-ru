---
title: Реализация шаблона элемента управления GridItem модели автоматизации пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: fdaac3cad61f6047201587e48d4377fa61b868af
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043402"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="49661-102">Реализация шаблона элемента управления GridItem модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="49661-103">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="49661-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="49661-104">Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="49661-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="49661-105">В этом разделе приводятся рекомендации и соглашения для реализации <xref:System.Windows.Automation.Provider.IGridItemProvider>, включая сведения о свойствах.</span><span class="sxs-lookup"><span data-stu-id="49661-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="49661-106">Ссылки на дополнительные материалы перечислены в конце раздела.</span><span class="sxs-lookup"><span data-stu-id="49661-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="49661-107">Шаблон элемента управления <xref:System.Windows.Automation.GridItemPattern> используется для поддержки отдельных дочерних элементов управления контейнеров, реализующих <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="49661-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="49661-108">Примеры элементов управления, реализующих данный шаблон элемента управления, см. в разделе [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="49661-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="49661-109">Правила и соглашения реализации</span><span class="sxs-lookup"><span data-stu-id="49661-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="49661-110">При реализации <xref:System.Windows.Automation.Provider.IGridProvider> обратите внимание на следующие правила и соглашения.</span><span class="sxs-lookup"><span data-stu-id="49661-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="49661-111">Координаты сетки отсчитываются от нуля, начиная с верхней левой ячейки с координатами (0, 0).</span><span class="sxs-lookup"><span data-stu-id="49661-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="49661-112">Объединенные ячейки будут передавать свои свойства <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> и <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> на основе свойств их базовой ячейки привязки в соответствии с определением в поставщике автоматизации пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="49661-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="49661-113">Как правило, это будет самая верхняя строка и крайний левый столбец.</span><span class="sxs-lookup"><span data-stu-id="49661-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="49661-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> не предусматривает активные манипуляции с сеткой, такие как объединение или разбиение ячеек.</span><span class="sxs-lookup"><span data-stu-id="49661-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="49661-115">Элементы управления, реализующие <xref:System.Windows.Automation.Provider.IGridItemProvider>, обычно могут быть пройдены (то есть клиент автоматизации пользовательского интерфейса может переходить в соседние элементы управления) с помощью клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="49661-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="49661-116">Обязательные члены для IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="49661-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="49661-117">Следующие свойства и методы обязательны для реализации <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="49661-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="49661-118">Обязательные члены</span><span class="sxs-lookup"><span data-stu-id="49661-118">Required members</span></span>|<span data-ttu-id="49661-119">Тип члена</span><span class="sxs-lookup"><span data-stu-id="49661-119">Member type</span></span>|<span data-ttu-id="49661-120">Примечания</span><span class="sxs-lookup"><span data-stu-id="49661-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="49661-121">Свойство.</span><span class="sxs-lookup"><span data-stu-id="49661-121">Property</span></span>|<span data-ttu-id="49661-122">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="49661-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="49661-123">Свойство.</span><span class="sxs-lookup"><span data-stu-id="49661-123">Property</span></span>|<span data-ttu-id="49661-124">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="49661-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="49661-125">Свойство.</span><span class="sxs-lookup"><span data-stu-id="49661-125">Property</span></span>|<span data-ttu-id="49661-126">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="49661-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="49661-127">Свойство.</span><span class="sxs-lookup"><span data-stu-id="49661-127">Property</span></span>|<span data-ttu-id="49661-128">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="49661-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="49661-129">Свойство.</span><span class="sxs-lookup"><span data-stu-id="49661-129">Property</span></span>|<span data-ttu-id="49661-130">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="49661-130">None</span></span>|  
  
 <span data-ttu-id="49661-131">Этот шаблон элемента управления не имеет связанных методов или событий.</span><span class="sxs-lookup"><span data-stu-id="49661-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="49661-132">Исключения</span><span class="sxs-lookup"><span data-stu-id="49661-132">Exceptions</span></span>  
 <span data-ttu-id="49661-133">Этот шаблон элемента управления не имеет связанных исключений.</span><span class="sxs-lookup"><span data-stu-id="49661-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49661-134">См. также</span><span class="sxs-lookup"><span data-stu-id="49661-134">See also</span></span>

- [<span data-ttu-id="49661-135">Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="49661-136">Поддержка шаблонов элементов управления в поставщике автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="49661-137">Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов</span><span class="sxs-lookup"><span data-stu-id="49661-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="49661-138">Реализация шаблона элемента управления Grid модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="49661-139">Общие сведения о дереве модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="49661-140">Использование кэширования в модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="49661-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
