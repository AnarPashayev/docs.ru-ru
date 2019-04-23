---
title: Практическое руководство. Реализация уведомления об изменении свойства
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204358"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="3cdea-102">Практическое руководство. Реализация уведомления об изменении свойства</span><span class="sxs-lookup"><span data-stu-id="3cdea-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="3cdea-103">Для поддержки <xref:System.Windows.Data.BindingMode.OneWay> или <xref:System.Windows.Data.BindingMode.TwoWay> привязки для включения свойства целевого объекта привязки автоматическое отражение динамических изменений источника привязки (например, область просмотра обновляется автоматически, когда пользователь редактирует форму), класс необходимо предоставлять уведомления соответствующие изменения свойства.</span><span class="sxs-lookup"><span data-stu-id="3cdea-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="3cdea-104">В этом примере показано, как создать класс, реализующий <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="3cdea-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cdea-105">Пример</span><span class="sxs-lookup"><span data-stu-id="3cdea-105">Example</span></span>  
 <span data-ttu-id="3cdea-106">Для реализации <xref:System.ComponentModel.INotifyPropertyChanged> необходимо объявить <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> событий и создайте `OnPropertyChanged` метод.</span><span class="sxs-lookup"><span data-stu-id="3cdea-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="3cdea-107">Затем для каждого свойства, которому потребуются уведомления об изменениях, вы вызываете `OnPropertyChanged` при каждом обновлении свойства.</span><span class="sxs-lookup"><span data-stu-id="3cdea-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="3cdea-108">Пример того, как `Person` класс может использоваться для поддержки <xref:System.Windows.Data.BindingMode.TwoWay> привязки, см. в разделе [Управление обновлением источника текст в текстовом поле](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="3cdea-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdea-109">См. также</span><span class="sxs-lookup"><span data-stu-id="3cdea-109">See also</span></span>

- [<span data-ttu-id="3cdea-110">Общие сведения об источниках привязки</span><span class="sxs-lookup"><span data-stu-id="3cdea-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="3cdea-111">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="3cdea-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3cdea-112">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="3cdea-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
