---
title: Задача 1. Создание нового приложения Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 63b84e4fd2c88d98fbf417ee1f55ec203d295116
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320384"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="0aaaa-102">Задача 1. Создание нового приложения Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="0aaaa-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="0aaaa-103">В этой задаче будет создать пустое приложение Windows Presentation Foundation (WPF), используя шаблон WPF Application Visual Studio и добавьте ссылки на соответствующие [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] сборки рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="0aaaa-104">Создание проекта приложения WPF</span><span class="sxs-lookup"><span data-stu-id="0aaaa-104">To create the WPF Application project</span></span>  
  
1. <span data-ttu-id="0aaaa-105">Откройте Visual Studio и на **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **проекта**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="0aaaa-106">В **новый проект** диалогового окна выберите либо **Visual C#**  или **Visual Basic** из **установленные шаблоны** в левую панель части поля.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="0aaaa-107">Если язык не отображается, найдите его в разделе **другие языки**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3. <span data-ttu-id="0aaaa-108">Выберите **Windows** в **установленные шаблоны** области.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4. <span data-ttu-id="0aaaa-109">Убедитесь, что в верхней области (значение по умолчанию) **.NET Framework 4** была в поле с раскрывающимся списком, а затем выберите **приложение WPF**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5. <span data-ttu-id="0aaaa-110">Задайте имя проекта, который **HostingApplication** в нижней части окна.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6. <span data-ttu-id="0aaaa-111">Задайте имя решения **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7. <span data-ttu-id="0aaaa-112">Нажмите кнопку **ОК** Создание проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="0aaaa-113">Visual Studio создает основной пользовательский Интерфейс WPF для приложения и включает в себя соответствующий XAML и файлы с выделенным кодом.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8. <span data-ttu-id="0aaaa-114">Добавьте ссылки на **WorkflowModel** сборки.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="0aaaa-115">Для этого в **обозревателе решений**, щелкните правой кнопкой мыши **HostingApplication** проекта и выберите **добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="0aaaa-116">В **добавить ссылку** диалоговом окне щелкните **.NET** вкладке, удерживая нажатой клавишу CTRL, выберите следующие сборки и нажмите кнопку **ОК**:</span><span class="sxs-lookup"><span data-stu-id="0aaaa-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="0aaaa-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="0aaaa-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="0aaaa-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="0aaaa-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="0aaaa-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="0aaaa-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="0aaaa-120">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="0aaaa-121">См. в разделе [задача 2: Размещение конструктора рабочих процессов](task-2-host-the-workflow-designer.md) Дополнительные сведения о размещении визуальной разработки конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="0aaaa-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aaaa-122">См. также</span><span class="sxs-lookup"><span data-stu-id="0aaaa-122">See also</span></span>

- [<span data-ttu-id="0aaaa-123">Повторное размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="0aaaa-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="0aaaa-124">Задача 2. Размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="0aaaa-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
