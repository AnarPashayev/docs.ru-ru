---
title: Вызов событий из поставщика автоматизации пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: c973d6ddba498f4bdab4be764a4be6bff1cacf9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966366"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="1438b-102">Вызов событий из поставщика автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="1438b-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="1438b-103">Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="1438b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1438b-104">Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1438b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1438b-105">В этом разделе содержится пример кода, демонстрирующий вызов события из поставщика автоматизации пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="1438b-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1438b-106">Пример</span><span class="sxs-lookup"><span data-stu-id="1438b-106">Example</span></span>  
 <span data-ttu-id="1438b-107">В следующем примере событие [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] вызывается в реализации пользовательского элемента управления "Кнопка".</span><span class="sxs-lookup"><span data-stu-id="1438b-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="1438b-108">Эта реализация позволяет клиентскому приложению модели автоматизации пользовательского интерфейса имитировать нажатие кнопки.</span><span class="sxs-lookup"><span data-stu-id="1438b-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="1438b-109">Для исключения излишней обработки в этом примере проверяется <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> , чтобы увидеть, должны ли вызываться события.</span><span class="sxs-lookup"><span data-stu-id="1438b-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="1438b-110">См. также</span><span class="sxs-lookup"><span data-stu-id="1438b-110">See also</span></span>

- [<span data-ttu-id="1438b-111">Общие сведения о поставщиках автоматизации пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="1438b-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
