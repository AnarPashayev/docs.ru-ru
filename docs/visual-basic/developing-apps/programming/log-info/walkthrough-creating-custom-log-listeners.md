---
title: Создание пользовательских прослушивателей журнала (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 90135074a4d34ea73743faffb2531305fcb326fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965265"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="4bbfc-102">Пошаговое руководство. Создание пользовательских прослушивателей журнала (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bbfc-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="4bbfc-103">В этом пошаговом руководстве демонстрируется создание пользовательского прослушивателя журнала и его настройка на прослушивание выходных данных объекта `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="4bbfc-104">Начало работы</span><span class="sxs-lookup"><span data-stu-id="4bbfc-104">Getting Started</span></span>  
 <span data-ttu-id="4bbfc-105">Прослушиватели журналов должны наследовать от класса <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="4bbfc-106">Создание прослушивателя</span><span class="sxs-lookup"><span data-stu-id="4bbfc-106">To create the listener</span></span>  
  
- <span data-ttu-id="4bbfc-107">В приложении создайте класс с именем `SimpleListener`, который наследует от класса <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="4bbfc-108">Методы <xref:System.Diagnostics.TraceListener.Write%2A> и <xref:System.Diagnostics.TraceListener.WriteLine%2A>, которые нужны для базового класса, используют `MsgBox` для отображения входных данных.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="4bbfc-109">К методам <xref:System.Diagnostics.TraceListener.Write%2A> и <xref:System.Diagnostics.TraceListener.WriteLine%2A> применяется атрибут <xref:System.Security.Permissions.HostProtectionAttribute>, чтобы их атрибуты соответствовали методы базового класса.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="4bbfc-110">Атрибут <xref:System.Security.Permissions.HostProtectionAttribute> позволяет узлу, на котором выполняется код, проверять наличие в коде синхронизации защиты узла.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4bbfc-111">Атрибут <xref:System.Security.Permissions.HostProtectionAttribute> действует только для неуправляемых приложений, на которых размещена среда CLR и реализована защита узлов, например для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="4bbfc-112">Чтобы объект `My.Application.Log` использовал прослушиватель журнала, следует присвоить строгое имя сборке, содержащей прослушиватель журнала.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="4bbfc-113">В следующей процедуре показано несколько простых шагов по созданию сборки прослушивателя журнала со строгим именем.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="4bbfc-114">Дополнительные сведения см. в разделе [Создание и использование сборок со строгими именами](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4bbfc-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="4bbfc-115">Задание строгого имени сборке прослушивателя журнала</span><span class="sxs-lookup"><span data-stu-id="4bbfc-115">To strongly name the log-listener assembly</span></span>  
  
1. <span data-ttu-id="4bbfc-116">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4bbfc-117">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2. <span data-ttu-id="4bbfc-118">Откройте вкладку **Подписывание**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-118">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="4bbfc-119">Выберите поле **Подписать сборку**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-119">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="4bbfc-120">В раскрывающемся списке **Выберите файл ключа строгого имени** щелкните **\<Новый...>** .</span><span class="sxs-lookup"><span data-stu-id="4bbfc-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="4bbfc-121">Откроется диалоговое окно **Создание ключа строгого имени**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5. <span data-ttu-id="4bbfc-122">Укажите имя для файла ключа в поле **Имя файла ключа**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6. <span data-ttu-id="4bbfc-123">Введите пароль в поля **Введите пароль** и **Подтверждение пароля**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7. <span data-ttu-id="4bbfc-124">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-124">Click **OK**.</span></span>  
  
8. <span data-ttu-id="4bbfc-125">Перестройте приложение.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="4bbfc-126">Добавление прослушивателя</span><span class="sxs-lookup"><span data-stu-id="4bbfc-126">Adding the Listener</span></span>  
 <span data-ttu-id="4bbfc-127">Теперь, когда сборка имеет строгое имя, необходимо определить строгое имя прослушивателя, чтобы объект `My.Application.Log` использовал прослушиватель журнала.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="4bbfc-128">Тип со строгим именем имеет следующий формат:</span><span class="sxs-lookup"><span data-stu-id="4bbfc-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="4bbfc-129">\<имя типа>, \<имя сборки>, \<номер версии>, \<язык>, \<строгое имя></span><span class="sxs-lookup"><span data-stu-id="4bbfc-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="4bbfc-130">Определение строгого имени прослушивателя</span><span class="sxs-lookup"><span data-stu-id="4bbfc-130">To determine the strong name of the listener</span></span>  
  
- <span data-ttu-id="4bbfc-131">В следующем коде показано, как определить строгое имя типа для `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="4bbfc-132">Строгое имя типа зависит от проекта.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="4bbfc-133">Можно добавить прослушиватель со строгим именем в коллекцию прослушивателей журнала `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="4bbfc-134">Добавление прослушивателя в My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="4bbfc-134">To add the listener to My.Application.Log</span></span>  
  
1. <span data-ttu-id="4bbfc-135">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="4bbfc-136">-или-</span><span class="sxs-lookup"><span data-stu-id="4bbfc-136">-or-</span></span>  
  
     <span data-ttu-id="4bbfc-137">Если есть файл app.config:</span><span class="sxs-lookup"><span data-stu-id="4bbfc-137">If there is an app.config file:</span></span>  
  
    1. <span data-ttu-id="4bbfc-138">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="4bbfc-139">В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="4bbfc-140">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-140">Click **Add**.</span></span>  
  
2. <span data-ttu-id="4bbfc-141">Найдите раздел `<listeners>` в разделе `<source>` с атрибутом `name` , равным DefaultSource, в разделе `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="4bbfc-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="4bbfc-142">Раздел `<sources>` находится в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="4bbfc-143">Добавьте этот элемент в раздел `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="4bbfc-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. <span data-ttu-id="4bbfc-144">Найдите раздел `<sharedListeners>` в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="4bbfc-145">Добавьте в этот раздел `<sharedListeners>` следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="4bbfc-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="4bbfc-146">Изменить значение `SimpleLogStrongName` на строгое имя прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="4bbfc-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbfc-147">См. также</span><span class="sxs-lookup"><span data-stu-id="4bbfc-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="4bbfc-148">Работа с журналами приложения</span><span class="sxs-lookup"><span data-stu-id="4bbfc-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="4bbfc-149">Практическое руководство. Исплючения журналов</span><span class="sxs-lookup"><span data-stu-id="4bbfc-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="4bbfc-150">Практическое руководство. Запись сообщений в журнал</span><span class="sxs-lookup"><span data-stu-id="4bbfc-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="4bbfc-151">Пошаговое руководство: Изменение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="4bbfc-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
