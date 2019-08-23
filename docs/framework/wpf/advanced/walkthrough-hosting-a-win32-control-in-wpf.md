---
title: Пошаговое руководство. Размещение элемента управления Win32 в WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917544"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Пошаговое руководство. Размещение элемента управления Win32 в WPF
Windows Presentation Foundation (WPF) предоставляет обширную среду для создания приложений. Однако при наличии значительных инвестиций в код Win32 может оказаться более эффективным использовать по крайней мере часть этого кода в приложении WPF, а не переписывать его полностью. WPF предоставляет простой механизм для размещения окна Win32 на странице WPF.  
  
 В этом разделе рассматривается приложение, в котором [размещается элемент управления ListBox Win32 в WPF, в](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)котором размещается элемент управления "список" Win32. Эту общую процедуру можно расширить для размещения любого окна Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Требования  
 В этом разделе предполагается базовый знакомство с программированием WPF и Windows API. Базовые сведения о программировании WPF см. в разделе [Начало работы](../getting-started/index.md). Общие сведения о программировании API Windows см. в любом из многочисленных книг по теме в определенных окнах *программирования* с помощью Чарльз Петцольд.  
  
 Поскольку пример, сопровождающий этот раздел, реализован в C#, он использует службы вызова платформы (PInvoke) для доступа к API Windows. Некоторые знания о вызове PInvoke полезны, но не являются обязательными.  
  
