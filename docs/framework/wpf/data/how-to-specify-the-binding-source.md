---
title: Практическое руководство. Указание источника привязки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 418dc77ce7638698d4850b06dafcea57787e1015
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959703"
---
# <a name="how-to-specify-the-binding-source"></a>Практическое руководство. Указание источника привязки
В привязке данных объект источника привязки означает объект, из которого вы получаете данные. В этом разделе описываются различные способы указания источника привязки.  
  
## <a name="example"></a>Пример  
 При привязке нескольких свойств к общему источнику вы хотите использовать свойство `DataContext`, которое предоставляет удобный способ для установления области применения, внутри которой все свойства с привязкой к данным наследуют общий источник.  
  
 В следующем примере контекст данных устанавливается для корневого элемента приложения. Это позволяет всем дочерним элементам наследовать этот контекст данных. Данные для привязки поступают из настраиваемого класса данных `NetIncome`, ссылка на который устанавливается напрямую через сопоставления и которому присвоен ключ ресурса `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 В следующем примере показано определение класса `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> Приведенный выше пример создает экземпляр объекта в разметке и использует его в качестве ресурса. Если вы хотите выполнить привязку к объекту, экземпляр которого уже создан в коде, необходимо задать свойство `DataContext` программным способом. Пример см. в разделе [Обеспечение доступности данных для привязки в XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Кроме того, если вы хотите указать источник в отдельных привязках явным образом, доступны следующие варианты. Они имеют приоритет над наследуемым контекстом данных.  
  
|Свойство.|Описание|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Это свойство используется для задания экземпляра объекта в качестве источника. Если не требуется функциональность установки области, в которой несколько свойств наследуют один и тот же контекст данных, можно использовать <xref:System.Windows.Data.Binding.Source%2A> свойство вместо `DataContext` свойства. Дополнительные сведения см. в разделе <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Это полезно, когда требуется указать источник относительно того, где расположен целевой объект привязки. Это свойство можно использовать в некоторых типичных сценариях, например, если вы хотите выполнить привязку одного свойства элемента к другому свойству этого же элемента или при определении привязки в стиле или шаблоне. Дополнительные сведения см. в разделе <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Укажите строку, представляющую элемент, к которому требуется привязать. Это полезно, когда требуется выполнить привязку к свойству другого элемента в вашем приложении. Например, <xref:System.Windows.Controls.Slider> если вы хотите использовать для управления высотой другого элемента управления в приложении или если вы хотите <xref:System.Windows.Controls.ContentControl.Content%2A> привязать элемент управления <xref:System.Windows.Controls.ListBox> к <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> свойству элемента управления. Дополнительные сведения см. в разделе <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Наследование значения свойства](../advanced/property-value-inheritance.md)
- [Общие сведения о привязке данных](data-binding-overview.md)
- [Общие сведения об объявлении привязок](binding-declarations-overview.md)
- [Разделы практического руководства](data-binding-how-to-topics.md)
