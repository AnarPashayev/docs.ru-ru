---
title: расширение разметки x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938883"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="78dab-102">расширение разметки x:Reference</span><span class="sxs-lookup"><span data-stu-id="78dab-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="78dab-103">Ссылается на экземпляр, который объявлен в другом месте в разметке XAML.</span><span class="sxs-lookup"><span data-stu-id="78dab-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="78dab-104">Ссылка на элемент `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="78dab-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="78dab-105">Использование атрибута XAML</span><span class="sxs-lookup"><span data-stu-id="78dab-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="78dab-106">Использование элемента объекта XAML</span><span class="sxs-lookup"><span data-stu-id="78dab-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="78dab-107">Значения XAML</span><span class="sxs-lookup"><span data-stu-id="78dab-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="78dab-108">`x:Name` Значение (или значение <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-определить свойства) экземпляра, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="78dab-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78dab-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="78dab-109">Remarks</span></span>  
 <span data-ttu-id="78dab-110">`x:Reference` обеспечивает поддержку уровня языка XAML понятие ссылки элемент, в противном случае было реализовано в конкретных платформах, таких как WPF.</span><span class="sxs-lookup"><span data-stu-id="78dab-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="78dab-111">x: Reference и WPF</span><span class="sxs-lookup"><span data-stu-id="78dab-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="78dab-112">В WPF и XAML 2006, ссылки на элементы будут удовлетворены функцией уровня платформы <xref:System.Windows.Data.Binding.ElementName%2A> привязки.</span><span class="sxs-lookup"><span data-stu-id="78dab-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="78dab-113">Для большинства приложений WPF и сценариев <xref:System.Windows.Data.Binding.ElementName%2A> привязка должна использоваться.</span><span class="sxs-lookup"><span data-stu-id="78dab-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="78dab-114">Исключения из этого общего правила могут быть случаи, где контекст данных или другие соображения, которые делают нецелесообразным привязки данных и не участвует компиляции разметки.</span><span class="sxs-lookup"><span data-stu-id="78dab-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="78dab-115">`x:Reference` Это конструкция, определенные в XAML 2009 г.</span><span class="sxs-lookup"><span data-stu-id="78dab-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="78dab-116">В WPF можно использовать возможности XAML 2009, но только для кода XAML, не скомпилированного с разметкой WPF.</span><span class="sxs-lookup"><span data-stu-id="78dab-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="78dab-117">Скомпилированный XAML с разметкой и форма BAML кода XAML пока не поддерживают ключевые слова языка и компоненты XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="78dab-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
