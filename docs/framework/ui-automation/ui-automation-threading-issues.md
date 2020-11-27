---
title: Проблемы потока модели автоматизация пользовательского интерфейса
description: Узнайте о проблемах, связанных с потоками модели автоматизации пользовательского интерфейса. Например, конфликты могут возникать, если клиентское приложение пытается взаимодействовать с собственным пользовательским интерфейсом в потоке пользовательского интерфейса.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 1f17336e6baa2e2baf4cd37a5b39bed913bd3bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258651"
---
# <a name="ui-automation-threading-issues"></a>Проблемы потока модели автоматизация пользовательского интерфейса

> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API автоматизации Windows. Автоматизация пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).  
  
 Из-за способа, которым [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] использует сообщения Windows, конфликты возникают, когда клиентское приложение пытается взаимодействовать с собственным [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] в потоке [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Эти конфликты могут привести к значительному снижению производительности или даже к зависанию приложения.  
  
 Если клиентское приложение предназначено для взаимодействия со всеми элементами на рабочем столе, включая его собственный [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], рекомендуется выполнять все вызовы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] в отдельном потоке. Сюда входит поиск элементов (например, с помощью метода <xref:System.Windows.Automation.TreeWalker> или <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ) и использование шаблонов элементов управления.  
  
 Безопасно выполнять вызовы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] в обработчике событий [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] обработчика событий, так как обработчик событий всегда вызывается в потоке, не являющемся потоком[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Однако при подписке на события, которые могут быть получены из клиентского приложения [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], необходимо вызывать метод <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>или связанный метод в потоке, не являющемся потоком[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Удалите обработчики событий в том же потоке.
