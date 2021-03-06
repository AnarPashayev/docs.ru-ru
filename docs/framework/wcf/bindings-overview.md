---
title: Общие сведения о привязках Windows Communication Foundation
description: Сведения о привязках, которые определяют способ подключения к службе WCF, включая элементы привязки и указания привязки для конечной точки службы.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: e918844342a20e7b6c22ef6a9fd3c01fe27db059
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272479"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Общие сведения о привязках Windows Communication Foundation

Привязки — это объекты, которые используются для указания сведений о соединении, необходимых для подключения к конечной точке службы Windows Communication Foundation (WCF). Для каждой конечной точки в службе WCF необходимо правильно указать привязку. В этом разделе описываются типы сведений о соединении, определяемые привязками, элементы привязки, привязки, которые включаются в WCF, а также способ указания привязки для конечной точки.  
  
## <a name="what-a-binding-defines"></a>Что определяет привязка  

 Информация в привязке может быть очень простой или очень сложной. Самые простые привязки указывают только транспортный протокол (такой как HTTP), который должен использоваться для подключения к конечной точке. Более того, информация, которую содержит привязка, включает сведения о том, как подключиться к конечной точке, попадает в одну из следующих категорий.  
  
 **Протоколы**  
 Определяют используемый механизм безопасности: возможность надежного обмена сообщениями или параметры потока контекста транзакций.  
  
 **Кодирование**  
 Определяет используемую в сообщениях кодировку (например, текст или двоичное кодирование).  
  
 **Транспорт**  
 Определяет основной используемый транспортный протокол (например, TCP или HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Элементы привязки  

 По сути, привязка состоит из упорядоченного стека элементов привязки, каждый из которых задает часть информации о связи, необходимой для подключения к конечной точке службы. Два нижних уровня стека являются обязательными. В основании стека находится элемент привязки транспорта, над ним - элемент, содержащий спецификации кодирования сообщения. Необязательные элементы привязки, задающие другие протоколы взаимодействия, располагаются над этими двумя обязательными элементами. Дополнительные сведения об этих элементах привязки и их правильном порядке см. в разделе [пользовательские привязки](./extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Привязки, предоставляемые системой  

 Информация в привязке может быть сложной, а некоторые параметры могут быть несовместимыми с другими. По этой причине в WCF включен набор привязок, предоставляемых системой. Эти привязки удовлетворяют большинство требований приложения. В следующих классах представлены некоторые примеры привязок, предоставляемых системой.  
  
- <xref:System.ServiceModel.BasicHttpBinding>: привязка протокола HTTP, которая подходит для подключения к веб-службам, соответствующим спецификации WS-I Basic Profile (например, службы на основе веб-службы ASP.NET).  
  
- <xref:System.ServiceModel.WSHttpBinding>: привязка с возможностью взаимодействия, которая подходит для подключения к конечным точкам, соответствующим протоколам WS-*.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Использует .NET Framework для подключения к другим конечным точкам WCF на том же компьютере.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Использует .NET Framework для создания соединений с сообщениями в очереди с другими конечными точками WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: Эта привязка обеспечивает более высокую производительность по сравнению с HTTP-привязками и идеально подходит для использования в локальной сети.
  
 Полный список с описаниями всех привязок, предоставляемых WCF, см. в разделе [привязки, предоставляемые системой](system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Использование собственных привязок  

 Если ни одна из предоставляемых системой привязок не имеет требуемого приложением службы сочетания возможностей, можно создать собственную привязку. Это можно сделать двумя способами. Можно создать новую привязку из уже имеющихся элементов привязки с помощью объекта <xref:System.ServiceModel.Channels.CustomBinding> или создать полностью пользовательскую привязку, наследуемую от привязки <xref:System.ServiceModel.Channels.Binding>. Дополнительные сведения о создании собственной привязки с помощью этих двух подходов см. в разделе [пользовательские привязки](./extending/custom-bindings.md) и [создание привязок User-Defined](./extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Использование привязок  

 Использование привязок включает два основных этапа.  
  
1. Выбор или определение привязки. Самый простой способ — выбрать одну из предоставляемых системой привязок, включенных в WCF, и использовать ее с параметрами по умолчанию. Также можно выбрать предоставляемую системой привязку и сбросить значения ее свойств таким образом, чтобы они соответствовали нужным требованиям. Кроме того, можно создать пользовательскую или определяемую пользователем привязку с расширенными возможностями управления и настройки.  
  
2. Создайте конечную точку, которая использует выбранную или определенную привязку.  
  
## <a name="code-and-configuration"></a>Код и конфигурация  

 Определить привязки можно двумя способами: через код или конфигурацию. Применять эти два способа можно независимо от того, какая привязка используется - предоставляемая системой или пользовательская. Как правило, использование кода позволяет полностью управлять определением привязки во время разработки. С другой стороны, с помощью конфигурации можно изменять параметры привязки, используя системный администратор или пользователь службы или клиента WCF, без повторной компиляции приложения службы. Такая гибкость часто желательно, так как вы не сможете предсказать конкретные требования к компьютерам, на которых должно быть развернуто приложение WCF. Если не указывать привязку (и адрес) в коде, их можно изменять без повторной компиляции или повторного развертывания приложения. Обратите внимание, что привязки, определенные в коде, создаются после задания привязок в конфигурации, что позволяет определенным в коде привязкам переопределять любые привязки, определенные в конфигурации.  
  
## <a name="see-also"></a>См. также

- [Использование привязок для настройки служб и клиентов](using-bindings-to-configure-services-and-clients.md)
