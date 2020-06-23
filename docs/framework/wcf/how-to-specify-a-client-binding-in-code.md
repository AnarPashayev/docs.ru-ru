---
title: Практическое руководство. Задание привязки клиента в коде
description: Узнайте, как задать привязку для клиента WCF принудительно в коде. Клиент обращается к службе в этом примере.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244508"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Практическое руководство. Задание привязки клиента в коде
В этом примере создается клиент, предназначенный для использования службы калькулятора, и привязка этого клиента задается императивно в коде. Клиент обращается к службе `CalculatorService`, которая реализует интерфейс `ICalculator`; как служба, так и клиент используют класс <xref:System.ServiceModel.BasicHttpBinding>.  
  
 В приведенной процедуре предполагается, что служба калькулятора выполняется. Сведения о создании службы см. в разделе [как указать привязку службы в конфигурации](how-to-specify-a-service-binding-in-configuration.md). Он также использует [средство служебной программы метаданных ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), Windows Communication Foundation (WCF) обеспечивает автоматическое создание клиентских компонентов. Этот инструмент создает код клиента для доступа к службе.  
  
 Клиент создается в два этапа. Программа Svcutil.exe генерирует класс `ClientCalculator`, реализующий интерфейс `ICalculator`. Затем данное клиентское приложение создается путем создания экземпляра класса `ClientCalculator` и задания привязки и адреса для службы в коде.  
  
 Исходный экземпляр этого примера см. в примере [басикбиндинг](./samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Задание пользовательской привязки в коде  
  
1. Из командной строки запустите программу Svcutil.exe, чтобы создать код из метаданных службы.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Создаваемый клиент содержит интерфейс `ICalculator`, определяющий контракт службы, которому должна удовлетворять реализация клиента.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Создаваемый клиент также содержит реализацию класса `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Создайте экземпляр класса `ClientCalculator`, использующего класс <xref:System.ServiceModel.BasicHttpBinding> в клиентском приложении, и вызовите операции службы по указанному адресу.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Скомпилируйте и запустите клиент.  
  
## <a name="see-also"></a>См. также

- [Использование привязок для настройки служб и клиентов](using-bindings-to-configure-services-and-clients.md)
