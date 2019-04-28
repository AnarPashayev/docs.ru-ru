---
title: Практическое руководство. Вызов диалогового окна печати
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 2ced508eb83e2955fdcd1ad87fb6415e2052446f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757162"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="3c1ad-102">Практическое руководство. Вызов диалогового окна печати</span><span class="sxs-lookup"><span data-stu-id="3c1ad-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="3c1ad-103">Чтобы обеспечить возможность печати из приложения, вы можете создать и открыть <xref:System.Windows.Controls.PrintDialog> объекта.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1ad-104">Пример</span><span class="sxs-lookup"><span data-stu-id="3c1ad-104">Example</span></span>  
 <span data-ttu-id="3c1ad-105">Элемент управления <xref:System.Windows.Controls.PrintDialog> предоставляет единую точку входа для [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], конфигурации и отправки задания [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c1ad-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="3c1ad-106">Элемент управления является простой в использовании и может быть создан с помощью [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] разметки или кода.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="3c1ad-107">Ниже приведен пример, как создать и открыть элемент управления в коде и способ печати из него.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="3c1ad-108">Также показано, как убедиться, что диалоговое окно предоставит пользователям возможность установки конкретного диапазона страниц.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="3c1ad-109">В примере кода предполагается, что имеется файл FixedDocumentSequence.xps в корне диска C:.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="3c1ad-110">Когда откроется диалоговое окно, пользователи будут доступны для выбора принтеров, установленных на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="3c1ad-111">Они также получат возможность выбрать [средство записи документов XPS Microsoft](https://go.microsoft.com/fwlink/?LinkId=147319) для создания [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] файла вместо печати.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c1ad-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Управления [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], как описано в этом разделе, не следует путать с <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> компонент Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="3c1ad-113">Строго говоря, можно использовать <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> метода, не открывая диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="3c1ad-114">В этом смысле элемент управления может использоваться как невидимого компонента печати.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="3c1ad-115">Но из соображений производительности было бы лучше использовать <xref:System.Printing.PrintQueue.AddJob%2A> метода или один из многих <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> и <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> методы <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="3c1ad-116">Дополнительные сведения об этом см. в разделе [печатать файлы XPS программным способом](how-to-programmatically-print-xps-files.md) и.</span><span class="sxs-lookup"><span data-stu-id="3c1ad-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1ad-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3c1ad-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="3c1ad-118">Документы в WPF</span><span class="sxs-lookup"><span data-stu-id="3c1ad-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="3c1ad-119">Общие сведения о печати</span><span class="sxs-lookup"><span data-stu-id="3c1ad-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="3c1ad-120">Средство записи документов Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="3c1ad-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
