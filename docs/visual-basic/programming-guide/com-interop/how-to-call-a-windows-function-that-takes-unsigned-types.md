---
title: Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: d1a679242f89c17e58a837ac2d356e1594972fb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022367"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="b5f13-102">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5f13-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="b5f13-103">При использовании класса, модуля или структура, которая содержит члены типов целое число без знака, можно получить доступ к этим членам с помощью Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5f13-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="b5f13-104">Для вызова функции Windows, принимающей тип без знака</span><span class="sxs-lookup"><span data-stu-id="b5f13-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="b5f13-105">Используйте [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) сообщить Visual Basic, какая из библиотек содержит функцию его имя, что последовательность вызова и как преобразовать строки, при его вызове.</span><span class="sxs-lookup"><span data-stu-id="b5f13-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="b5f13-106">В `Declare` выражение use `UInteger`, `ULong`, `UShort`, или `Byte` соответствующим образом для каждого параметра с типом без знака.</span><span class="sxs-lookup"><span data-stu-id="b5f13-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="b5f13-107">См. в документации для функции Windows, чтобы найти имена и значения констант, используемых при вызове.</span><span class="sxs-lookup"><span data-stu-id="b5f13-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="b5f13-108">Многие из них определяются в файле WinUser.h.</span><span class="sxs-lookup"><span data-stu-id="b5f13-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="b5f13-109">Объявите необходимые константы в коде.</span><span class="sxs-lookup"><span data-stu-id="b5f13-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="b5f13-110">Многие константы Windows-32-разрядных неподписанных значений, их следует объявлять `As UInteger`.</span><span class="sxs-lookup"><span data-stu-id="b5f13-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="b5f13-111">Вызовите функцию обычным способом.</span><span class="sxs-lookup"><span data-stu-id="b5f13-111">Call the function in the normal way.</span></span> <span data-ttu-id="b5f13-112">В следующем примере вызывается функция Windows `MessageBox`, который принимает в качестве аргумента целого числа без знака.</span><span class="sxs-lookup"><span data-stu-id="b5f13-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="b5f13-113">Можно протестировать функцию `messageThroughWindows` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="b5f13-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="b5f13-114">`UInteger`, `ULong`, `UShort`, И `SByte` типы данных не являются частью [независимость от языка и независимые от языка компоненты](../../../standard/language-independence-and-language-independent-components.md) (CLS), поэтому CLS-совместимого кода нельзя использовать компонент, который они используются.</span><span class="sxs-lookup"><span data-stu-id="b5f13-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b5f13-115">Вызов неуправляемого кода, таких как интерфейс (API), Windows предоставляет код, чтобы потенциальные угрозы безопасности.</span><span class="sxs-lookup"><span data-stu-id="b5f13-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b5f13-116">Вызов Windows API требует разрешение неуправляемого кода, которое может повлиять на выполнение в ситуациях частичного доверия.</span><span class="sxs-lookup"><span data-stu-id="b5f13-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="b5f13-117">Дополнительные сведения см. в разделе <xref:System.Security.Permissions.SecurityPermission> и [разрешений доступа к коду](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5f13-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f13-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b5f13-118">See also</span></span>

- [<span data-ttu-id="b5f13-119">Типы данных</span><span class="sxs-lookup"><span data-stu-id="b5f13-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b5f13-120">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="b5f13-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="b5f13-121">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="b5f13-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="b5f13-122">Оператор Declare</span><span class="sxs-lookup"><span data-stu-id="b5f13-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="b5f13-123">Пошаговое руководство: Вызов API Windows</span><span class="sxs-lookup"><span data-stu-id="b5f13-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
