---
title: Практическое руководство. Размещение службы WCF в управляемом приложении
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637582"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Практическое руководство. Размещение службы WCF в управляемом приложении

Для размещения службы внутри управляемого приложения внедрите код службы внутрь кода управляемого приложения, определите конечную точку для службы императивно в коде, декларативно с помощью конфигурации или посредством конечных точек по умолчанию, а затем создайте экземпляр класса <xref:System.ServiceModel.ServiceHost>.

Чтобы начать принимать сообщения, вызовите метод <xref:System.ServiceModel.ICommunicationObject.Open%2A> для <xref:System.ServiceModel.ServiceHost>. При этом создается и открывается прослушиватель для этой службы. Такое размещение службы часто называется "резидентным", так как управляемое приложение самостоятельно выполняет функции ведущего приложения. Чтобы закрыть службу, вызовите метод <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> для <xref:System.ServiceModel.ServiceHost>.

Служба может также размещаться в управляемой службе Windows, в службах IIS или в службе активации процесса Windows (WAS). Дополнительные сведения о вариантах службы размещения, см. в разделе [размещение служб](../../../docs/framework/wcf/hosting-services.md).

Размещение служб в управляемом приложении - самый гибкий вариант размещения, так как в этом случае требуется минимальное развертывание инфраструктуры. Дополнительные сведения о размещении службы в управляемых приложениях см. в разделе [размещение в приложении управляемых](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

В следующей процедуре показано, как реализовать резидентную службу в консольном приложения.

## <a name="create-a-self-hosted-service"></a>Создание резидентной службы

1. Создайте новое консольное приложение.

   1. Откройте Visual Studio и выберите **New** > **проекта** из **файл** меню.

   2. В **установленные шаблоны** выберите **Visual C#** или **Visual Basic**, а затем выберите **Windows Desktop**.

   3. Выберите **консольное приложение** шаблона. Тип `SelfHost` в **имя** поле, а затем выберите **ОК**.

2. Щелкните правой кнопкой мыши **SelfHost** в **обозревателе решений** и выберите **добавить ссылку**. Выберите **System.ServiceModel** из **.NET** вкладку **ОК**.

    > [!TIP]
    > Если **обозревателе решений** окно не отображается, выберите пункт **обозревателе решений** из **представление** меню.

3. Дважды щелкните **Program.cs** или **Module1.vb** в **обозревателе решений** чтобы открыть его в окне кода, если он еще не открыт. Добавьте следующие инструкции в начало файла:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Определите и реализуйте контракт службы. В этом примере определяется служба `HelloWorldService`, которая возвращает сообщение на основании входных данных, передаваемых службе.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Дополнительные сведения о том, как определить и реализовать интерфейс службы см. в разделе [как: Определите контракт службы](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) и [как: Реализация контракта службы](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).

5. В начале метода `Main` создайте экземпляр класса <xref:System.Uri> с базовым адресом для службы.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Создайте экземпляр класса <xref:System.ServiceModel.ServiceHost>, передав <xref:System.Type>, представляющий тип службы, и универсальный код ресурса (URI) базового адреса в метод <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Включите публикацию метаданных и вызовите метод <xref:System.ServiceModel.ICommunicationObject.Open%2A> в <xref:System.ServiceModel.ServiceHost>, чтобы инициализировать службу и подготовить ее к приему сообщений.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > В этом примере используются конечные точки по умолчанию, и для данной службы не требуется файл конфигурации. Если конечные точки не настроены, то среда выполнения создает одну конечную точку для каждого базового адреса в каждом контракте службы, реализованном в службе. Дополнительные сведения о конечных точках по умолчанию, см. в разделе [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

7. Нажмите клавишу **Ctrl**+**Shift**+**B** для сборки решения.

## <a name="test-the-service"></a>Проверка службы

1. Нажмите клавишу **Ctrl**+**F5** для запуска службы.

2. Откройте **тестовый клиент WCF**.

    > [!TIP]
    > Чтобы открыть **тестовый клиент WCF**, откройте командную строку разработчика для Visual Studio и выполнение **WcfTestClient.exe**.

3. Выберите **добавить службу** из **файл** меню.

4. Тип `http://localhost:8080/hello` в поле "адрес" и нажмите кнопку **ОК**.

    > [!TIP]
    > Убедитесь, что служба запущена. В противном случае проверка дает отрицательный результат на этом этапе. Если базовый адрес в коде был изменен, используйте на этом этапе измененный базовый адрес.

5. Дважды щелкните **SayHello** под **Мои проекты служб** узла. Введите имя в **значение** столбца в **запроса** списке и нажмите кнопку **Invoke**.

   Появится ответное сообщение в **ответа** списка.

## <a name="example"></a>Пример

В следующем примере создается объект <xref:System.ServiceModel.ServiceHost> для размещения службы типа `HelloWorldService`, затем вызывается метод <xref:System.ServiceModel.ICommunicationObject.Open%2A> для <xref:System.ServiceModel.ServiceHost>. Базовый адрес предоставляется в коде, включена публикация метаданных и используются конечные точки по умолчанию.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>См. также

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Практическое руководство. Размещение службы WCF в IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Резидентное размещение](../../../docs/framework/wcf/samples/self-host.md)
- [Размещение служб](../../../docs/framework/wcf/hosting-services.md)
- [Практическое руководство. Определите контракт службы](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Практическое руководство. Реализация контракта службы](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Служебная программа для метаданных ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Использование привязок для настройки служб и клиентов](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Привязки, предоставляемые системой](../../../docs/framework/wcf/system-provided-bindings.md)
