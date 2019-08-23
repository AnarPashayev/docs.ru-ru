---
title: Общие сведения о компоненте HelpProvider (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965696"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="f707a-102">Общие сведения о компоненте HelpProvider (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f707a-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f707a-103">Компонент Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) используется для связывания файла справки HTML Help 1. x (либо файла. chm, созданного с помощью справки HTML или файла. htm) с приложением Windows.</span><span class="sxs-lookup"><span data-stu-id="f707a-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="f707a-104">Получить справку можно различными способами:</span><span class="sxs-lookup"><span data-stu-id="f707a-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="f707a-105">Предоставьте контекстную справку для элементов управления на Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f707a-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="f707a-106">Предоставить контекстную справку по конкретному диалоговому окну или определенным элементам управления в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="f707a-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="f707a-107">Открытие файла справки для конкретных областей, например главной страницы оглавления, индекса или функции поиска.</span><span class="sxs-lookup"><span data-stu-id="f707a-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="f707a-108">Использование поставщика справки</span><span class="sxs-lookup"><span data-stu-id="f707a-108">Using the Help Provider</span></span>  
 <span data-ttu-id="f707a-109">Добавление компонента в форму Windows позволяет другим элементам управления формы предоставлять свойства <xref:System.Windows.Forms.HelpProvider> справки компонента. <xref:System.Windows.Forms.HelpProvider></span><span class="sxs-lookup"><span data-stu-id="f707a-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="f707a-110">Это позволяет предоставить справку для элементов управления в форме Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f707a-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="f707a-111">Файл справки можно связать с <xref:System.Windows.Forms.HelpProvider> компонентом <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> с помощью свойства.</span><span class="sxs-lookup"><span data-stu-id="f707a-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="f707a-112">Вы указываете тип справки, предоставляемый вызовом <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> , и предоставляя значение <xref:System.Windows.Forms.HelpNavigator> из перечисления для указанного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="f707a-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="f707a-113">Вы предоставляете ключевое слово или раздел для справки, <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> вызывая метод.</span><span class="sxs-lookup"><span data-stu-id="f707a-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="f707a-114">Кроме того, чтобы связать определенную строку справки с другим элементом управления, используйте <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="f707a-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="f707a-115">Строка, связываемая с элементом управления с помощью этого метода, отображается во всплывающем окне, когда пользователь нажимает клавишу F1, когда элемент управления находится в фокусе.</span><span class="sxs-lookup"><span data-stu-id="f707a-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="f707a-116">Если <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> параметр не задан, необходимо использовать <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> для предоставления текста справки.</span><span class="sxs-lookup"><span data-stu-id="f707a-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="f707a-117">Если заданы <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> и, и строка справки, то Справка, основанная на <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> , будет иметь приоритет.</span><span class="sxs-lookup"><span data-stu-id="f707a-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f707a-118">При указании пути к файлу справки в <xref:System.Windows.Forms.Help.ShowHelp%2A> методе или <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> свойстве <xref:System.Windows.Forms.HelpProvider> элемента управления могут возникнуть проблемы с использованием относительного пути.</span><span class="sxs-lookup"><span data-stu-id="f707a-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="f707a-119">Поэтому для указания файла справки следует использовать абсолютный путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="f707a-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f707a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f707a-120">See also</span></span>

- [<span data-ttu-id="f707a-121">Справочные системы в приложениях Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f707a-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
