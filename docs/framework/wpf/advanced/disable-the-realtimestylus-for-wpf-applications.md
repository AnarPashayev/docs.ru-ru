---
title: Отключение объекта RealTimeStylus для WPF-приложений
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124687"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="4933b-102">Отключение объекта RealTimeStylus для WPF-приложений</span><span class="sxs-lookup"><span data-stu-id="4933b-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="4933b-103">Windows Presentation Foundation (WPF) обеспечивает встроенную поддержку для обработки сенсорного ввода Windows 7. Поддержка проходит по в режиме реального времени платформой планшетного пера как <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, и <xref:System.Windows.UIElement.OnStylusMove%2A> события.</span><span class="sxs-lookup"><span data-stu-id="4933b-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="4933b-104">Windows 7 также предоставляет мультисенсорного ввода, как окно сообщения Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4933b-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="4933b-105">Эти два API являются взаимно исключают друг друга на одном HWND.</span><span class="sxs-lookup"><span data-stu-id="4933b-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="4933b-106">Включение сенсорного ввода с помощью этой платформы tablet (по умолчанию для приложений WPF) отключает сообщения WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4933b-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="4933b-107">Таким образом Чтобы использовать WM_TOUCH для получения сенсорных сообщений из окна WPF, необходимо отключить встроенную поддержку пера в WPF.</span><span class="sxs-lookup"><span data-stu-id="4933b-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="4933b-108">Это применимо в сценарии, такие как окно WPF, компонент, который использует WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4933b-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="4933b-109">Чтобы отключить прослушивание ввод с помощью пера WPF, удалите всю поддержку планшета, добавленные в окне WPF.</span><span class="sxs-lookup"><span data-stu-id="4933b-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4933b-110">Пример</span><span class="sxs-lookup"><span data-stu-id="4933b-110">Example</span></span>  
 <span data-ttu-id="4933b-111">В следующем примере кода показан способ удаления поддержки платформы планшета по умолчанию с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="4933b-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4933b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="4933b-112">See also</span></span>

- [<span data-ttu-id="4933b-113">Перехват ввода, осуществляемого пером</span><span class="sxs-lookup"><span data-stu-id="4933b-113">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
