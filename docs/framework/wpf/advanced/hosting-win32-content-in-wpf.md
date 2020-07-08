---
title: Размещение содержимого Win32
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: c0c62f1999feaf591c512314515f01e83fa12591
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052095"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="88621-102">Размещение содержимого Win32 в WPF</span><span class="sxs-lookup"><span data-stu-id="88621-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88621-103">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="88621-103">Prerequisites</span></span>

<span data-ttu-id="88621-104">См. раздел [взаимодействие WPF и Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="88621-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="88621-105">Пошаговое руководство по Win32 в Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="88621-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="88621-106">Чтобы повторно использовать содержимое Win32 внутри [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложений, используйте <xref:System.Windows.Interop.HwndHost> , который является элементом управления, который делает HWND похожими на [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] содержимое.</span><span class="sxs-lookup"><span data-stu-id="88621-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="88621-107">Как <xref:System.Windows.Interop.HwndSource> , <xref:System.Windows.Interop.HwndHost> прост в использовании: наследование от <xref:System.Windows.Interop.HwndHost> и реализация `BuildWindowCore` методов и `DestroyWindowCore` , создание экземпляра <xref:System.Windows.Interop.HwndHost> производного класса и его размещение в [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложении.</span><span class="sxs-lookup"><span data-stu-id="88621-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="88621-108">Если логика Win32 уже упакована как элемент управления, ваша `BuildWindowCore` Реализация немного больше, чем вызов `CreateWindow` .</span><span class="sxs-lookup"><span data-stu-id="88621-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="88621-109">Например, чтобы создать элемент управления LISTBOX Win32 в C++, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="88621-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

<span data-ttu-id="88621-110">Но предположим, что код Win32 не так уж сам самодостаточный?</span><span class="sxs-lookup"><span data-stu-id="88621-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="88621-111">В этом случае можно создать диалоговое окно Win32 и внедрить его содержимое в более крупное [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложение.</span><span class="sxs-lookup"><span data-stu-id="88621-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="88621-112">В этом примере это показано в Visual Studio и C++, хотя это также можно сделать на другом языке или в командной строке.</span><span class="sxs-lookup"><span data-stu-id="88621-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="88621-113">Начните с простого диалогового окна, компилируемого в проект библиотеки DLL C++.</span><span class="sxs-lookup"><span data-stu-id="88621-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="88621-114">Затем Познакомьтесь с диалоговым окном в приложении большего размера [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="88621-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="88621-115">Компиляция библиотеки DLL как управляемой ( `/clr` )</span><span class="sxs-lookup"><span data-stu-id="88621-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="88621-116">Преобразование диалогового окна в элемент управления</span><span class="sxs-lookup"><span data-stu-id="88621-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="88621-117">Определение производного класса <xref:System.Windows.Interop.HwndHost> с помощью `BuildWindowCore` `DestroyWindowCore` методов и</span><span class="sxs-lookup"><span data-stu-id="88621-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="88621-118">Переопределение `TranslateAccelerator` метода для работы с диалоговыми ключами</span><span class="sxs-lookup"><span data-stu-id="88621-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="88621-119">Переопределение `TabInto` метода для поддержки перехода по клавише TAB</span><span class="sxs-lookup"><span data-stu-id="88621-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="88621-120">Переопределение `OnMnemonic` метода для поддержки назначенных клавиш</span><span class="sxs-lookup"><span data-stu-id="88621-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="88621-121">Создание экземпляра <xref:System.Windows.Interop.HwndHost> подкласса и помещение его в правый [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] элемент</span><span class="sxs-lookup"><span data-stu-id="88621-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="88621-122">Преобразование диалогового окна в элемент управления</span><span class="sxs-lookup"><span data-stu-id="88621-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="88621-123">Диалоговое окно можно преобразовать в дочерний HWND с помощью стилей WS_CHILD и DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="88621-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="88621-124">Перейдите в файл ресурсов (. RC), в котором определено диалоговое окно, и найдите начало определения диалогового окна:</span><span class="sxs-lookup"><span data-stu-id="88621-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="88621-125">Измените вторую строку на:</span><span class="sxs-lookup"><span data-stu-id="88621-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="88621-126">Это действие не полностью упаковывается в самодостаточный элемент управления. Вам все равно нужно вызвать, `IsDialogMessage()` чтобы обработка определенных сообщений была возможна, но изменение элемента управления обеспечивает простой способ размещения этих элементов управления в другом HWND.</span><span class="sxs-lookup"><span data-stu-id="88621-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="88621-127">Подкласс HwndHost</span><span class="sxs-lookup"><span data-stu-id="88621-127">Subclass HwndHost</span></span>

<span data-ttu-id="88621-128">Импортируйте такие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="88621-128">Import the following namespaces:</span></span>

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

<span data-ttu-id="88621-129">Затем создайте производный класс класса <xref:System.Windows.Interop.HwndHost> и переопределите `BuildWindowCore` `DestroyWindowCore` методы и:</span><span class="sxs-lookup"><span data-stu-id="88621-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

<span data-ttu-id="88621-130">Здесь используется `CreateDialog` для создания диалогового окна, которое на самом деле является элементом управления.</span><span class="sxs-lookup"><span data-stu-id="88621-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="88621-131">Поскольку это один из первых методов, вызываемых в библиотеке DLL, необходимо также выполнить стандартную инициализацию Win32, вызвав функцию, которая будет определена позже, с именем `InitializeGlobals()` :</span><span class="sxs-lookup"><span data-stu-id="88621-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="88621-132">Переопределение метода TranslateAccelerator для работы с диалоговыми ключами</span><span class="sxs-lookup"><span data-stu-id="88621-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="88621-133">Если вы запустили этот пример, вы получите элемент управления диалогового окна, отображающий, но при этом будет игнорироваться вся обработка клавиатуры, которая делает диалоговое окно функциональным.</span><span class="sxs-lookup"><span data-stu-id="88621-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="88621-134">Теперь необходимо переопределить `TranslateAccelerator` реализацию (которая поступает из `IKeyboardInputSink` интерфейса, <xref:System.Windows.Interop.HwndHost> реализующего).</span><span class="sxs-lookup"><span data-stu-id="88621-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="88621-135">Этот метод вызывается, когда приложение получает WM_KEYDOWN и WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="88621-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

<span data-ttu-id="88621-136">Это большой объем кода в одной части, поэтому он может использовать некоторые более подробные объяснения.</span><span class="sxs-lookup"><span data-stu-id="88621-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="88621-137">Сначала код, использующий макросы C++ и C++; необходимо иметь в виду, что уже существует макрос с именем `TranslateAccelerator` , который определен в файле WinUser. h:</span><span class="sxs-lookup"><span data-stu-id="88621-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="88621-138">Поэтому убедитесь, что определен `TranslateAccelerator` метод, а не `TranslateAcceleratorW` метод.</span><span class="sxs-lookup"><span data-stu-id="88621-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="88621-139">Точно так же существует и неуправляемый Winuser. h MSG, и управляемая `Microsoft::Win32::MSG` структура.</span><span class="sxs-lookup"><span data-stu-id="88621-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="88621-140">Можно определить неоднозначность между двумя `::` операторами с помощью оператора C++.</span><span class="sxs-lookup"><span data-stu-id="88621-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

<span data-ttu-id="88621-141">Оба они имеют одни и те же данные, но иногда проще работать с неуправляемым определением, поэтому в этом примере можно определить очевидную процедуру преобразования:</span><span class="sxs-lookup"><span data-stu-id="88621-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

<span data-ttu-id="88621-142">Вернуться к `TranslateAccelerator` .</span><span class="sxs-lookup"><span data-stu-id="88621-142">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="88621-143">Основной принцип заключается в вызове функции Win32 `IsDialogMessage` для выполнения максимально возможной работы, но не `IsDialogMessage` имеет доступа к каким-либо данным за пределами диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="88621-143">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="88621-144">В качестве вкладки пользователя в диалоговом окне, когда Табуляция выполняется после последнего элемента управления в нашем диалоговом окне, необходимо установить фокус на эту [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] часть, вызвав `IKeyboardInputSite::OnNoMoreStops` .</span><span class="sxs-lookup"><span data-stu-id="88621-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

<span data-ttu-id="88621-145">Теперь вызовите `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="88621-145">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="88621-146">Но одной из обязанностей `TranslateAccelerator` метода является то, что [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] вы обработали нажатие клавиши.</span><span class="sxs-lookup"><span data-stu-id="88621-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="88621-147">Если вы не обработали его, входное событие может быть туннелем и пузырьковым через остальную часть приложения.</span><span class="sxs-lookup"><span data-stu-id="88621-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="88621-148">Здесь вы узнаете о том, как работать с клавиатурой мессанже и характерность входной архитектуры в Win32.</span><span class="sxs-lookup"><span data-stu-id="88621-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="88621-149">К сожалению, не `IsDialogMessage` возвращает никакого способа, обрабатывает ли он определенное нажатие клавиши.</span><span class="sxs-lookup"><span data-stu-id="88621-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="88621-150">Еще хуже, он будет вызывать `DispatchMessage()` нажатия клавиш, которые не должны обработаны!</span><span class="sxs-lookup"><span data-stu-id="88621-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="88621-151">Поэтому необходимо выполнить реконструирование `IsDialogMessage` и вызвать его только для тех ключей, которые будут обработаны:</span><span class="sxs-lookup"><span data-stu-id="88621-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="88621-152">Переопределение метода Табинто для поддержки перехода по клавише TAB</span><span class="sxs-lookup"><span data-stu-id="88621-152">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="88621-153">Теперь, когда вы реализуете `TranslateAccelerator` , пользователь может переходить на вкладку внутри диалогового окна и использовать его в более масштабном [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложении.</span><span class="sxs-lookup"><span data-stu-id="88621-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="88621-154">Но пользователь не может вернуться на вкладку в диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="88621-154">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="88621-155">Чтобы решить эту проблему, переопределите `TabInto` :</span><span class="sxs-lookup"><span data-stu-id="88621-155">To solve that, you override `TabInto`:</span></span>

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

<span data-ttu-id="88621-156">`TraversalRequest`Параметр указывает, является ли действие вкладки вкладкой TAB или Shift.</span><span class="sxs-lookup"><span data-stu-id="88621-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="88621-157">Переопределение метода OnMnemonic для поддержки назначенных клавиш</span><span class="sxs-lookup"><span data-stu-id="88621-157">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="88621-158">Обработка клавиатуры почти завершена, но есть одна вещь, что не работает.</span><span class="sxs-lookup"><span data-stu-id="88621-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="88621-159">Если пользователь нажмет клавишу Alt-F, фокус не будет переходить к полю "First Name:" (изменить).</span><span class="sxs-lookup"><span data-stu-id="88621-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="88621-160">Поэтому Переопределите `OnMnemonic` метод:</span><span class="sxs-lookup"><span data-stu-id="88621-160">So, you override the `OnMnemonic` method:</span></span>

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

<span data-ttu-id="88621-161">Почему это не вызывается `IsDialogMessage` ?</span><span class="sxs-lookup"><span data-stu-id="88621-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="88621-162">У вас есть та же самая ошибка, что и перед--необходимо иметь возможность информировать [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] код о том, обрабатывает ли код нажатие клавиши или нет, и не `IsDialogMessage` может сделать это.</span><span class="sxs-lookup"><span data-stu-id="88621-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="88621-163">Кроме того, существует вторая ошибка, так как `IsDialogMessage` отказывается обрабатывать назначенный символ, если HWND не находится внутри диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="88621-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="88621-164">Создание экземпляра производного класса HwndHost</span><span class="sxs-lookup"><span data-stu-id="88621-164">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="88621-165">Наконец, теперь, когда все ключи и поддержка вкладок есть, вы можете поместить их <xref:System.Windows.Interop.HwndHost> в более крупное [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложение.</span><span class="sxs-lookup"><span data-stu-id="88621-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="88621-166">Если основное приложение написано в, самый [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] простой способ поместить его в нужное место — оставить пустой <xref:System.Windows.Controls.Border> элемент, где нужно поместить <xref:System.Windows.Interop.HwndHost> .</span><span class="sxs-lookup"><span data-stu-id="88621-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="88621-167">Здесь вы создадите <xref:System.Windows.Controls.Border> именованную `insertHwndHostHere` :</span><span class="sxs-lookup"><span data-stu-id="88621-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

<span data-ttu-id="88621-168">Все, что остается, — найти хорошее место в коде, чтобы создать экземпляр <xref:System.Windows.Interop.HwndHost> и подключить его к <xref:System.Windows.Controls.Border> .</span><span class="sxs-lookup"><span data-stu-id="88621-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="88621-169">В этом примере он будет размещен в конструкторе для <xref:System.Windows.Window> производного класса:</span><span class="sxs-lookup"><span data-stu-id="88621-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

<span data-ttu-id="88621-170">Это позволяет:</span><span class="sxs-lookup"><span data-stu-id="88621-170">Which gives you:</span></span>

![Снимок экрана: приложение WPF работает.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="88621-172">См. также</span><span class="sxs-lookup"><span data-stu-id="88621-172">See also</span></span>

- [<span data-ttu-id="88621-173">Взаимодействие WPF и Win32</span><span class="sxs-lookup"><span data-stu-id="88621-173">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
