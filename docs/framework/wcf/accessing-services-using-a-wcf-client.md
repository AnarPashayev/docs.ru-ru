---
title: Обращение к службам с использованием клиента WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297256"
---
# <a name="accessing-services-using-a-wcf-client"></a>Обращение к службам с использованием клиента WCF

После создания службы, следующим шагом является создание клиента WCF-прокси. Клиентское приложение использует прокси клиента WCF для взаимодействия со службой. Клиентские приложения обычно импортируют метаданные службы для создания кода клиента WCF, который может использоваться для вызова службы.

 Ниже приведены основные шаги для создания клиента WCF:

1. Скомпилируйте код службы.

2. Создайте прокси клиента WCF.

3. Создайте экземпляр клиентского прокси-класса WCF.

Клиентский прокси WCF можно создать вручную с помощью Service Model Metadata Utility Tool (SvcUtil.exe) Дополнительные сведения см. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Клиентский прокси WCF также может возникать в Visual Studio с помощью **Add Service Reference** функции. Для создания клиентского прокси-класса WCF любым методом выбранная служба должна быть запущена. Если служба размещается резидентно, то необходимо запустить узел. Если служба размещена на веб-сервере IIS/WAS, то больше ничего делать не нужно.

## <a name="servicemodel-metadata-utility-tool"></a>Средство ServiceModel Metadata Utility Tool
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) является средством командной строки для создания кода из метаданных. Ниже приведен пример базовой команды Svcutil.exe.

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Средство Svcutil.exe можно также использовать с файлами языков WSDL (язык описания веб-служб) и XSD (язык определения схемы XML) в файловой системе.

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Результатом является файл кода, содержащий код клиента WCF, который клиентское приложение может использовать для вызова службы.

 Кроме того, с помощью этого средства можно создавать файлы конфигурации.

```
Svcutil.exe <file1 [,file2]>
```

 Если задано только одно имя файла, это имя выходного файла. Если задано два имени файла, то первый файл является исходным файлом конфигурации, содержимое которого объединяется с создаваемой конфигурацией и записывается во второй файл. Дополнительные сведения о конфигурации см. в разделе [Настройка привязок для служб](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Незащищенные запросы метаданных представляют определенную угрозу таким же образом, любой незащищенным сетевым запросам: Если вы не уверены в конечную точку, взаимодействующие с говорит, что это, можно извлечь данные могут быть метаданные вредоносной службы.

## <a name="add-service-reference-in-visual-studio"></a>Функция «Добавить ссылку на службу» в Visual Studio

 Запустив службу, щелкните правой кнопкой мыши проект, который будет содержать клиентский прокси WCF и выберите **добавить** > **ссылки на службу**. В **Добавление диалога ссылки на службу**, введите URL-адрес для службы, которую требуется вызвать и нажмите **Go** кнопки. В диалоговом окне отобразится список доступных служб по указанному адресу. Дважды щелкните службу, см. в разделе контрактов и операций, доступных и указать пространство имен для сформированного кода щелкните **ОК** кнопки.

## <a name="example"></a>Пример
 В следующем примере кода показан созданный контракт службы.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 Средство ServiceModel Metadata служебной программы и **Add Service Reference** в Visual Studio создает класс клиента WCF. Класс наследует универсальному классу <xref:System.ServiceModel.ClientBase%601> и реализует интерфейс `ICalculator`. Кроме того, это средство создает интерфейс `ICalculator` (не показан в этом примере).

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a>Использование клиента WCF
 Использование клиента WCF, создайте экземпляр клиента WCF и затем вызывать его методы, как показано в следующем коде.

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a>Отладка создаваемых клиентом исключений

Многие исключения, создаваемые клиента WCF, вызваны исключения в службе. Ниже приведены некоторые примеры.

-   <xref:System.Net.Sockets.SocketException>: Существующее соединение было принудительно закрыто удаленным узлом.

-   <xref:System.ServiceModel.CommunicationException>: Базовое подключение было неожиданно закрыто.

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Подключение через сокет прервано. Это может быть вызвано ошибкой при обработке сообщения, истечением времени ожидания на удаленном узле или проблемой с соответствующим сетевым ресурсом.

Если происходят исключения этих типов, лучшим решением проблемы является включение трассировки на стороне службы и определение исключения, которое там произошло. Дополнительные сведения о трассировке см. в разделе [трассировки](../../../docs/framework/wcf/diagnostics/tracing/index.md) и [с помощью трассировки для устранения неполадок приложения](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>См. также

- [Практическое руководство. Создание клиента](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Практическое руководство. Службы доступа с дуплексным контрактом](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Практическое руководство. Асинхронный вызов операций службы](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Практическое руководство. Доступ к службам с односторонним контрактом и контрактом типа запрос ответ](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Практическое руководство. Доступ к WSE 3.0 служба](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Основные сведения о созданном коде клиента](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [Практическое руководство. Улучшения запуска время клиентских приложений WCF с использованием XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Указание поведения клиента во время выполнения](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Настройка поведения клиентов](../../../docs/framework/wcf/configuring-client-behaviors.md)
