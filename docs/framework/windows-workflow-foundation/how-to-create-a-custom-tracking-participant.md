---
title: Практическое руководство. Создание настраиваемого участника отслеживания
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 280f68c8b762562a56ce96f45f118702fb0e4d76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962402"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="9dd5e-102">Практическое руководство. Создание настраиваемого участника отслеживания</span><span class="sxs-lookup"><span data-stu-id="9dd5e-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="9dd5e-103">Отслеживание рабочих процессов обеспечивает видимость состояния выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="9dd5e-104">Среда выполнения рабочего процесса отправляет записи отслеживания, описывающие события жизненного цикла рабочего процесса, события жизненного цикла действия, возобновления закладок и сбои.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="9dd5e-105">Эти записи отслеживания используются участниками отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="9dd5e-106">Windows Workflow Foundation (WF) включает стандартный участник отслеживания, который записывает записи отслеживания в качестве события трассировки событий Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="9dd5e-107">Если это не отвечает заданным требованиям, то можно создать своего собственного участника отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="9dd5e-108">На этом шаге учебника описывается, как создать настраиваемого участника отслеживания и профиль отслеживания, которые захватывают выходные данные действий `WriteLine`, чтобы их можно было показать пользователю.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dd5e-109">Каждый раздел в учебнике «Приступая к работе» построен на основе предыдущих разделов.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="9dd5e-110">Для изучения этого раздела необходимо сначала пройти предыдущие шаги.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="9dd5e-111">Чтобы скачать готовую версию или просмотреть видео пошаговое руководство, см. Руководство по [Windows Workflow Foundation (WF45) — Начало работы](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="9dd5e-112">Создание пользовательского участника отслеживания</span><span class="sxs-lookup"><span data-stu-id="9dd5e-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="9dd5e-113">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите **добавить**, **класс**.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="9dd5e-114">Введите `StatusTrackingParticipant` в поле **имя** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="9dd5e-115">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="9dd5e-116">Измените класс `StatusTrackingParticipant` таким образом, чтобы он наследовался от класса `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="9dd5e-117">Добавьте следующее переопределение метода `Track`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-117">Add the following `Track` method override.</span></span> <span data-ttu-id="9dd5e-118">Существует несколько различных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-118">There are several different types of tracking records.</span></span> <span data-ttu-id="9dd5e-119">Нас интересуют только выходные данные действий `WriteLine`, которые содержатся в записях отслеживания действий.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="9dd5e-120">Если `TrackingRecord` является `ActivityTrackingRecord` для действия `WriteLine`, `Text` действия `WriteLine` добавляется в файл после `InstanceId` рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="9dd5e-121">В этом руководстве файл сохраняется в текущей папке ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="9dd5e-122">Если профиль отслеживания не указан, используется профиль по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="9dd5e-123">Если используется профиль отслеживания по умолчанию, записи отслеживания создаются для всех `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="9dd5e-124">Поскольку нам нужно получить текст только один раз в течение жизненного цикла действия `WriteLine`, мы извлекаем текст только из состояния `ActivityStates.Executing`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="9dd5e-125">В [для создания профиля отслеживания и регистрации участника отслеживания](#to-create-the-tracking-profile-and-register-the-tracking-participant)создается профиль отслеживания, который указывает, что создаются только `WriteLine` `ActivityStates.Executing` записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="9dd5e-126">Создание профиля отслеживания и регистрация участника отслеживания</span><span class="sxs-lookup"><span data-stu-id="9dd5e-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="9dd5e-127">Щелкните правой кнопкой мыши **воркфловхостформ** в **Обозреватель решений** и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="9dd5e-128">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="9dd5e-129">Добавьте следующий код в `ConfigureWorkflowApplication` сразу после кода, добавляющего `StringWriter` к расширениям рабочего процесса, и перед обработчиками жизненного цикла рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="9dd5e-130">Этот профиль отслеживания указывает, что только записи состояния действий `WriteLine` в состоянии `Executing` отправляются пользовательскому участнику отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="9dd5e-131">После добавления кода запуск `ConfigureWorkflowApplication` будет выглядеть так, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="9dd5e-132">Отображение сведений об отслеживании</span><span class="sxs-lookup"><span data-stu-id="9dd5e-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="9dd5e-133">Щелкните правой кнопкой мыши **воркфловхостформ** в **Обозреватель решений** и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="9dd5e-134">В обработчике `InstanceId_SelectedIndexChanged` добавьте следующий код сразу после кода очистки окна состояния.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="9dd5e-135">Если новый рабочий процесс выбран в списке рабочих процессов, записи отслеживания для этого рабочего процесса загружаются и отображаются в окне состояния.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="9dd5e-136">Ниже приведен полный пример обработчика `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="9dd5e-137">Сборка и запуск приложения</span><span class="sxs-lookup"><span data-stu-id="9dd5e-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="9dd5e-138">Нажмите клавиши Ctrl+Shift+B, чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="9dd5e-139">Нажмите клавиши Ctrl+F5, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="9dd5e-140">Выберите диапазон для игры подбора и тип рабочего процесса, который нужно запустить, и щелкните **Новая игра**.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="9dd5e-141">Введите предположение в поле **предположение** и нажмите кнопку **Перейти** , чтобы отправить свое предположение.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="9dd5e-142">Обратите внимание, что состояние рабочего процесса отображается в окне состояния.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="9dd5e-143">Этот результат получен из действий `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="9dd5e-144">Переключитесь на другой рабочий процесс, выбрав его в поле со списком **идентификатор экземпляра рабочего процесса** , и обратите внимание, что состояние текущего рабочего процесса удалено.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="9dd5e-145">Переключитесь на предыдущий рабочий процесс и отметьте, что состояние восстановлено, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9dd5e-146">Если перейти к рабочему процессу, который был запущен до включения отслеживания, состояние не отображается.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="9dd5e-147">Но если вы вводите дополнительные предположения, их состояние сохраняется, поскольку теперь отслеживание включено.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="9dd5e-148">Эти сведения полезны для определения диапазона случайного числа, но они не содержат никаких данных о предыдущих предположениях.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="9dd5e-149">Эти сведения находятся на следующем шаге [: Разместите несколько версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="9dd5e-150">Запишите идентификатор экземпляра рабочего процесса и доведите игру до конца.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="9dd5e-151">Откройте проводник Windows и перейдите в папку **нумбергуессворкфловхост\бин\дебуг** (или **Bin\Release** в зависимости от параметров проекта).</span><span class="sxs-lookup"><span data-stu-id="9dd5e-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="9dd5e-152">Обратите внимание, что в дополнение к исполняемым файлам проекта существуют файлы с именами с идентификатором GUID.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="9dd5e-153">Определите файл, который соответствует идентификатору экземпляра рабочего процесса, завершенного на предыдущем шаге, и откройте его в Блокноте.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="9dd5e-154">Данные отслеживания содержат информацию, подобную следующим данным.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="9dd5e-155">В дополнение к отсутствию догадок пользователя эти данные отслеживания не содержат сведения о последнем предположении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="9dd5e-156">Это происходит потому, что данные отслеживания состоят только из выходных данных `WriteLine` рабочего процесса, а последнее отображаемое сообщение выдается из обработчика `Completed` после завершения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="9dd5e-157">На следующем этапе работы с руководством [выполните следующие действия. Разместите несколько версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), существующие `WriteLine` действия будут изменены, чтобы отобразить предположения пользователя, и добавлено дополнительное `WriteLine` действие, которое отображает окончательные результаты.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="9dd5e-158">После интеграции [этих изменений можно: Размещение нескольких версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) показывает, как разместить несколько версий рабочего процесса в одно и то же время.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
