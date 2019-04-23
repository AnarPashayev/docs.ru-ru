---
title: Практическое руководство. Преобразование привязанных данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093804"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="e1361-102">Практическое руководство. Преобразование привязанных данных</span><span class="sxs-lookup"><span data-stu-id="e1361-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="e1361-103">В этом примере показано, как применить преобразования к данным, который используется в привязках.</span><span class="sxs-lookup"><span data-stu-id="e1361-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="e1361-104">Чтобы преобразовать данные во время привязки, необходимо создать класс, реализующий <xref:System.Windows.Data.IValueConverter> интерфейс, который включает в себя <xref:System.Windows.Data.IValueConverter.Convert%2A> и <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> методы.</span><span class="sxs-lookup"><span data-stu-id="e1361-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1361-105">Пример</span><span class="sxs-lookup"><span data-stu-id="e1361-105">Example</span></span>  
 <span data-ttu-id="e1361-106">В следующем примере показана реализация преобразователя, преобразующий значение даты, переданный так, чтобы отобразить только года, месяца и дня.</span><span class="sxs-lookup"><span data-stu-id="e1361-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="e1361-107">При реализации <xref:System.Windows.Data.IValueConverter> интерфейс, он является хорошей практикой для оформления для реализации с <xref:System.Windows.Data.ValueConversionAttribute> для указания того, для разработки средств типы данных, участвующие в преобразовании, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="e1361-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="e1361-108">После создания преобразователь, его можно добавить как ресурс в вашей [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] файл.</span><span class="sxs-lookup"><span data-stu-id="e1361-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="e1361-109">В следующем примере *src* соответствует пространству имен, в котором *DateConverter* определен.</span><span class="sxs-lookup"><span data-stu-id="e1361-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="e1361-110">Наконец можно использовать преобразователь в привязке, используя следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="e1361-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="e1361-111">В следующем примере текстовое содержимое <xref:System.Windows.Controls.TextBlock> привязан к *StartDate*, который является свойством из внешнего источника данных.</span><span class="sxs-lookup"><span data-stu-id="e1361-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="e1361-112">Ресурсы стиля, указанные в приведенном выше примере определяются в разделе ресурсов, не приведенные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="e1361-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1361-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e1361-113">See also</span></span>

- [<span data-ttu-id="e1361-114">Реализация проверки привязки</span><span class="sxs-lookup"><span data-stu-id="e1361-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="e1361-115">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="e1361-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e1361-116">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="e1361-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
