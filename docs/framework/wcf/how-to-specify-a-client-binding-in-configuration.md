---
title: Практическое руководство. Указание привязки клиента в конфигурации
description: Узнайте, как декларативно указать привязку для клиента WCF в файле конфигурации. Клиент обращается к службе в этом примере.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244495"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Практическое руководство. Указание привязки клиента в конфигурации
В этом примере создается клиентское консольное приложение, предназначенное для использования службы калькулятора, и привязка этого клиента задается декларативно в конфигурации. Клиент обращается к службе `CalculatorService`, которая реализует интерфейс `ICalculator`; как служба, так и клиент используют класс <xref:System.ServiceModel.BasicHttpBinding>.  
  
 В приведенной процедуре предполагается, что служба калькулятора работает. Сведения о том, как создать службу, см. в разделе [как указать привязку службы в конфигурации](how-to-specify-a-service-binding-in-configuration.md). Он также использует [средство служебной программы метаданных ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , которое Windows Communication Foundation (WCF) предоставляет для автоматического создания клиентских компонентов. Инструмент создает код и конфигурацию клиента для доступа к службе.  
  
 Клиент создается в два этапа. Программа Svcutil.exe генерирует класс `ClientCalculator`, реализующий интерфейс `ICalculator`. Затем данное клиентское приложение создается путем конструирования экземпляра класса `ClientCalculator`.  
  
 В большинстве случаев рекомендуется указывать привязку и адрес декларативно в конфигурации, а не принудительно в коде. Как правило, определять конечные точки в коде непрактично, поскольку привязки и адреса для развернутой службы чаще всего отличаются от привязок и адресов, используемых в процессе разработки службы. В общем случае, если не указывать привязку и адрес в коде, их можно изменять без повторной компиляции или повторного развертывания приложения.  
  
 Вы можете выполнить все описанные ниже действия по настройке с помощью [средства редактора конфигурации (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Исходный экземпляр этого примера см. в примере [басикбиндинг](./samples/basicbinding.md) .  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Указание привязки клиента в конфигурации  
  
1. Из командной строки запустите программу Svcutil.exe, чтобы создать код из метаданных службы.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Создаваемый клиент содержит интерфейс `ICalculator`, определяющий контракт службы, которому должна удовлетворять реализация клиента.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Создаваемый клиент также содержит реализацию класса `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Программа Svcutil.exe также создает конфигурацию для клиента, использующего класс <xref:System.ServiceModel.BasicHttpBinding>. При использовании Visual Studio назовите этот файл App.config. Обратите внимание, что адрес и сведения о привязке не указываются в любом месте реализации службы. Кроме того, для извлечения этих сведений из файла конфигурации не требуется писать код.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Создайте экземпляр класса `ClientCalculator` в приложении, затем вызовите операции службы.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Скомпилируйте и запустите клиент.  
  
## <a name="see-also"></a>См. также

- [Использование привязок для настройки служб и клиентов](using-bindings-to-configure-services-and-clients.md)
