---
title: Производство канала настройки
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: bebdd7e5913fd3bbc1ab88d32e6612b9bc951852
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241152"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="a53f3-102">Производство канала настройки</span><span class="sxs-lookup"><span data-stu-id="a53f3-102">Configuration Channel Factory</span></span>

<span data-ttu-id="a53f3-103">В образце описывается использование <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="a53f3-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="a53f3-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>Позволяет централизованно управлять конфигурацией клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="a53f3-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="a53f3-105">Это также можно использовать в случаях, когда конфигурация выбирается или изменяется после времени загрузки домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a53f3-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a53f3-106">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="a53f3-106">Demonstrates</span></span>

 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="a53f3-107">Разговор</span><span class="sxs-lookup"><span data-stu-id="a53f3-107">Discussion</span></span>

 <span data-ttu-id="a53f3-108">В образце описывается использование <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> для добавления определенного файла конфигурации к клиентскому приложению без использования файла конфигурации приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a53f3-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="a53f3-109">Образец состоит из двух проектов.</span><span class="sxs-lookup"><span data-stu-id="a53f3-109">The sample consists of two projects.</span></span> <span data-ttu-id="a53f3-110">Первый проект представляет собой простую службу, запускаемую в ответ на сообщения, передаваемые от клиентов.</span><span class="sxs-lookup"><span data-stu-id="a53f3-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="a53f3-111">Второй проект - это клиентское приложение, которое создает два объекта <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> с использованием <xref:System.Configuration.ExeConfigurationFileMap> для файла конфигурации Test.config и использует их для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="a53f3-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="a53f3-112">Оба клиента взаимодействуют со службой с использованием конфигурации, указанной в Test.config.</span><span class="sxs-lookup"><span data-stu-id="a53f3-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="a53f3-113">В следующем коде к клиентскому приложению добавляется пользовательский файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a53f3-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a53f3-114">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="a53f3-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a53f3-115">Откройте Visual Studio 2012 с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="a53f3-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="a53f3-116">Щелкните правой кнопкой мыши решение Конфигуратиончаннелфактори (2 проекта) и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="a53f3-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="a53f3-117">В окне **Общие свойства** выберите **запускаемый проект** и щелкните **Несколько запускаемых проектов**.</span><span class="sxs-lookup"><span data-stu-id="a53f3-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="a53f3-118">Переместите проект **службы** в начало списка с **действием "Запуск"**, а затем переместите проект **клиента** после проекта **службы** , а также с **действием "Запуск"**, чтобы **клиентский** проект выполнялся после проекта **службы** .</span><span class="sxs-lookup"><span data-stu-id="a53f3-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="a53f3-119">Нажмите кнопку **ОК**, а затем клавишу F5 (или CTRL + F5), чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="a53f3-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a53f3-120">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a53f3-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a53f3-121">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a53f3-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a53f3-122">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="a53f3-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a53f3-123">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a53f3-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
