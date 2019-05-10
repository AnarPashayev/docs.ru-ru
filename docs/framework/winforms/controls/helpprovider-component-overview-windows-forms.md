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
ms.openlocfilehash: 9e8dc2ee2773b26a7bfef1da209399a8b49de9ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624121"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="8078a-102">Общие сведения о компоненте HelpProvider (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8078a-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="8078a-103">Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) компонент используется для связывания файл HTML Help 1.x справки (CHM-файл, созданный с помощью HTML Help Workshop, или HTM-файл) с приложением Windows.</span><span class="sxs-lookup"><span data-stu-id="8078a-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="8078a-104">Можно предоставить справку в различными способами:</span><span class="sxs-lookup"><span data-stu-id="8078a-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="8078a-105">Укажите контекстной справки для элементов управления в формах Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8078a-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="8078a-106">Предоставить контекстную справку для определенного диалогового или конкретных элементов управления в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="8078a-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="8078a-107">Откройте файл справки для конкретной области, например на главной странице оглавление, индекс или функция поиска.</span><span class="sxs-lookup"><span data-stu-id="8078a-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="8078a-108">С помощью поставщика по справке</span><span class="sxs-lookup"><span data-stu-id="8078a-108">Using the Help Provider</span></span>  
 <span data-ttu-id="8078a-109">Добавление <xref:System.Windows.Forms.HelpProvider> компонента в форму Windows позволяет других элементов управления в форме для предоставления справки свойства <xref:System.Windows.Forms.HelpProvider> компонента.</span><span class="sxs-lookup"><span data-stu-id="8078a-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="8078a-110">Это позволяет предоставить справку для элементов управления в форме Windows.</span><span class="sxs-lookup"><span data-stu-id="8078a-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="8078a-111">Можно связать файл справки с <xref:System.Windows.Forms.HelpProvider> компонента с помощью <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="8078a-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="8078a-112">Укажите тип справки, получен с помощью вызова <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> и указав значение от <xref:System.Windows.Forms.HelpNavigator> перечисления для указанного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="8078a-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="8078a-113">Укажите ключевое слово или раздел для справки, вызвав <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="8078a-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="8078a-114">При необходимости, чтобы связать определенную строку справки с другим элементом управления, используйте <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="8078a-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="8078a-115">Строка, которая будет связана с элементом управления, с помощью этого метода отображается во всплывающем окне, когда пользователь нажимает клавишу F1, элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="8078a-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="8078a-116">Если <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> не был задан, необходимо использовать <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> для предоставления текста справки.</span><span class="sxs-lookup"><span data-stu-id="8078a-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="8078a-117">Если вы настроили оба <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> и строку справки на основе справки <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> будет иметь приоритет.</span><span class="sxs-lookup"><span data-stu-id="8078a-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8078a-118">Могут возникать проблемы, с помощью относительного пути, при задании пути к файлу справки, в <xref:System.Windows.Forms.Help.ShowHelp%2A> метод или <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> свойство <xref:System.Windows.Forms.HelpProvider> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="8078a-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="8078a-119">Таким образом не забудьте указать абсолютный путь к файлу справки.</span><span class="sxs-lookup"><span data-stu-id="8078a-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8078a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="8078a-120">See also</span></span>

- [<span data-ttu-id="8078a-121">Справочные системы в приложениях Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8078a-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
