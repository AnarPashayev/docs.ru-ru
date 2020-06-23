---
title: Учебник. Создание клиента Windows Communication Foundation
description: Узнайте, как создать клиент, извлекая метаданные из службы WCF в составе серии статей, которые помогут приступить к созданию приложения WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246328"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Учебник. Создание клиента Windows Communication Foundation

В этом руководстве описываются четвертые из пяти задач, необходимых для создания базового приложения Windows Communication Foundation (WCF). Общие сведения о учебниках см. в разделе [учебник. Начало работы с Windows Communication Foundation приложениями](getting-started-tutorial.md).

Следующей задачей для создания приложения WCF является создание клиента путем извлечения метаданных из службы WCF. Для добавления ссылки на службу, которая получает метаданные из конечной точки обмена метаданными службы, используется Visual Studio. Затем Visual Studio создает управляемый файл исходного кода для прокси клиента на выбранном языке. Он также создает файл конфигурации клиента (*App.config*). Этот файл позволяет клиентскому приложению подключаться к службе в конечной точке.

> [!NOTE]
> При вызове службы WCF из проекта библиотеки классов в Visual Studio используйте функцию **Добавление ссылки на службу** для автоматического создания прокси-сервера и связанного файла конфигурации. Однако, поскольку проекты библиотеки классов не используют этот файл конфигурации, необходимо добавить параметры в созданный файл конфигурации в файл *App.config* для исполняемого файла, вызывающего библиотеку классов.

> [!NOTE]
> В качестве альтернативы для создания прокси-класса и файла конфигурации вместо Visual Studio следует использовать [средство служебной программы для метаданных ServiceModel](#servicemodel-metadata-utility-tool) .

Клиентское приложение использует созданный прокси-класс для взаимодействия со службой. Эта процедура описана в разделе [учебник. Использование клиента](how-to-use-a-wcf-client.md).

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> - Создание и Настройка проекта консольного приложения для клиента WCF.
> - Добавьте ссылку на службу WCF для создания прокси-класса и файлов конфигурации.

## <a name="create-a-windows-communication-foundation-client"></a>Создание клиента Windows Communication Foundation

1. Создание проекта консольного приложения в Visual Studio:

    1. В меню **файл** выберите команду **Открыть**  >  **проект или решение** и перейдите к созданному ранее решению **GettingStarted** (*GettingStarted. sln*). Щелкните **Open**(Открыть).

    2. В меню **вид** выберите **Обозреватель решений**.

    3. В окне **Обозреватель решений** выберите решение **GettingStarted** (верхний узел), а затем в контекстном меню выберите **добавить**  >  **Новый проект** .

    4. В левой части окна **Добавление нового проекта** выберите категорию **Рабочий стол Windows** в разделе **Visual C#** или **Visual Basic**.

    5. Выберите шаблон **консольное приложение (.NET Framework)** и введите *GettingStartedClient* в поле **имя**. Щелкните **ОК**.

2. Добавьте ссылку в проект **GettingStartedClient** в <xref:System.ServiceModel> сборку:

    1. В окне **Обозреватель решений** выберите папку **References** в проекте **GettingStartedClient** , а затем в контекстном меню выберите пункт **Добавить ссылку** .

    2. В окне **Добавление ссылки** в разделе **сборки** в левой части окна выберите **платформа**.

    3. Найдите и выберите **System. ServiceModel**, а затем нажмите кнопку **ОК**.

    4. Сохраните решение, выбрав **файл**  >  **сохранить все**.

3. Добавьте ссылку на службу в службу калькулятора:

   1. В окне **Обозреватель решений** выберите папку **References** в проекте **GettingStartedClient** , а затем в контекстном меню выберите **Добавление ссылки на службу** .

   2. В окне **Добавление ссылки на службу** выберите **Обнаружение**.

      Служба CalculatorService запускается, и Visual Studio отображает ее в окне **службы** .

   3. Выберите **CalculatorService** , чтобы развернуть его и отобразить контракты службы, реализованные службой. Оставьте **пространство имен** по умолчанию и нажмите кнопку **ОК**.

      Visual Studio добавит новый элемент в папку **подключенные службы** проекта **GettingStartedClient** .

### <a name="servicemodel-metadata-utility-tool"></a>Средство служебной программы метаданных ServiceModel

В следующих примерах показано, как при необходимости использовать [средство служебной программы метаданных ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) для создания файла прокси-класса. Это средство создает файл прокси-класса и файл *App.config* . В следующих примерах показано, как создать прокси-сервер в C# и Visual Basic соответственно:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Файл конфигурации клиента

После создания клиента Visual Studio создаст файл конфигурации **App.config** в проекте **GettingStartedClient** , который должен быть похож на следующий пример:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

В [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) разделе Обратите внимание на [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) элемент. Элемент ** &lt; Endpoint &gt; ** определяет конечную точку, которую клиент использует для доступа к службе следующим образом:

- Адрес: `http://localhost:8000/GettingStarted/CalculatorService` . Адрес конечной точки.
- Контракт службы: `ServiceReference1.ICalculator` . Контракт службы обрабатывает взаимодействие между клиентом WCF и службой. Visual Studio создала этот контракт при использовании функции **Добавление ссылки на службу** . По сути, это копия контракта, определенного в проекте Жеттингстартедлиб.
- Привязка: <xref:System.ServiceModel.WSHttpBinding> . Привязка указывает HTTP как транспорт, взаимодействующую безопасность и другие сведения о конфигурации.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
>
> - Создание и Настройка проекта консольного приложения для клиента WCF.
> - Добавьте ссылку на службу WCF, чтобы создать класс прокси и файлы конфигурации для клиентского приложения.

Перейдите к следующему руководству, чтобы узнать, как использовать созданный клиент.

> [!div class="nextstepaction"]
> [Учебник. Использование клиента WCF](how-to-use-a-wcf-client.md)
