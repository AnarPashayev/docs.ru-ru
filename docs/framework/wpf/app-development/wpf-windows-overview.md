---
title: Общие сведения об окнах WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: 6ab547951b00cc4a479034129254e4060486348d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817954"
---
# <a name="wpf-windows-overview"></a>Общие сведения об окнах WPF
Пользователи взаимодействуют с автономными приложениями Windows Presentation Foundation (WPF) через Windows. Основная цель окна — разместить содержимое, которое визуализирует данные и позволяет пользователям взаимодействовать с ними. Автономные [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] приложения предоставляют собственные окна с <xref:System.Windows.Window> помощью класса. В этом разделе <xref:System.Windows.Window> описываются основные принципы создания и управления окнами в автономных приложениях.  
  
> [!NOTE]
>  Приложения, размещенные [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] в браузере [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] , включая [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] и свободные страницы, не предоставляют собственные окна. Вместо этого они размещаются в Windows, предоставляемых Windows Internet Explorer. См. раздел [Общие сведения о приложениях браузера WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Класс окна  
 На следующем рисунке показаны составные части окна:  
  
 ![Снимок экрана, на котором показаны элементы окна.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Окно разделено на две области: неклиентскую и клиентскую.  
  
 Неклиентская *область* окна реализуется с помощью [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] и включает части окна, которые являются общими для большинства окон, в том числе следующие:  
  
- Граница.  
  
- Заголовок окна.  
  
- Значок.  
  
- Кнопки "Свернуть", "Развернуть" и "Восстановить".  
  
- Кнопка "Закрыть".  
  
- Системное меню с элементами, которые позволяют пользователям свернуть, развернуть, восстановить, перемещать, изменять размеры и закрыть окно.  
  
 *Клиентская область* окна — это область внутри неклиентской области окна, которая используется разработчиками для добавления содержимого, зависящего от приложения, таких как строки меню, панели инструментов и элементы управления.  
  
 В [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]окно инкапсулируется <xref:System.Windows.Window> классом, который используется для следующих действий:  
  
- Отобразить окно.  
  
- Настроить размер, положение и внешний вид окна.  
  
- Разместить содержимое конкретного приложения.  
  
- Управлять временем существования окна.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Реализация окна  
 Реализация типичного окна состоит как из внешнего вида, так и поведения, где *внешний вид* определяет, как окно будет выглядеть для пользователей и их *поведение* определяет способ работы окна при взаимодействии пользователей с ним. В [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]среде можно реализовать внешний вид и поведение окна с помощью кода или [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметки.  
  
 Однако в общем случае внешний вид окна реализуется с помощью [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметки, а его поведение реализуется с помощью кода программной части, как показано в следующем примере.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Чтобы разрешить [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] совместную работу файла разметки и файла кода программной части, необходимо выполнить следующие действия.  
  
- В разметке `Window` элемент должен `x:Class` включать атрибут. При сборке приложения существование `x:Class` в файле разметки вызывает [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] создание `partial` класса, производного от <xref:System.Windows.Window> , и имеет имя, заданное `x:Class` атрибутом. Для этого требуется добавить [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] объявление пространства имен для `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`схемы() [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Созданный `partial` класс`InitializeComponent` реализует метод, который вызывается для регистрации событий и задания свойств, реализованных в разметке.  
  
- В коде программной части класс должен быть `partial` классом с тем же именем, который указан `x:Class` атрибутом в разметке и должен быть производным от <xref:System.Windows.Window>класса. Это позволяет связать файл кода программной части с `partial` классом, созданным для файла разметки при сборке приложения (см. раздел [Создание приложения WPF](building-a-wpf-application-wpf.md)).  
  
- В коде программной части <xref:System.Windows.Window> класс должен реализовывать конструктор, который `InitializeComponent` вызывает метод. `InitializeComponent`реализуется созданным `partial` классом файла разметки для регистрации событий и задания свойств, определенных в разметке.  
  
> [!NOTE]
>  При добавлении нового <xref:System.Windows.Window> в проект с помощью [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <xref:System.Windows.Window> служб реализуется с помощью разметки и кода программной части, а также включается необходимая конфигурация для создания связи между файлами разметки и файлов кода программной части в виде описано здесь.  
  
 С такой конфигурацией вы можете сосредоточиться на определении внешнего вида окна в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметке и реализации его поведения в коде программной части. В следующем примере показано окно с кнопкой, реализованной в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметке, и обработчиком событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> события кнопки, реализованного в коде программной части.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Настройка определения окна для MSBuild  
 Реализация окна определяет, как оно настроено для [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Для окна, которое определено с помощью [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметки и кода программной части:  
  
- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]файлы разметки настраиваются [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] как `Page` элементы.  
  
- Файлы кода программной части настраиваются [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] как `Compile` элементы.  
  
 Это показано в следующем [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] файле проекта.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Сведения о создании [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] приложений см. [в разделе Создание приложения WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Время существования окна  
 Как и любой класс, окно имеет время существования, которое начинается с момента создания его экземпляра, после чего оно открывается, активируется, деактивируется и, в конечном счете, закрывается.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Открытие окна  
 Чтобы открыть окно, сначала создайте его экземпляр, как показано в следующем примере.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 В этом примере `MarkupAndCodeBehindWindow` экземпляр создается при запуске приложения, что происходит <xref:System.Windows.Application.Startup> при возникновении события.  
  
 При создании экземпляра окна ссылка на него автоматически добавляется в список окон, управляемых <xref:System.Windows.Application> объектом (см <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>.). Кроме того, первое окно, для которого создается экземпляр, по умолчанию устанавливается <xref:System.Windows.Application> в качестве главного окна приложения (см. раздел <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 После этого окно открывается путем вызова <xref:System.Windows.Window.Show%2A> метода; результат показан на следующем рисунке.  
  
 ![Окно, открытое при вызове Window. показывать](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Окно, открываемое путем вызова <xref:System.Windows.Window.Show%2A> , является немодальным окном, что означает, что приложение работает в режиме, позволяющем пользователям активировать другие окна в одном приложении.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A>вызывается для открытия окон, таких как модальные диалоговые окна. Дополнительные сведения см. в разделе [Обзор диалоговых](dialog-boxes-overview.md) окон.  
  
 Когда <xref:System.Windows.Window.Show%2A> вызывается, окно выполняет инициализацию перед отображением, чтобы установить инфраструктуру, позволяющую принимать входные данные пользователя. При инициализации <xref:System.Windows.Window.SourceInitialized> окна возникает событие, и отображается окно.  
  
 В качестве ярлыка <xref:System.Windows.Application.StartupUri%2A> можно задать, чтобы указать первое окно, которое автоматически открывается при запуске приложения.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 При запуске приложения окно, указанное значением <xref:System.Windows.Application.StartupUri%2A> , открывается немодально; внутреннее окно открывается путем вызова его <xref:System.Windows.Window.Show%2A> метода.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Владение окном  
 Окно, открываемое с помощью <xref:System.Windows.Window.Show%2A> метода, не имеет неявной связи с окном, которое его создало; пользователи могут взаимодействовать с любым окном независимо друг от друга. Это означает, что одно из окон может выполнять следующие действия:  
  
- Охватывает другой (если <xref:System.Windows.Window.Topmost%2A> для `true`свойства не задано значение).  
  
- Сворачиваться, разворачиваться и восстанавливаться без влияния на другое окно.  
  
 Для некоторых окон требуется связь с окном, которое их открывает. Например, приложение интегрированной среды разработки (IDE) может открывать окна свойств и окна инструментов, в которых типичное поведение заключается в покрытии окна, которое их создает. Кроме того, такие окна должны всегда закрываться, сворачиваться, разворачиваться и восстанавливаться вместе с окном, которое их создало. Такая связь может быть установлена путем создания одного окна другим и достигается путем задания <xref:System.Windows.Window.Owner%2A> свойству собственного *окна* ссылки на *окно владельца*. Эти действия показаны в следующем примере.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 После установки владения:  
  
- Принадлежащее окно может ссылаться на окно его владельца путем проверки значения его <xref:System.Windows.Window.Owner%2A> свойства.  
  
- Окно "владелец" может обнаружить все окна, которыми он владеет, проверив значение его <xref:System.Windows.Window.OwnedWindows%2A> свойства.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Предотвращение активации окна  
 Существуют ситуации, когда не следует активировать Windows при отображении, например в окнах беседы приложения электронной почты в стиле Internet Messenger или окна уведомлений.  
  
 Если в приложении есть окно, которое не должно быть активировано при отображении, можно <xref:System.Windows.Window.ShowActivated%2A> установить его `false` свойство в значение <xref:System.Windows.Window.Show%2A> перед вызовом метода в первый раз. Результат:  
  
- Окно не активируется.  
  
- <xref:System.Windows.Window.Activated> Событие окна не вызывается.  
  
- Текущее активированное окно останется активным.  
  
 Однако окно активируется, если пользователь щелкнет его неклиентскую или клиентскую область. В этом случае:  
  
- Окно активируется.  
  
- Вызывается <xref:System.Windows.Window.Activated> событие окна.  
  
- Ранее активированное окно деактивируется.  
  
- Затем события окна <xref:System.Windows.Window.Deactivated> и <xref:System.Windows.Window.Activated> порождаются в ответ на действия пользователя.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Активация окна  
 Когда окно открывается впервые, оно становится активным окном (если оно не отображается со <xref:System.Windows.Window.ShowActivated%2A> `false`значением). *Активное окно* — это окно, которое в данный момент захватывает ввод пользователя, например, нажатие клавиш и щелчки мышью. Когда окно активируется, оно вызывает <xref:System.Windows.Window.Activated> событие.  
  
> [!NOTE]
>  При первом открытии <xref:System.Windows.FrameworkElement.Loaded> окна события и <xref:System.Windows.Window.ContentRendered> вызываются только после <xref:System.Windows.Window.Activated> возникновения события. С учетом этого окно может считаться открытым при <xref:System.Windows.Window.ContentRendered> возникновении.  
  
 После активизации окна пользователь может активировать другое окно в том же приложении или активировать другое приложение. В этом случае активное в настоящий момент окно станет неактивным и вызовет <xref:System.Windows.Window.Deactivated> событие. Аналогично, когда пользователь выбирает неактивное окно, окно снова становится активным и <xref:System.Windows.Window.Activated> вызывается.  
  
 Одной из распространенных причин для <xref:System.Windows.Window.Activated> обработки <xref:System.Windows.Window.Deactivated> и является включение и отключение функций, которые могут выполняться только при активном окне. Например, некоторые окна отображают интерактивное содержимое, которое требует постоянного ввода данных или внимания пользователя, включая игры и видеопроигрыватели. Ниже приведен пример упрощенного видеопроигрывателя, демонстрирующий обработку <xref:System.Windows.Window.Activated> и <xref:System.Windows.Window.Deactivated> реализацию такого поведения.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Другие типы приложений могут выполнять код в фоновом режиме, когда окно деактивировано. Например, почтовый клиент может продолжать опрашивать почтовый сервер, пока пользователь работает с другими приложениями. Такие приложения часто обеспечивают другое или дополнительное поведение, когда главное окно не активно. В случае почтовой программы это может означать как добавление нового почтового элемента в папку "Входящие", так и добавление значка уведомления на панель задач. Значок уведомления должен отображаться только в том случае, если окно почты не активно, которое можно определить с помощью проверки <xref:System.Windows.Window.IsActive%2A> свойства.  
  
 Если фоновая задача завершается, в окне может потребоваться более срочно уведомлять пользователя о вызове <xref:System.Windows.Window.Activate%2A> метода. Если пользователь взаимодействует с другим приложением, которое активируется <xref:System.Windows.Window.Activate%2A> при вызове, кнопка панели задач окна отображается. Если пользователь взаимодействует с текущим приложением, вызов <xref:System.Windows.Window.Activate%2A> переводит окно на передний план.  
  
> [!NOTE]
>  Активацию области действия приложения можно выполнять с помощью <xref:System.Windows.Application.Activated?displayProperty=nameWithType> событий <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> и.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Закрытие окна  
 Время существования окна заканчивается, когда пользователь его закрывает. Окно может быть закрыто с помощью элементов в неклиентской области, включая следующие:  
  
- Элемент **закрытия** **системного** меню.  
  
- Нажатие клавиш ALT+F4.  
  
- Нажмите кнопку **Закрыть** .  
  
 Можно указать дополнительные способы закрытия окна для клиентской области, к наиболее типичным из которых относятся следующие:  
  
- Элемент **Exit** в меню **файл** , обычно для основных окон приложений.  
  
- Элемент **закрытия** в меню **файл** , обычно в дополнительном окне приложения.  
  
- Кнопка **Отмена** , обычно в модальном диалоговом окне.  
  
- Кнопка " **Закрыть** " (обычно в немодальном диалоговом окне).  
  
 Чтобы закрыть окно в ответ на один из этих пользовательских механизмов, необходимо вызвать <xref:System.Windows.Window.Close%2A> метод. В следующем примере реализуется возможность закрытия окна с помощью команды **выход** в меню **файл** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Когда окно закрывается, оно вызывает два события <xref:System.Windows.Window.Closing> : <xref:System.Windows.Window.Closed>и.  
  
 <xref:System.Windows.Window.Closing>вызывается перед закрытием окна и предоставляет механизм, с помощью которого можно предотвратить закрытие окна. Одна из распространенных причин, препятствующих закрытию окна, заключается в том, что содержимое окна содержит измененные данные. В этом случае <xref:System.Windows.Window.Closing> событие может быть обработано, чтобы определить, являются ли данные "грязными", и, если да, попросить пользователя либо продолжить закрытие окна без сохранения данных, либо отменить закрытие окна. В следующем примере показаны основные аспекты обработки <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Обработчик событий передается, который реализует свойство, для `true` которого задается значение, чтобы предотвратить закрытие окна. <xref:System.ComponentModel.CancelEventArgs> <xref:System.Windows.Window.Closing>  
  
 Если <xref:System.Windows.Window.Closing> не обрабатывается или обрабатывается, но не отменяется, окно закроется. Сразу же после закрытия <xref:System.Windows.Window.Closed> окна вызывается. На этом этапе невозможно предотвратить закрытие окна.  
  
> [!NOTE]
>  Приложение может быть настроено для автоматического завершения работы при закрытии главного окна приложения (см <xref:System.Windows.Application.MainWindow%2A>.) или при закрытии последнего окна. Дополнительные сведения см. в разделе <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Хотя окно может быть явно закрыто с помощью механизмов, предоставленных в неклиентской и клиентской областях, окно также может быть неявно закрыто в результате поведения в других частях приложения или [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], включая следующие:  
  
- Пользователь выходит из системы или завершает работу Windows.  
  
- Владелец окна закрывается (см <xref:System.Windows.Window.Owner%2A>. раздел).  
  
- Главное окно приложения закрыто и <xref:System.Windows.Application.ShutdownMode%2A> имеет значение. <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- вызывается метод <xref:System.Windows.Application.Shutdown%2A>;  
  
> [!NOTE]
>  После закрытия окно нельзя открыть повторно.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>События времени существования окна  
 На следующем рисунке показана последовательность основных событий во время существования окна:  
  
 ![Схема, показывающая события в течение времени существования окна.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 На следующем рисунке показана последовательность основных событий во время существования окна, которое отображается без активации (<xref:System.Windows.Window.ShowActivated%2A> `false` устанавливается до отображения окна):  
  
 ![Схема, показывающая события в течение времени существования окна без активации.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Расположение окна  
 Когда окно открыто, оно располагается в координатах x и y относительно рабочего стола. Это расположение можно определить с помощью проверки <xref:System.Windows.Window.Left%2A> свойств и <xref:System.Windows.Window.Top%2A> соответственно. Можно задать эти свойства, чтобы изменить расположение окна.  
  
 Можно также указать начальное расположение <xref:System.Windows.Window> при первом отображении, <xref:System.Windows.Window.WindowStartupLocation%2A> задав для свойства одно из следующих <xref:System.Windows.WindowStartupLocation> значений перечисления:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (по умолчанию)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Если в качестве <xref:System.Windows.WindowStartupLocation.Manual>расположения запуска задано значение, <xref:System.Windows.Window.Left%2A> а свойства <xref:System.Windows.Window.Top%2A> и не заданы, <xref:System.Windows.Window> то запросит Windows указать расположение в.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Окна верхнего уровня и Z-порядок  
 Помимо расположения в координатах x и y, окно имеет координату по оси z, которая определяет его вертикальную позицию относительно других окон. Это называется z-порядком окна. Существует два типа: обычный z-порядок и верхний z-порядок. Расположение окна в *стандартном z-порядке* определяется тем, активно ли оно в данный момент. По умолчанию окно находится в обычном z-порядке. Расположение окна в *верхнем z-порядке* также определяется тем, активно ли оно в данный момент. Кроме того, окна в самом верхнем z-порядке всегда расположены над окнами в обычном z-порядке. Окно находится в самом верхнем z-порядке, присвоив <xref:System.Windows.Window.Topmost%2A> `true`свойству значение.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 В каждом z-порядке активное в данный момент окно появляется поверх всех других окон в том же z-порядке.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Размер окна  
 Помимо расположения рабочего стола, размер окна определяется несколькими свойствами, включая различные свойства <xref:System.Windows.Window.SizeToContent%2A>Width и Height.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> и<xref:System.Windows.FrameworkElement.MaxWidth%2A> используются для управления диапазоном ширины, который может иметь окно в течение своего времени существования, и настраивается, как показано в следующем примере.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Высота окна управляется <xref:System.Windows.FrameworkElement.MinHeight%2A>,, <xref:System.Windows.FrameworkElement.Height%2A>и <xref:System.Windows.FrameworkElement.MaxHeight%2A>настраивается, как показано в следующем примере.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Так как различные значения ширины и высоты определяют диапазон, то что ширина и высота изменяемого окна могут находиться в любом месте указанного диапазона для соответствующего измерения. Чтобы определить текущую ширину и высоту, проверьте <xref:System.Windows.FrameworkElement.ActualWidth%2A> и <xref:System.Windows.FrameworkElement.ActualHeight%2A>соответственно.  
  
 Если вы хотите, чтобы ширина и высота окна имели размер, соответствующий размеру содержимого окна, можно использовать <xref:System.Windows.Window.SizeToContent%2A> свойство, которое имеет следующие значения:  
  
- <xref:System.Windows.SizeToContent.Manual>. Нет эффекта (по умолчанию).  
  
- <xref:System.Windows.SizeToContent.Width>. По ширине содержимого, что оказывает тот же результат, что <xref:System.Windows.FrameworkElement.MinWidth%2A> и установка и <xref:System.Windows.FrameworkElement.MaxWidth%2A> в ширину содержимого.  
  
- <xref:System.Windows.SizeToContent.Height>. Вписать в высоту содержимого, что оказывает тот же результат, что <xref:System.Windows.FrameworkElement.MinHeight%2A> и при задании и <xref:System.Windows.FrameworkElement.MaxHeight%2A> высоты содержимого.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. По ширине и <xref:System.Windows.FrameworkElement.MinHeight%2A> высоте содержимого, что оказывает тот же результат, что и установка и <xref:System.Windows.FrameworkElement.MaxHeight%2A> в высоту <xref:System.Windows.FrameworkElement.MinWidth%2A> содержимого, и установка и <xref:System.Windows.FrameworkElement.MaxWidth%2A> в ширину содержимого.  
  
 В следующем примере показано окно, размеры которого автоматически устанавливаются равными его содержимому по вертикали и по горизонтали при первом отображении.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 В следующем примере показано, <xref:System.Windows.Window.SizeToContent%2A> как задать свойство в коде, чтобы указать, как размер окна изменяется в соответствии с содержимым.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Порядок приоритета для свойств размера  
 Различные свойства размеров окна объединяются для определения диапазона ширины и высоты окна изменяемого размера. Чтобы обеспечить соблюдение допустимого диапазона, <xref:System.Windows.Window> вычисляет значения свойств размера с помощью следующих порядков приоритета.  
  
 **Для свойств высоты:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Для свойств ширины:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Порядок приоритета также может определять размер окна, когда оно развернуто, что управляется <xref:System.Windows.Window.WindowState%2A> свойством.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Состояние окна  
 В течение времени существования окна изменяемого размера оно может иметь три состояния: обычное, свернутое и развернутое. Окно с нормальным состоянием является состоянием окна по умолчанию. Окно с этим состоянием позволяет пользователю перемещать его и изменять размер, используя захват для изменения размера или границу.  
  
 Окно с свернутым состоянием сворачивается к кнопке панели задач, если <xref:System.Windows.Window.ShowInTaskbar%2A> свойство имеет значение `true`; в противном случае оно сворачивается до наименьшего возможного размера, которое может быть и перемещается в левый нижний угол рабочего стола. Ни один из типов свернутого окна не может быть изменен с помощью границы или захвата для изменения размера, хотя свернутое окно, которое не отображается на панели задач, можно перетаскивать на рабочем столе.  
  
 Окно с развернутым состоянием разворачивается до максимального размера, который может быть только большим, чем <xref:System.Windows.FrameworkElement.MaxWidth%2A>зависят от свойств, <xref:System.Windows.FrameworkElement.MaxHeight%2A>и. <xref:System.Windows.Window.SizeToContent%2A> Как и для свернутого окна, размер развернутого окна нельзя изменить с помощью захвата для изменения размера или перетаскивания границы.  
  
> [!NOTE]
>  Значения <xref:System.Windows.Window.Top%2A>свойств, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>и окнавсегдапредставляютзначениядлянормальногосостояния,дажееслиокновданныймоментразвернутоилиуменьшено.<xref:System.Windows.FrameworkElement.Height%2A>  
  
 Состояние окна можно настроить, задав его <xref:System.Windows.Window.WindowState%2A> свойство, которое может иметь одно из следующих <xref:System.Windows.WindowState> значений перечисления:  
  
- <xref:System.Windows.WindowState.Normal> (по умолчанию)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 В следующем примере показано создание окна, которое отображается развернутым при его открытии.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 В общем случае следует задать <xref:System.Windows.Window.WindowState%2A> настройку начального состояния окна. После отображения окна изменяемого размера пользователи могут нажимать кнопки свертывания, развертывания и восстановления на панели заголовка окна, чтобы изменить состояние окна.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Внешний вид окна  
 Можно изменить внешний вид клиентской области окна, добавляя в нее определенное содержимое, такое как кнопки, метки и текстовые поля. Чтобы настроить неклиентскую область, <xref:System.Windows.Window> предоставляет несколько свойств, которые включают в себя <xref:System.Windows.Window.Icon%2A> установку значка окна и <xref:System.Windows.Window.Title%2A> установку его заголовка.  
  
 Можно также изменить внешний вид и поведение границы неклиентской области, настраивая режим изменения размера окна, стиль окна и отображение в виде кнопки на панели задач рабочего стола.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Режим изменения размера  
 В зависимости от <xref:System.Windows.Window.WindowStyle%2A> свойства можно управлять тем, как пользователи (и, если) могут изменять размер окна. Выбранный стиль окна влияет на то, может ли пользователь изменять размер окна, перетаскивая его границу мышью, отображаются ли кнопки **сворачивания**, **развернуть**и **изменить размер** в неклиентской области, и если они отображаются, то доступной.  
  
 Можно настроить изменение размера окна, задав его <xref:System.Windows.Window.ResizeMode%2A> свойство, которое может быть одним из следующих <xref:System.Windows.ResizeMode> значений перечисления:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (по умолчанию)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Как и в случае, режим изменения размера окна вряд ли изменится во время его существования, что означает, что, скорее всего, вы [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] задаете его из разметки. <xref:System.Windows.Window.WindowStyle%2A>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Обратите внимание, что можно определить, является ли окно развернутым, минимальным или восстанавливаемым, <xref:System.Windows.Window.WindowState%2A> проверив свойство.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Стиль окна  
 Граница, предоставляемая из неклиентской области окна, подходит для большинства приложений. Однако существуют ситуации, когда требуются различные типы границ либо границы вовсе не требуются, в зависимости от типа окна.  
  
 Чтобы управлять тем, какой тип границы получает окно, задайте <xref:System.Windows.Window.WindowStyle%2A> свойству одно из следующих значений <xref:System.Windows.WindowStyle> перечисления:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (по умолчанию)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Эффект этих стилей окна показан на следующем рисунке:  
  
 ![Иллюстрация стилей границ окна.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Можно задать <xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] с помощью разметки или кода, так как маловероятно, что в течение времени существования окна он будет настроен с помощью [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] разметки.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Непрямоугольный стиль окна  
 Существуют также ситуации, когда стили границ, <xref:System.Windows.Window.WindowStyle%2A> позволяющие вам быть, недостаточно. Например, может потребоваться создать приложение с непрямоугольной границей, [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] например с помощью.  
  
 Например, рассмотрим всплывающее окно распознавания речи, показанное на следующем рисунке:  
  
 ![Всплывающее окно речевого ввода, говорящее на перетаскивание.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Этот тип окна может быть создан путем присвоения <xref:System.Windows.Window.WindowStyle%2A> <xref:System.Windows.WindowStyle.None>свойству значения, а также специальной поддержки <xref:System.Windows.Window> для прозрачности.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Это сочетание значений указывает, что окно отрисовывается полностью прозрачным. В этом состоянии нельзя использовать элементы оформления неклиентской области окна (кнопки "Закрыть", "Минимизировать", "Развернуть" и "Восстановить" и т. д.). Следовательно, необходимо предоставить свои собственные элементы.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Наличие панели задач  

Внешний вид окна по умолчанию включает кнопку панели задач, как показано на следующем рисунке.

 ![Снимок экрана, на котором показано окно с кнопкой на панели задач.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 У некоторых типов окон нет кнопки панели задач, например окон сообщений и диалоговых окон (см. [Обзор диалоговых окон](dialog-boxes-overview.md)). Можно указать, отображается ли кнопка панели задач для окна, задав <xref:System.Windows.Window.ShowInTaskbar%2A> свойство (`true` по умолчанию).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Вопросы безопасности  
 <xref:System.Windows.Window>требует `UnmanagedCode` создания экземпляра разрешения безопасности. Для приложений, установленных и запускаемых с локального компьютера, это включено в набор разрешений, предоставленных приложению.  
  
 Однако это выходит за рамки набора разрешений, предоставленных приложениям, которые запускаются из зоны Интернета или местной интрасети с помощью ClickOnce. Следовательно, пользователи получат предупреждение системы безопасности ClickOnce и потребуют повысить уровень разрешений приложения до полного доверия.  
  
 Кроме того [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] , не может отображать окна или диалоговые окна по умолчанию. Обсуждение вопросов безопасности отдельных приложений см. в разделе [стратегия безопасности WPF — безопасность платформы](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Другие типы окон  
 <xref:System.Windows.Navigation.NavigationWindow>— Это окно, предназначенное для размещения содержимого, доступного для навигации. Дополнительные сведения см. в разделе [Общие сведения о навигации](navigation-overview.md).  
  
 Диалоговые окна — это окна, которые часто используются для сбора информации от пользователя для выполнения функции. Например, когда пользователь хочет открыть файл, диалоговое окно **Открытие файла** обычно отображается приложением для получения имени файла от пользователя. Дополнительные сведения см. в разделе [Общие сведения о диалоговых окнах](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Общие сведения о диалоговых окнах](dialog-boxes-overview.md)
- [Построение приложения WPF](building-a-wpf-application-wpf.md)