> [!NOTE]
> Этот учебник включает ряд примеров кода из связанного примера. Однако для удобства чтения он не содержит полный пример кода. Вы можете получить или просмотреть полный код из [размещения элемента управления ListBox Win32 в примере WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Основная процедура  
 В этом разделе описывается базовая процедура размещения окна Win32 на странице WPF. В остальных разделах подробно описывается каждый шаг.  
  
 Основная процедура размещения  
  
1. Реализация страницы WPF для размещения окна. Один из способов — создать <xref:System.Windows.Controls.Border> элемент, чтобы зарезервировать раздел страницы для размещаемого окна.  
  
2. Реализуйте класс для размещения элемента управления, наследуемого <xref:System.Windows.Interop.HwndHost>от.  
  
3. В этом классе Переопределите <xref:System.Windows.Interop.HwndHost> член <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>класса.  
  
4. Создайте размещенное окно в качестве дочернего элемента для окна, содержащего страницу WPF. Хотя в традиционном программировании WPF не требуется явно использовать его, страница размещения является окном с дескриптором (HWND). HWND страницы можно получить с помощью `hwndParent` параметра <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> метода. Размещаемое окно необходимо создать в качестве дочернего объекта этого окна HWND.  
  
5. Создав главное окно, верните HWND размещаемого окна. Если требуется разместить один или несколько элементов управления Win32, обычно создается окно главного приложения в качестве дочернего элемента HWND и делаются дочерние элементы управления этого главного окна. Заключение элементов управления в главное окно предоставляет простой способ для страницы WPF получать уведомления от элементов управления, которые работают с некоторыми конкретными проблемами Win32 с уведомлениями через границу HWND.  
  
6. Обрабатывайте некоторые сообщения, которые отправляются в главное окно, например уведомления от дочерних элементов управления. Это можно сделать двумя способами.  
  
    - Если вы предпочитаете обработку сообщений в классе размещения, переопределите <xref:System.Windows.Interop.HwndHost.WndProc%2A> метод <xref:System.Windows.Interop.HwndHost> класса.  
  
    - Если вы предпочитаете, чтобы WPF обрабатывал сообщения, обработайте <xref:System.Windows.Interop.HwndHost> событие <xref:System.Windows.Interop.HwndHost.MessageHook> класса в коде программной части. Это событие возникает для каждого сообщения, получаемого размещаемым окном. При выборе этого варианта необходимо все равно переопределить <xref:System.Windows.Interop.HwndHost.WndProc%2A>, но требуется только минимальная реализация.  
  
7. Переопределите методы <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost>и для <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> . Эти методы необходимо переопределить для удовлетворения <xref:System.Windows.Interop.HwndHost> контракта, но может потребоваться лишь минимальная реализация.  
  
8. В файле кода программной части создайте экземпляр класса, размещающего элемент управления, и сделайте его дочерним <xref:System.Windows.Controls.Border> элементом элемента, предназначенного для размещения окна.  
  
9. Взаимодействие с размещенным окном путем отправки [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] ИТ и обработки сообщений из своих дочерних окон, например уведомлений, отправляемых элементами управления.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Реализация макета страницы  
 Макет страницы WPF, на которой размещен элемент управления ListBox, состоит из двух регионов. В левой части страницы размещается несколько элементов управления WPF, которые [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] предоставляют, что позволяет управлять элементом управления Win32. В правом верхнем углу страницы имеется квадратная область для размещенного элемента управления ListBox.  
  
 Код для реализации этого макета довольно прост. Корневым элементом является <xref:System.Windows.Controls.DockPanel> элемент с двумя дочерними элементами. Первый — <xref:System.Windows.Controls.Border> это элемент, в котором размещается элемент управления ListBox. Он занимает квадрат размером 200 x 200 в верхнем правом углу страницы. Второй — <xref:System.Windows.Controls.StackPanel> это элемент, содержащий набор элементов управления WPF, отображающих информацию и позволяющих управлять элементом управления ListBox путем установки предоставленных свойств взаимодействия. Для каждого из элементов, являющихся дочерними <xref:System.Windows.Controls.StackPanel>для, см. справочный материал по различным элементам, которые используются для получения подробных сведений о том, что такое элементы или что они делают, они перечислены в приведенном ниже примере кода, но не будут объяснены (базовый модель взаимодействия не требует каких-либо действий, они предоставляются для добавления взаимодействия в пример.  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Реализация размещения элемента управления Microsoft Win32 в классе  
 Ядром этого образца является класс, который фактически размещает в себе элемент управления, ControlHost.cs. Он наследует от <xref:System.Windows.Interop.HwndHost>. Конструктор принимает два параметра, высоту и ширину, которые соответствуют высоте и ширине <xref:System.Windows.Controls.Border> элемента, на котором размещается элемент управления ListBox. Эти значения используются позже, чтобы обеспечить соответствие <xref:System.Windows.Controls.Border> размера элемента управления элементу.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Кроме того, имеется набор констант. Эти константы в основном берутся из Winuser. h и позволяют использовать обычные имена при вызове функций Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Переопределение класса BuildWindowCore для создания окна Microsoft Win32  
 Этот метод переопределяется, чтобы создать окно Win32, которое будет размещено на странице, и установить соединение между окном и страницей. Поскольку в этом примере также показано размещение элемента управления ListBox, создаются два окна. Первый — это окно, которое на самом деле размещено на странице WPF. Элемент управления ListBox создается в качестве дочернего элемента этого окна.  
  
 Это делается для того, чтобы упростить получение уведомлений от элемента управления. <xref:System.Windows.Interop.HwndHost> Класс позволяет обрабатывать сообщения, отправленные в размещаемое окно. Если вы размещаете элемент управления Win32 напрямую, то получаете сообщения, отправленные во внутренний цикл обработки сообщений элемента управления. Можно отображать элемент управления и отправлять ему сообщения, но не получать уведомления, которые элемент управления отправляет своему родительскому окну. Это означает, среди прочего, что нет способа обнаружения взаимодействия пользователя с элементом управления. Вместо этого следует создать главное окно и сделать элемент управления дочерним элементом этого окна. Это позволит обрабатывать сообщения для главного окна, включая уведомления, отправляемые элементом управления. Для удобства, поскольку главное окно — это всего лишь программа-оболочка для элемента управления, мы будем называть этот пакет "элементом управления ListBox".  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Создание главного окна и элемента управления ListBox  
 Можно использовать PInvoke для создания главного окна для элемента управления путем создания и регистрации класса окна и т. д. Однако гораздо проще создать окно с помощью готового "статического" класса окон. Это позволит реализовать в окне процедуру, необходимую для получения уведомлений из элемента управления, и требует минимальной работы с кодом.  
  
 HWND элемента управления предоставляется через доступное только для чтения свойство, чтобы главная страница могла использовать его для отправки сообщения элементу управления.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Элемент управления ListBox создается в качестве дочернего элемента главного окна. Высота и ширина обоих окон задается с помощью значений, передаваемых конструктору (см. выше). Это гарантирует, что размер главного окна и элемента управления идентичен размеру отведенной для них области на странице.  После создания окон образец возвращает <xref:System.Runtime.InteropServices.HandleRef> объект, содержащий HWND главного окна.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Реализация классов DestroyWindow и WndProc  
 Кроме <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>того, необходимо <xref:System.Windows.Interop.HwndHost.WndProc%2A> переопределить методы и <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> для <xref:System.Windows.Interop.HwndHost>. В этом примере сообщения для элемента управления обрабатываются <xref:System.Windows.Interop.HwndHost.MessageHook> обработчиком, поэтому <xref:System.Windows.Interop.HwndHost.WndProc%2A> реализация и <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> является минимальной. В случае <xref:System.Windows.Interop.HwndHost.WndProc%2A>параметр `handled`имеетзначение ,указывающее,чтосообщениенебылообработано,ивозвращает0.`false` Для <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, просто удалите окно.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Размещение элемента управления на странице  
 Чтобы разместить элемент управления на странице, сначала необходимо создать новый экземпляр `ControlHost` класса. Передайте высоту и ширину элемента Border, который содержит элемент управления (`ControlHostElement`), `ControlHost` в конструктор. Это позволит гарантировать, что ListBox имеет правильный размер. Затем вы разместите элемент управления на странице, назначив `ControlHost` объект <xref:System.Windows.Controls.Decorator.Child%2A> свойству узла <xref:System.Windows.Controls.Border>.  
  
 Пример присоединяет обработчик к <xref:System.Windows.Interop.HwndHost.MessageHook> событию `ControlHost` объекта для получения сообщений от элемента управления. Это событие вызывается для каждого сообщения, отправляемого в главное окно. В данном случае это сообщения, отправленные в окно, которое служит оболочкой текущего элемента управления ListBox, включая уведомления от элемента управления. В этом примере вызывается метод SendMessage, чтобы получать информацию от элемента управления и менять его содержимое. Подробные сведения о том, как страница обменивается данными с элементом управления, рассматриваются в следующем разделе.  
  
> [!NOTE]
> Обратите внимание, что для SendMessage существует два объявления PInvoke. Это необходимо, поскольку один из них `wParam` использует параметр для передачи строки, а другой использует его для передачи целого числа. Необходимо отдельно объявить каждую сигнатуру, чтобы обеспечить правильный маршалинг данных.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Обмен данными между элементом управления и страницей  
 Вы управляете элементом управления, отправляя ему сообщения Windows. Элемент управления уведомляет вас, когда пользователь взаимодействует с ним, отправляя уведомления в главное окно. [Размещение элемента управления ListBox в Win32 в примере WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) включает пользовательский интерфейс, который предоставляет несколько примеров того, как это работает:  
  
- Добавить элемент в список  
  
- Удалить выбранный элемент из списка  
  
- Отобразить текст выбранного в настоящее время элемента  
  
- Отобразить число элементов в списке  
  
 Пользователь также может выбрать элемент в списке, щелкнув его так же, как и для обычного приложения Win32. Отображаемые данные обновляются каждый раз, когда пользователь меняет состояние списка, выбирая, добавляя или изменяя документы.  
  
 Чтобы добавить элементы, отправьте в список [ `LB_ADDSTRING` сообщение](/windows/desktop/Controls/lb-addstring). Чтобы удалить элементы, отправьте [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) , чтобы получить индекс текущего выделения, а затем [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) удалить элемент. Образец также отправляет [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)и использует возвращенное значение для обновления отображения, показывающего количество элементов. Оба экземпляра [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) используют одно из объявлений PInvoke, обсуждаемых в предыдущем разделе.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Когда пользователь выбирает элемент или изменяет его выбор, элемент управления уведомляет основное окно, отправляя ему [ `WM_COMMAND` сообщение](/windows/desktop/menurc/wm-command) <xref:System.Windows.Interop.HwndHost.MessageHook> , которое вызывает событие для страницы. Обработчик получает те же сведения, что и процедура главного окна в главном окне. Он также передает ссылку на логическое значение, `handled`. Вы можете `handled` задать `true` для параметра значение, чтобы указать, что вы обработали сообщение и дальнейшая обработка не требуется.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)отправляется по ряду причин, поэтому необходимо проверить идентификатор уведомления, чтобы определить, является ли оно событием, которое вы хотите обменять. Идентификатор содержится в высоком слове `wParam` параметра. В примере для извлечения идентификатора используются битовые операторы. Если пользователь внес или изменил свой выбор, идентификатор будет иметь [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)значение.  
  
 Когда [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) принимается, пример получает индекс выбранного элемента, отправляя [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)элемент управления сообщение. Чтобы получить текст, сначала создайте <xref:System.Text.StringBuilder>. Затем вы отправляете элемент управления [ `LB_GETTEXT` сообщение](/windows/desktop/Controls/lb-gettext). Передайте пустой <xref:System.Text.StringBuilder> объект в `wParam` качестве параметра. При [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) возврате объект <xref:System.Text.StringBuilder> будет содержать текст выбранного элемента. Для [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) такого использования требуется еще одно объявление PInvoke.  
  
 Наконец, задайте `handled` значение `true` , чтобы указать, что сообщение было обработано.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Interop.HwndHost>
- [Взаимодействие WPF и Win32](wpf-and-win32-interoperation.md)
- [Пошаговое руководство: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md) (Пошаговое руководство. Создание классического приложения WPF)
