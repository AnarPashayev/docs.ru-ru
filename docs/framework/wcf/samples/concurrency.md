---
title: параллелизм
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 3a78612f679218711a81278184c16b04d6d6f802
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045679"
---
# <a name="concurrency"></a>параллелизм
Образец Concurrency демонстрирует использование <xref:System.ServiceModel.ServiceBehaviorAttribute> с перечислением <xref:System.ServiceModel.ConcurrencyMode>, определяющим, будет ли экземпляр службы обрабатывать сообщения последовательно или параллельно. Образец основан на [Начало работы](../../../../docs/framework/wcf/samples/getting-started-sample.md), который реализует `ICalculator` контракт службы. Этот образец определяет новый контракт, `ICalculatorConcurrency`, унаследованный от `ICalculator`, который добавляет две операции для контроля состояния параллелизма службы. Изменив параметр параллелизма, можно запустить клиент и посмотреть, как изменилось поведение.  
  
 В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.  
  
> [!NOTE]
> Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Доступны три режима параллелизма.  
  
- `Single`: Каждый экземпляр службы обрабатывает одно сообщение за раз. Это режим параллелизма по умолчанию.  
  
- `Multiple`: Каждый экземпляр службы обрабатывает несколько сообщений одновременно. Чтобы использовать этот режим параллелизма, реализация службы должна быть потокобезопасной.  
  
- `Reentrant`: Каждый экземпляр службы обрабатывает одно сообщение за раз, но принимает повторные вызовы. Служба принимает такие вызовы только в ответ на собственные вызовы. Повторный вход показан в образце [ConcurrencyMode.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) повторного входа.  
  
 Использование параллелизма связано с режимом создания экземпляров. В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.PerCall> параллелизм не имеет значения, так как каждое сообщение обрабатывается новым экземпляром службы. В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.Single> имеет значение параллелизм <xref:System.ServiceModel.ConcurrencyMode.Single> или <xref:System.ServiceModel.ConcurrencyMode.Multiple>, в зависимости от того, обрабатывает ли один экземпляр сообщения последовательно или параллельно. В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.PerSession> могут иметь значение любые режимы параллелизма.  
  
 Класс службы задает поведение параллелизма с помощью атрибута `[ServiceBehavior(ConcurrencyMode=<setting>)]`, как показано в следующем образце кода. Преобразуя в комментарий различные строки, можно поэкспериментировать с режимами параллелизма `Single` и `Multiple`. Не забывайте строить службу заново после изменения режима параллелизма.  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 По умолчанию образец использует параллелизм <xref:System.ServiceModel.ConcurrencyMode.Multiple> с режимом создания экземпляров <xref:System.ServiceModel.InstanceContextMode.Single>. Код клиента изменен для использования асинхронного прокси. Это позволяет клиенту направлять службе сразу несколько вызовов, не дожидаясь ответа на каждый вызов. Можно наблюдать различия в поведении режима параллелизма службы.  
  
 При выполнении примера запросы и ответы операций отображаются в окне консоли клиента. Отображается режим параллелизма, в котором работает служба, вызываются все операции, и отображается число операций. Обратите внимание, что в режиме параллельности `Multiple` результаты возвращаются в порядке, отличном от порядка вызовов, потому что служба обрабатывает несколько сообщений параллельно. Если изменить режим параллельности на `Single`, результаты возвращаются в порядке вызова, потому что служба обрабатывает все сообщения последовательно. Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Если для создания прокси-клиента используется программа Svcutil. exe, убедитесь, что включен `/async` параметр.  
  
3. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры. Этот образец расположен в следующем каталоге.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
