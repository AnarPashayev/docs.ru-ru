---
title: Практическое руководство. Создание и запуск длительного рабочего процесса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 7940d1d8869d3b82c1aa19cb038a68b8724345dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320056"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Практическое руководство. Создание и запуск длительного рабочего процесса
Одна из функций центра Windows Workflow Foundation (WF) предоставляет возможность среды выполнения сохранения и выгрузки бездействующих рабочих процессов в базе данных. Действия, описанные в [как: Запуск рабочего процесса](how-to-run-a-workflow.md) показаны основы размещение рабочих процессов, используя консольное приложение. Приведены примеры запуска рабочих процессов, обработчиков жизненного цикла рабочего процесса и возобновления закладок. Для эффективной демонстрации сохранения рабочего процесса требуется более сложный узел рабочих процессов, обеспечивающий запуск и возобновление нескольких экземпляров рабочего процесса. На этом шаге учебника показано, как создать ведущее приложение форм Windows Form, которое обеспечивает запуск и возобновление нескольких экземпляров рабочих процессов, сохранение рабочего процесса и основу для таких дополнительных возможностей, как отслеживание версий, которые показаны в последующих шагах учебника, и управление ими.  
  
> [!NOTE]
>  Этот шаг руководства и последующие шаги использовать все три типа рабочего процесса из [как: Создание рабочего процесса](how-to-create-a-workflow.md). Если вы не прошли все три типа можно загрузить полную версию из учебника [Windows Workflow Foundation (WF45) - Приступая к работе](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Чтобы скачать полную версию или просмотреть пошаговое видео учебника, см. в разделе [Windows Workflow Foundation (WF45) - Приступая к работе](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Содержание раздела  
  
-   [Создание базы данных сохраняемости](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Добавление ссылки в сборки DurableInstancing](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Создание ведущей формы рабочего процесса](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Добавление свойств и вспомогательных методов формы](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Настройка хранилища экземпляров, обработчиков жизненного цикла рабочего процесса и расширений](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Разрешение запуска и возобновления нескольких типов рабочих процессов](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Запуск нового рабочего процесса](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Возобновление рабочего процесса](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Завершение рабочего процесса](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Сборка и запуск приложения](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
### <a name="BKMK_CreatePersistenceDatabase"></a> Чтобы создать базу данных сохраняемости  
  
1. Откройте SQL Server Management Studio и подключитесь к локальному серверу, например **. \SQLEXPRESS**. Щелкните правой кнопкой мыши **баз данных** узла на локальном сервере, а затем выберите **новую базу данных**. Присвойте имя новой базы данных **WF45GettingStartedTutorial**, примите все остальные значения, а затем выберите **ОК**.  
  
    > [!NOTE]
    >  Убедитесь, что у вас есть **Create Database** разрешение на локальном сервере, перед созданием базы данных.  
  
2. Выберите **откройте**, **файл** из **файл** меню. Перейдите в следующую папку: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     Выберите следующие два файла и нажмите кнопку **откройте**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3. Выберите **SqlWorkflowInstanceStoreSchema.sql** из **окно** меню. Убедитесь, что **WF45GettingStartedTutorial** выбран в **доступных баз данных** раскрывающегося списка и выберите **Execute** из **запроса**меню.  
  
4. Выберите **SqlWorkflowInstanceStoreLogic.sql** из **окно** меню. Убедитесь, что **WF45GettingStartedTutorial** выбран в **доступных баз данных** раскрывающегося списка и выберите **Execute** из **запроса**меню.  
  
    > [!WARNING]
    >  Важно выполнить предыдущие два шага в правильном порядке. Если выполнить запросы в неправильном порядке, произойдет ошибка и база данных сохраняемости не будет правильно настроена.  
  
### <a name="BKMK_AddReference"></a> Для добавления ссылки на сборки DurableInstancing  
  
1. Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **обозревателе решений** и выберите **добавить ссылку**.  
  
2. Выберите **сборки** из **добавить ссылку** списка и введите `DurableInstancing` в **поиск сборок** поле. Сборки отфильтруются, и будет легче выбрать необходимые ссылки.  
  
3. Установите флажок рядом с **System.Activities.DurableInstancing** и **System.Runtime.DurableInstancing** из **результаты поиска** , а нажмите **ОК**.  
  
### <a name="BKMK_CreateForm"></a> Создание ведущей формы рабочего процесса  
  
> [!NOTE]
>  В шагах этой процедуры показано, как добавить и настроить форму вручную. При необходимости можно загрузить файлы решений для учебника и добавить готовую форму в проект. Чтобы скачать файлы учебника, см. в разделе [Windows Workflow Foundation (WF45) - Приступая к работе](https://go.microsoft.com/fwlink/?LinkID=248976). После загрузки файлов, щелкните правой кнопкой мыши **NumberGuessWorkflowHost** и выберите **добавить ссылку**. Добавьте ссылку на **System.Windows.Forms** и **System.Drawing**. Эти ссылки добавляются автоматически при добавлении новой формы из **добавить**, **новый элемент** меню, но необходимо добавить вручную при импорте формы. После добавления ссылок щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **обозревателе решений** и выберите **добавить**, **существующий элемент**. Перейдите к `Form` папке в файлах проекта, выберите **WorkflowHostForm.cs** (или **WorkflowHostForm.vb**) и нажмите кнопку **добавить**. Если вы решили импортировать форму, а затем переходите к следующему разделу, [для добавления свойств и вспомогательных методов формы](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1. Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **обозревателе решений** и выберите **добавить**, **новый элемент**.  
  
2. В **установленные** шаблонов выберите **формы Windows**, тип `WorkflowHostForm` в **имя** и нажмите кнопку **добавить**.  
  
3. Задайте следующие свойства формы.  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Размер|400, 420|  
  
4. Добавьте в форму следующие элементы управления в указанном порядке и задайте значения свойств.  
  
    |Элемент управления|Свойство: Значение|  
    |-------------|---------------------|  
    |**Кнопка**|Имя. NewGame<br /><br /> Расположение: 13, 13<br /><br /> Размер: 75, 23<br /><br /> Text: Новая игра|  
    |**Метка**|Расположение: 94, 18<br /><br /> Text: Угадайте число от 1 до|  
    |**ComboBox**|Имя. NumberRange<br /><br /> Значением DropDownStyle: DropDownList<br /><br /> Элементы: 10, 100, 1000<br /><br /> Расположение: 228, 12<br /><br /> Размер: 143, 21|  
    |**Метка**|Расположение: 13, 43<br /><br /> Text: Тип рабочего процесса|  
    |**ComboBox**|Имя. WorkflowType<br /><br /> Значением DropDownStyle: DropDownList<br /><br /> Элементы: StateMachineNumberGuessWorkflow FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Расположение: 94, 40<br /><br /> Размер: 277, 21|  
    |**Метка**|Имя. WorkflowVersion<br /><br /> Расположение: 13, 362<br /><br /> Text: Версия рабочего процесса|  
    |**GroupBox**|Расположение: 13, 67<br /><br /> Размер: 358, 287<br /><br /> Text: Игра|  
  
    > [!NOTE]
    >  При добавлении следующих элементов управления, их следует поместите в GroupBox.  
  
    |Элемент управления|Свойство: Значение|  
    |-------------|---------------------|  
    |**Метка**|Расположение: 7, 20<br /><br /> Text: Идентификатор экземпляра рабочего процесса|  
    |**ComboBox**|Имя. InstanceId<br /><br /> Значением DropDownStyle: DropDownList<br /><br /> Расположение: 121, 17<br /><br /> Размер: 227, 21|  
    |**Метка**|Расположение: 7, 47<br /><br /> Text: Догадка|  
    |**TextBox**|Имя. Догадка<br /><br /> Расположение: 50, 44<br /><br /> Размер: 65, 20|  
    |**Кнопка**|Имя. EnterGuess<br /><br /> Расположение: 121, 42<br /><br /> Размер: 75, 23<br /><br /> Text: Ввести догадку|  
    |**Кнопка**|Имя. QuitGame<br /><br /> Расположение: 274, 42<br /><br /> Размер: 75, 23<br /><br /> Text: Выход|  
    |**TextBox**|Имя. WorkflowStatus<br /><br /> Расположение: 10, 73<br /><br /> Многострочный: True<br /><br /> Только для чтения: True<br /><br /> Полосы прокрутки: Вертикально<br /><br /> Размер: 338, 208|  
  
5. Задайте **AcceptButton** свойства формы **EnterGuess**.  
  
 В следующем примере показана заполненная форма.  
  
 ![WF45 Приступая к работе ведущей формы рабочего процесса учебника](./media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
### <a name="BKMK_AddHelperMethods"></a> Для добавления свойств и вспомогательных методов формы  
 В этом разделе показано, как добавить в класс формы свойства и вспомогательные методы, которые настраивают пользовательский интерфейс формы для запуска и возобновления рабочих процессов угадывания числа.  
  
1. Щелкните правой кнопкой мыши **WorkflowHostForm** в **обозревателе решений** и выберите **Просмотр кода**.  
  
2. Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3. Добавьте следующие объявления элементов в **WorkflowHostForm** класса.  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  Если у вас другая строка подключения, обновите строку `connectionString` так, чтобы она указывала на вашу базу данных.  
  
4. Добавьте свойство `WorkflowInstanceId` в класс `WorkflowFormHost`.  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     `InstanceId` Поле со списком отображает список идентификаторов экземпляра сохраненного рабочего процесса и `WorkflowInstanceId` свойство возвращает текущий выбранный рабочий процесс.  
  
5. Добавьте обработчик события `Load` формы. Чтобы добавить обработчик, перейдите в **конструкторе** формы, щелкните **события** значок в верхней части **свойства** окна и дважды щелкните **нагрузки**.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6. Добавьте следующий код к `WorkflowHostForm_Load`.  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     Когда форма загружена, настраивается класс `SqlWorkflowInstanceStore`, для полей со списком диапазонов и типов рабочего процесса устанавливаются значения по умолчанию, а сохраненные экземпляры рабочих процессов добавляются в поле `InstanceId`.  
  
7. Добавьте обработчик событий `SelectedIndexChanged` для `InstanceId`. Чтобы добавить обработчик, перейдите в **конструкторе** формы, выберите `InstanceId` поле со списком, нажмите кнопку **события** значок в верхней части **свойства** окно, и Дважды щелкните **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8. Добавьте следующий код к `InstanceId_SelectedIndexChanged`. Каждый раз, когда пользователь выбирает рабочий процесс с помощью поля со списком, этот обработчик обновляет окно состояния.  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
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
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
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
    ```  
  
9. Добавьте следующий метод `ListPersistedWorkflows` в класс формы.  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows` запрашивает хранилища экземпляров сохраненные экземпляры рабочих процессов и добавляет идентификаторы экземпляров для `cboInstanceId` поле со списком.  
  
10. Добавьте следующий метод `UpdateStatus` и соответствующий делегат в класс формы. Этот метод обновляет окно состояния в форме с данными о состоянии рабочего процесса, выполняемого в данный момент.  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. Добавьте следующий метод `GameOver` и соответствующий делегат в класс формы. После завершения рабочего процесса, этот метод обновляет пользовательский Интерфейс формы, удаляя идентификатор экземпляра завершенного рабочего процесса из **InstanceId** поле со списком.  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
### <a name="BKMK_ConfigureWorkflowApplication"></a> Чтобы настроить хранилище экземпляров, обработчиков жизненного цикла рабочего процесса и расширения  
  
1. Добавьте метод `ConfigureWorkflowApplication` в класс формы.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Этот метод задает `WorkflowApplication`, добавляет необходимые расширения и обработчики событий жизненного цикла рабочего процесса.  
  
2. В `ConfigureWorkflowApplication` укажите `SqlWorkflowInstanceStore` для `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3. Затем создайте экземпляр класса `StringWriter` и добавьте его в коллекцию `Extensions` приложения `WorkflowApplication`. Когда `StringWriter` добавляется к расширениям, он записывает все `WriteLine` выходные данные действия. Когда рабочий процесс становится неактивным, выходные данные `WriteLine` можно извлечь из `StringWriter` и показать на форме.  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4. Добавьте следующий обработчик события `Completed`. После успешного завершения рабочего процесса число ходов, которое потребовалось для угадывания числа, отображается в окне состояния. Если рабочий процесс завершается, выдаются сведения об исключении, которое явилось причиной. В конце обработчика вызывается метод `GameOver`, который удаляет завершенный рабочий процесс из списка рабочих процессов.  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5. Добавьте следующие обработчики `Aborted` и `OnUnhandledException`. Метод `GameOver` не вызывается из обработчика `Aborted`, поскольку в случае аварийного завершения выполнения экземпляра рабочего процесса работа экземпляра не прекращается окончательно, позже можно перезапустить экземпляр.  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6. Добавьте следующий обработчик `PersistableIdle`. Этот обработчик получает расширение `StringWriter`, которое было добавлено, извлекает данные из действий `WriteLine` и отображает их в окне состояния.  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     Для перечисления <xref:System.Activities.PersistableIdleAction> существует три значения: <xref:System.Activities.PersistableIdleAction.None>,<xref:System.Activities.PersistableIdleAction.Persist> и <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> Вызывает сохранение рабочего процесса, но не приводит к выгрузке рабочего процесса. <xref:System.Activities.PersistableIdleAction.Unload> Вызывает сохранение и выгрузку рабочего процесса.  
  
     Ниже приведен полный пример метода `ConfigureWorkflowApplication`.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
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
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
### <a name="BKMK_WorkflowVersionMap"></a> Чтобы включить запуск и возобновление нескольких типов рабочих процессов  
 Чтобы возобновить экземпляр рабочего процесса, ведущее приложение должно предоставить определение рабочего процесса. В этом учебнике описано 3 типа рабочих процессов и далее предоставлено несколько версий этих типов. `WorkflowIdentity` Позволяет ведущему приложению связать идентификационные данные с помощью сохраненного экземпляра рабочего процесса. В этом разделе показано, как создать служебный класс, который поможет сопоставить идентификационные данные из сохраненного экземпляра рабочего процесса с соответствующим определением рабочего процесса. Дополнительные сведения о `WorkflowIdentity` и управления версиями, см. в разделе [с помощью WorkflowIdentity и управления версиями](using-workflowidentity-and-versioning.md).  
  
1. Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **обозревателе решений** и выберите **добавить**, **класс**. Тип `WorkflowVersionMap` в **имя** поле и нажмите кнопку **добавить**.  
  
2. Добавьте следующие инструкции `using` или `Imports` в начало файла с другими инструкциями `using` или `Imports`.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3. Замените объявление класса `WorkflowVersionMap` следующим объявлением.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     `WorkflowVersionMap` содержит три удостоверения рабочего процесса, которые сопоставляются с тремя определениями рабочих процессов из этого учебника и используется в следующих разделах при запуске и возобновлении рабочих процессов.  
  
### <a name="BKMK_StartWorkflow"></a> Чтобы запустить новый рабочий процесс  
  
1. Добавьте обработчик событий `Click` для `NewGame`. Чтобы добавить обработчик, перейдите в **конструкторе** для формы и дважды щелкните файл `NewGame`. Добавляется обработчик `NewGame_Click`, и активируется представление кода формы. Когда пользователь нажимает эту кнопку, запускается новый рабочий процесс.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Добавьте следующий код в обработчик события щелчка. Этот код создает словарь входных аргументов для рабочего процесса, различаемых по имени аргумента. Этот словарь содержит одну запись с диапазоном случайного созданных чисел, полученных из поля со списком диапазонов.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3. Затем добавьте следующий код, который запускает рабочий процесс. `WorkflowIdentity` и определение рабочего процесса, соответствующие выбранному типу рабочего процесса, извлекаются с помощью вспомогательного класса `WorkflowVersionMap`. Затем создается новый экземпляр `WorkflowApplication` с помощью определения рабочего процесса, `WorkflowIdentity` и словаря входных аргументов.  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4. Затем необходимо добавить следующий код, который добавляет рабочий процесс в список рабочих процессов и отображает сведения о версии рабочего процесса на форме.  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5. Вызовите `ConfigureWorkflowApplication` для настройки хранилища экземпляров, расширений и обработчиков жизненного цикла рабочего процесса для экземпляра `WorkflowApplication`.  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6. Теперь вызовите `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Ниже приведен полный пример обработчика `NewGame_Click`.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
### <a name="BKMK_ResumeWorkflow"></a> Возобновление рабочего процесса  
  
1. Добавьте обработчик событий `Click` для `EnterGuess`. Чтобы добавить обработчик, перейдите в **конструкторе** для формы и дважды щелкните файл `EnterGuess`. Когда пользователь нажимает эту кнопку, возобновляется рабочий процесс.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Добавьте следующий код, чтобы убедиться в том, что рабочий процесс выбран в списке рабочих процессов и догадка пользователя верна.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3. Затем извлеките `WorkflowApplicationInstance` сохраненного экземпляра рабочего процесса. `WorkflowApplicationInstance` представляет экземпляр сохраненного рабочего процесса, который еще не был связан с определением рабочего процесса. `DefinitionIdentity` экземпляра `WorkflowApplicationInstance` содержит `WorkflowIdentity` экземпляра сохраненного рабочего процесса. В этом учебнике служебный класс `WorkflowVersionMap` используется для сопоставления `WorkflowIdentity` с соответствующим определением рабочего процесса. Когда определение рабочего процесса получено, создается приложение `WorkflowApplication` на основе правильного определения.  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4. После создания `WorkflowApplication` настройте хранилище экземпляров, обработчики жизненного цикла рабочего процесса и расширения, вызвав `ConfigureWorkflowApplication`. Эти шаги требуются каждый раз, когда создается новое приложение `WorkflowApplication`, и должны быть выполнены до того, как экземпляр рабочего процесса будет загружен в `WorkflowApplication`. После загрузки рабочего процесса он возобновляется с догадкой пользователя.  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5. И наконец, очистите текстовое поле с догадкой и подготовьте форму для ввода другой догадки.  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     Ниже приведен полный пример обработчика `EnterGuess_Click`.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
### <a name="BKMK_TerminateWorkflow"></a> Завершение рабочего процесса  
  
1. Добавьте обработчик событий `Click` для `QuitGame`. Чтобы добавить обработчик, перейдите в **конструкторе** для формы и дважды щелкните файл `QuitGame`. Когда пользователь нажимает эту кнопку, рабочий процесс, выбранный на данный момент, завершается.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Добавьте следующий код в обработчик `QuitGame_Click`: Code First проверяет, что рабочий процесс выбран в списке рабочих процессов. Затем он загружает сохраненный экземпляр в `WorkflowApplicationInstance`, использует `DefinitionIdentity` для получения правильного определения рабочего процесса и инициализирует `WorkflowApplication`. После этого настраиваются расширения и обработчики жизненного цикла рабочего процесса с помощью метода `ConfigureWorkflowApplication`. После настройки `WorkflowApplication` приложение загружается и вызывается метод `Terminate`.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
### <a name="BKMK_BuildAndRun"></a> Сборка и запуск приложения  
  
1. Дважды щелкните **Program.cs** (или **Module1.vb**) в **обозревателе решений** для отображения кода.  
  
2. Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. Удалите или закомментируйте существующий рабочий процесс, код из размещения [как: Запуск рабочего процесса](how-to-run-a-workflow.md)и замените его следующим кодом.  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4. Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **обозревателе решений** и выберите **свойства**. В **приложения** задайте **приложения Windows** для **тип выходных данных**. Этот шаг не обязателен, но, если его не выполнить, вместе с формой отображается окно консоли.  
  
5. Нажмите клавиши Ctrl+Shift+B, чтобы создать приложение.  
  
6. Убедитесь, что **NumberGuessWorkflowHost** присвоено значение в качестве запускаемого приложения, и нажмите Ctrl + F5, чтобы запустить приложение.  
  
7. Выберите диапазон для игры на угадывание и тип рабочего процесса для запуска и нажмите кнопку **новая игра**. Введите догадку в **предположение** поле и нажмите кнопку **Go** Чтобы отправить догадку. Обратите внимание, что выходные данные действий `WriteLine` отображаются на форме.  
  
8. Запустите несколько рабочих процессов, с помощью разных типов рабочих процессов и диапазонов чисел, введите некоторые догадки и переключение между рабочими процессами, выбрав из **идентификатор экземпляра рабочего процесса** списка.  
  
     Обратите внимание, что, если перейти к новому рабочему процессу, предыдущие догадки и ход выполнения рабочего процесса не отображаются в окне состояния. Состояние недоступно, так как оно не перехвачено и не сохранено. На следующем шаге этого руководства [как: Создать настраиваемый участник отслеживания](how-to-create-a-custom-tracking-participant.md), создание настраиваемого участника отслеживания, сохраняет эти данные.
