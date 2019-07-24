---
title: 'Оптимизация производительности: Привязка данных'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401450"
---
# <a name="optimizing-performance-data-binding"></a>Оптимизация производительности: Привязка данных
Привязка данных [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] предоставляет приложениям простой и последовательный способ представления данных и взаимодействия с ними. Элементы могут быть привязаны к данным из различных источников данных в виде объектов CLR и [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 В этом разделе даются рекомендации по повышению производительности привязки данных.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Как разрешаются ссылки для привязки данных  
 Прежде чем обсуждать вопросы производительности привязки данных, стоит изучить, как механизм привязки данных [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] разрешает ссылки на объекты для привязки.  
  
 Источником [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] привязки данных может быть любой объект CLR. Можно выполнить привязку к свойствам, вложенным свойствам или индексаторам объекта CLR. Ссылки привязки разрешаются либо с помощью Microsoft .NET отражения платформы, либо <xref:System.ComponentModel.ICustomTypeDescriptor>из. Ниже приведены три метода для разрешения ссылок на объекты для привязки.  
  
 Первый метод включает использование отражения. В этом случае <xref:System.Reflection.PropertyInfo> объект используется для обнаружения атрибутов свойства и предоставляет доступ к метаданным свойств. При использовании <xref:System.ComponentModel.ICustomTypeDescriptor> интерфейса подсистема привязки данных использует этот интерфейс для доступа к значениям свойств. <xref:System.ComponentModel.ICustomTypeDescriptor> Интерфейс особенно полезен в случаях, когда объект не имеет статического набора свойств.  
  
 Уведомления об изменении свойств можно предоставить либо путем реализации <xref:System.ComponentModel.INotifyPropertyChanged> интерфейса, либо с помощью уведомлений об изменениях, связанных <xref:System.ComponentModel.TypeDescriptor>с. Однако предпочтительной стратегией для реализации уведомлений об изменении свойств является использование <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Если исходный объект является объектом CLR, а свойство Source является свойством CLR, то [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] обработчику привязки данных необходимо сначала использовать отражение для исходного объекта <xref:System.ComponentModel.TypeDescriptor>, чтобы получить объект, <xref:System.ComponentModel.PropertyDescriptor>а затем запросить. Эта последовательность операций отражения может занимать очень много времени с точки зрения производительности.  
  
 Вторым методом разрешения ссылок на объекты является исходный объект CLR, реализующий <xref:System.ComponentModel.INotifyPropertyChanged> интерфейс, и свойство Source, которое является свойством CLR. В этом случае механизм привязки данных использует отражение непосредственно в исходном типе и возвращает необходимое свойство. Это по-прежнему не самый оптимальный метод, но он предъявляет меньше требований к рабочему набору, чем первый метод.  
  
 Третий способ разрешения ссылок на объекты — это исходный объект, который является <xref:System.Windows.DependencyObject> объектом, а свойство Source <xref:System.Windows.DependencyProperty>—. В этом случае механизму привязки данных не нужно использовать отражение. Вместо этого механизм свойства и механизм привязки данных оба разрешают ссылку на свойство независимо. Это оптимальный метод для разрешения ссылок на объекты, используемые для привязки данных.  
  
 В следующей таблице сравнивается скорость привязки <xref:System.Windows.Controls.TextBlock.Text%2A> данных свойства элементов 1000 <xref:System.Windows.Controls.TextBlock> с помощью этих трех методов.  
  
|**Привязка свойства Text объекта TextBlock**|**Время привязки (мс)**|**Время отрисовки — включает привязку (мс)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|К свойству объекта CLR|115|314|  
|К свойству объекта CLR, реализующего<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|К a <xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Привязка к большим объектам среды CLR  
 При привязке данных к одному объекту CLR с тысячами свойств возникает значительное влияние на производительность. Это влияние можно уменьшить, разделив один объект на несколько объектов CLR с меньшим числом свойств. В таблице показана привязка и время отрисовки для привязки данных к одному крупному объекту CLR по сравнению с несколькими объектами меньшего размера.  
  
|**Привязка данных 1000 объектов TextBlock**|**Время привязки (мс)**|**Время отрисовки — включает привязку (мс)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|К объекту CLR с 1000 свойствами|950|1200|  
|Для 1000 объектов CLR с одним свойством|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Привязка к ItemsSource  
 Рассмотрим ситуацию, в которой имеется объект CLR <xref:System.Collections.Generic.List%601> , содержащий список сотрудников, которые необходимо отобразить <xref:System.Windows.Controls.ListBox>в. Чтобы создать соответствие между этими двумя объектами, необходимо привязать список сотрудников к <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> свойству <xref:System.Windows.Controls.ListBox>объекта. Предположим, что к группе присоединяется новый сотрудник. Вы можете подумать, что для вставки нового пользователя в привязанные <xref:System.Windows.Controls.ListBox> значения вы просто добавите этого пользователя в список сотрудников и предполагаю, что это изменение будет автоматически распознано механизмом привязки данных. Это предположение было бы ложным. в действительности изменение не будет <xref:System.Windows.Controls.ListBox> автоматически отражаться. Это обусловлено тем, <xref:System.Collections.Generic.List%601> что объект CLR не создает автоматически событие изменения коллекции. Чтобы получить объект <xref:System.Windows.Controls.ListBox> для получения изменений, необходимо заново создать список сотрудников и повторно присоединить его <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> к свойству <xref:System.Windows.Controls.ListBox>. Хотя это решение работает, оно серьезно влияет на производительность. Каждый раз при переназначении <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> в <xref:System.Windows.Controls.ListBox> новый объект <xref:System.Windows.Controls.ListBox> первый из них порождает предыдущие элементы и повторно создает весь список. Влияние на производительность будет увеличено, если <xref:System.Windows.Controls.ListBox> карта является сложной. <xref:System.Windows.DataTemplate>  
  
 Очень эффективным решением этой проблемы является составление списка <xref:System.Collections.ObjectModel.ObservableCollection%601>сотрудников. <xref:System.Collections.ObjectModel.ObservableCollection%601> Объект вызывает уведомление об изменении, которое может получить механизм привязки данных. Событие добавляет или удаляет элемент из объекта <xref:System.Windows.Controls.ItemsControl> без необходимости повторно создавать весь список.  
  
 В таблице ниже показано время, необходимое для обновления <xref:System.Windows.Controls.ListBox> (с отключенной виртуализацией пользовательского интерфейса) при добавлении одного элемента. Число в первой строке представляет время, затраченное на привязку объекта CLR <xref:System.Collections.Generic.List%601> к <xref:System.Windows.Controls.ListBox> элементу <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Число во второй строке представляет время <xref:System.Collections.ObjectModel.ObservableCollection%601> , затраченное <xref:System.Windows.Controls.ListBox> на привязку к элементу <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Обратите внимание на значительную экономию времени, используя <xref:System.Collections.ObjectModel.ObservableCollection%601> стратегию привязки данных.  
  
|**Привязка данных ItemsSource**|**Время обновления для 1 элемента (мс)**|  
|--------------------------------------|---------------------------------------|  
|В объект CLR <xref:System.Collections.Generic.List%601>|1656|  
|В объект<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Привязка IList к ItemsControl не IEnumerable  
 Если у вас есть выбор между привязкой <xref:System.Collections.Generic.IList%601> <xref:System.Collections.IEnumerable> или к <xref:System.Windows.Controls.ItemsControl> объекту, выберите <xref:System.Collections.Generic.IList%601> объект. Привязка <xref:System.Collections.IEnumerable> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] к вызову принудительно<xref:System.Collections.Generic.IList%601> создает объект-оболочку, что означает, что производительность затронет ненужные издержки второго объекта. <xref:System.Windows.Controls.ItemsControl>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Не преобразовывайте объекты среды CLR в XML только для привязки данных.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]позволяет привязывать данные к [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] содержимому, однако привязка данных к [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] содержимому выполняется медленнее, чем привязка данных к объектам CLR. Не преобразуйте данные объекта CLR в XML, если единственной целью является привязка данных.  
  
## <a name="see-also"></a>См. также

- [Улучшение производительности приложений WPF](optimizing-wpf-application-performance.md)
- [Планирование производительности приложения](planning-for-application-performance.md)
- [Использование преимуществ оборудования](optimizing-performance-taking-advantage-of-hardware.md)
- [Разметка и разработка](optimizing-performance-layout-and-design.md)
- [Двумерная графика и изображения](optimizing-performance-2d-graphics-and-imaging.md)
- [Поведение объекта](optimizing-performance-object-behavior.md)
- [Ресурсы приложений](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Дополнительные рекомендации по повышению производительности](optimizing-performance-other-recommendations.md)
- [Общие сведения о привязке данных](../data/data-binding-overview.md)
- [Пошаговое руководство: Кэширование данных приложения в приложении WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
