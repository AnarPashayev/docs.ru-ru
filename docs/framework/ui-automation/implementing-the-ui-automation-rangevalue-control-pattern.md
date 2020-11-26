---
title: Реализация шаблона элемента управления RangeValue автоматизации пользовательского интерфейса
description: Ознакомьтесь с правилами и соглашениями по реализации шаблона элемента управления RangeValue в модели автоматизации пользовательского интерфейса. См. раздел обязательные элементы для интерфейса IRangeValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 9b5bfd571b078b7aeab149f5371004ac832fadcc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239566"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="5f7a8-104">Реализация шаблона элемента управления RangeValue автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5f7a8-104">Implementing the UI Automation RangeValue Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="5f7a8-105">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="5f7a8-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5f7a8-106">Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5f7a8-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5f7a8-107">В этом разделе приводятся рекомендации и соглашения для реализации <xref:System.Windows.Automation.Provider.IRangeValueProvider>, включая сведения о событиях и свойствах.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="5f7a8-108">Ссылки на дополнительные материалы перечислены в конце раздела.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5f7a8-109">Шаблон элемента управления <xref:System.Windows.Automation.RangeValuePattern> используется для поддержки элементов управления, для которых можно установить значение из диапазона.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="5f7a8-110">Примеры элементов управления, реализующих данный шаблон элемента управления, см. в разделе [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5f7a8-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5f7a8-111">Правила и соглашения реализации</span><span class="sxs-lookup"><span data-stu-id="5f7a8-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="5f7a8-112">При реализации шаблона элемента управления Range Value обратите внимание на следующие правила и соглашения.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5f7a8-113">Элементы управления позволяют повторную калибровку своих поддерживаемых свойств на основе языкового стандарта или предпочтений пользователя.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="5f7a8-114">Примером этого является элемент управления "Термометр", который можно задать для отображения температуры в шкале Цельсия или Фаренгейта.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="5f7a8-115">Элементы управления, имеющие неоднозначные значения диапазона, такие как индикаторы выполнения или ползунки, должны нормализовать эти значения.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="5f7a8-116">![Индикатор выполнения.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="5f7a8-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="5f7a8-117">Пример индикатора выполнения, где значение имеет тип Integer, а минимальное и максимальное значения свойства нормализованы до 0 и 100 соответственно</span><span class="sxs-lookup"><span data-stu-id="5f7a8-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>

## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="5f7a8-118">Обязательные члены для IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="5f7a8-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="5f7a8-119">Обязательный член</span><span class="sxs-lookup"><span data-stu-id="5f7a8-119">Required member</span></span>|<span data-ttu-id="5f7a8-120">Тип члена</span><span class="sxs-lookup"><span data-stu-id="5f7a8-120">Member type</span></span>|<span data-ttu-id="5f7a8-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="5f7a8-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="5f7a8-122">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-122">Property</span></span>|<span data-ttu-id="5f7a8-123">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="5f7a8-124">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-124">Property</span></span>|<span data-ttu-id="5f7a8-125">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="5f7a8-126">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-126">Property</span></span>|<span data-ttu-id="5f7a8-127">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="5f7a8-128">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-128">Property</span></span>|<span data-ttu-id="5f7a8-129">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="5f7a8-130">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-130">Property</span></span>|<span data-ttu-id="5f7a8-131">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="5f7a8-132">Свойство.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-132">Property</span></span>|<span data-ttu-id="5f7a8-133">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="5f7a8-134">Методы</span><span class="sxs-lookup"><span data-stu-id="5f7a8-134">Methods</span></span>|<span data-ttu-id="5f7a8-135">Нет</span><span class="sxs-lookup"><span data-stu-id="5f7a8-135">None</span></span>|  
  
 <span data-ttu-id="5f7a8-136">Этот шаблон элемента управления не имеет связанных событий.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="5f7a8-137">Исключения</span><span class="sxs-lookup"><span data-stu-id="5f7a8-137">Exceptions</span></span>  

 <span data-ttu-id="5f7a8-138">Поставщики должны вызывать следующие исключения.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5f7a8-139">Тип исключения</span><span class="sxs-lookup"><span data-stu-id="5f7a8-139">Exception type</span></span>|<span data-ttu-id="5f7a8-140">Условие</span><span class="sxs-lookup"><span data-stu-id="5f7a8-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="5f7a8-141">Метод<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> вызывается со значением либо больше, чем <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> , либо меньше, чем <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="5f7a8-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f7a8-142">См. также</span><span class="sxs-lookup"><span data-stu-id="5f7a8-142">See also</span></span>

- [<span data-ttu-id="5f7a8-143">Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5f7a8-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5f7a8-144">Поддержка шаблонов элементов управления в поставщике модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5f7a8-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5f7a8-145">Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов</span><span class="sxs-lookup"><span data-stu-id="5f7a8-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5f7a8-146">Общие сведения о дереве модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5f7a8-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="5f7a8-147">Использование кэширования в модели автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5f7a8-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
