---
title: Расширение разметки StaticResource
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: c160322fb3834fcd705c0482f5e55c8da32d143b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141255"
---
# <a name="staticresource-markup-extension"></a>Расширение разметки StaticResource
Предоставляет значение для любого [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] атрибута свойства путем поиска ссылки на уже определенный ресурс. Поведение подстановки для этого ресурса аналогично поиску во время загрузки, который будет искать ресурсы, ранее загруженные из разметки текущей [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] страницы, а также другие источники приложений, и будет создавать это значение ресурса в качестве значения свойства в объектах времени выполнения.  
  
## <a name="xaml-attribute-usage"></a>Использование атрибута XAML  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a>Использование элемента объекта XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Значения XAML  
  
|||  
|-|-|  
|`key`|Ключ для запрашиваемого ресурса. Этот ключ изначально был назначен [директивой x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) , если ресурс был создан в разметке, или был предоставлен в `key` качестве параметра при <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> вызове, если ресурс был создан в коде.|  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
> Не `StaticResource` должна пытаться сделать прямую ссылку на ресурс, который определен лексически в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] файле. Попытка сделать это не поддерживается, и даже если такая ссылка не завершается ошибкой, попытка пересылки ссылки приведет к снижению производительности во время загрузки при поиске внутренних хэш-таблиц, представляющих собой <xref:System.Windows.ResourceDictionary> . Для достижения лучших результатов измените композицию словарей ресурсов таким образом, чтобы можно было избежать пересылки ссылок. Если вы не можете избежать прямой ссылки, используйте вместо этого [расширение разметки DynamicResource](dynamicresource-markup-extension.md) .  
  
 Указанное <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> значение должно соответствовать существующему ресурсу, идентифицированному с помощью [директивы x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) на определенном уровне страницы, приложения, доступных тем элементов управления и внешних ресурсов, а также системных ресурсов. Поиск ресурсов выполняется в указанном порядке. Дополнительные сведения о поведении поиска ресурсов для статических и динамических ресурсов см. в разделе [ресурсы XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Ключ ресурса может быть любой строкой, определенной в [грамматике имяxaml](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Ключ ресурса также может быть другими типами объектов, например <xref:System.Type>. <xref:System.Type> Ключом является фундаментальное понятие того, как элементы управления могут быть оформлены темами с помощью неявного ключа стиля. Дополнительные сведения см. в разделе [Общие сведения о разработке элементов управления](../controls/control-authoring-overview.md).  
  
 Альтернативные декларативные средства для ссылки на ресурс — это [расширение разметки DynamicResource](dynamicresource-markup-extension.md).  
  
 Синтаксис атрибутов является наиболее распространенным синтаксисом, используемым с этим расширением разметки. Строковая лексема, указываемая после строки идентификатора `StaticResource`, присваивается в качестве значения <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> соответствующего класса расширения <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource`может использоваться в синтаксисе объектного элемента. В этом случае указание значения <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> свойства обязательно.  
  
 Излишним может оказаться и использование `StaticResource` в атрибуте, в котором свойство <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> определено как пара "свойство=значение".  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 Подробное определение зачастую удобно использовать для расширений, которые имеют несколько устанавливаемых свойств, а также в том случае, если некоторые свойства являются необязательными. Так как `StaticResource` имеет только одно устанавливаемое свойство, которое является обязательным, это использование не является типичным.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] В реализации процессора обработка этого расширения разметки определяется <xref:System.Windows.StaticResourceExtension> классом.  
  
 `StaticResource` является расширением разметки. Расширения разметки обычно реализуются, если требуется заменить значения атрибутов на нелитеральные значения или имена обработчиков и если требуется больше, чем простая настройка преобразователей типов на работу с определенными типами или свойствами. Все расширения разметки в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] используют символы "{" и "}" в синтаксисе их атрибутов, который является соглашением, по которому обработчик [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] распознает, что расширение разметки должно обработать атрибут. Дополнительные сведения см. в разделе [Расширения разметки и XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>См. также

- [Стилизация и использование шаблонов](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Обзор XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Расширения разметки и XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Ресурсы XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ресурсы и код](resources-and-code.md)
