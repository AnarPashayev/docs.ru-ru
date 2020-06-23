---
title: Практическое руководство. Как создать простую веб-службу WCF HTTP
description: Узнайте, как создать службу, предоставляющую конечную веб-точку в WCF. Конечные точки веб-сайта отправляют данные с помощью XML или JSON. Конверт SOAP отсутствует.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247108"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Практическое руководство. Как создать простую веб-службу WCF HTTP

Windows Communication Foundation (WCF) позволяет создать службу, предоставляющую конечную веб-точку. Сетевые конечные точки отправляют данные в виде XML-кода или JSON, без конверта SOAP. В этом разделе показано, как предоставить такую конечную точку.

> [!NOTE]
> Единственный способ защитить сетевую конечную точку заключается в том, чтобы предоставить ее через протокол HTTPS, используя механизм безопасности транспорта. Поскольку при использовании безопасности на основе сообщений сведения безопасности обычно помещаются в заголовки SOAP и сообщения, отправляемые другим конечным точкам (не SOAP), не содержат конвертов SOAP, негде разместить данные по безопасности и приходится полагаться на механизм безопасности транспорта.

## <a name="to-create-a-web-endpoint"></a>Создание сетевой конечной точки

1. Определите контракт службы с использованием интерфейса, отмеченного атрибутами <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> и <xref:System.ServiceModel.Web.WebGetAttribute>.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > По умолчанию атрибут <xref:System.ServiceModel.Web.WebInvokeAttribute> сопоставляет с операцией вызовы POST. Однако можно указать метод HTTP (например, HEAD, PUT или DELETE) для сопоставления с операцией, задав параметр «method=». В методе <xref:System.ServiceModel.Web.WebGetAttribute> отсутствует параметр «method=», при этом метод сопоставляет с операцией службы только вызовы GET.

2. Реализуйте контракт службы.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Размещение службы

1. Создание объекта <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Добавьте конечную точку <xref:System.ServiceModel.Description.ServiceEndpoint> с поведением <xref:System.ServiceModel.Description.WebHttpBehavior>.

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Если не добавить конечную точку, <xref:System.ServiceModel.Web.WebServiceHost> автоматически создает конечную точку по умолчанию. <xref:System.ServiceModel.Web.WebServiceHost> также добавляет <xref:System.ServiceModel.Description.WebHttpBehavior> и отключает страницу справки HTTP и функцию GET языка описания веб-служб (WSDL), чтобы конечная точка метаданных не мешала конечной точке HTTP по умолчанию.
    >
    >  Добавление конечной точки, не являющейся конечной точкой SOAP, с URL-адресом "" приводит к непредвиденному поведению при попытке вызова операции на конечной точке. Причина этого заключается в том, что URI прослушивания конечной точки совпадает с универсальным кодом ресурса (URI) для страницы справки (страница, отображаемая при переходе по базовому адресу службы WCF).

     Это можно предотвратить любым из следующих способов.

    - Всегда указывать непустой код URI для конечной точки, не являющейся конечной точкой SOAP.

    - Отключить страницу справки. Это можно сделать с помощью следующего кода:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Откройте узел службы и подождите, пока пользователь не нажмет клавишу ВВОД.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     В этом образце показано, как разместить веб-службу с помощью консольного приложения. Также можно разместить эту службу в IIS. Для этого укажите класс <xref:System.ServiceModel.Activation.WebServiceHostFactory> в файле SVC, как показано в следующем коде.

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Вызов операций службы, сопоставленных с операцией GET, в Internet Explorer

1. Откройте Internet Explorer и введите " `http://localhost:8000/EchoWithGet?s=Hello, world!` " и нажмите клавишу ВВОД. URL-адрес содержит базовый адрес службы ( `http://localhost:8000/` ), относительный адрес конечной точки (""), операцию службы для вызова ("ечовисжет") и вопросительный знак, за которым следует список именованных параметров, разделенных амперсандом (&).

## <a name="to-call-service-operations-in-code"></a>Вызов операции службы в коде.

1. Создайте экземпляр класса <xref:System.ServiceModel.ChannelFactory%601> в блоке `using`.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Добавьте <xref:System.ServiceModel.Description.WebHttpBehavior> в конечную точку, вызываемую объектом <xref:System.ServiceModel.ChannelFactory%601>.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Создайте канал и вызовите службу.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Закройте объект <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Пример

Ниже приведен полный код этого примера.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Компиляция кода

При компиляции Service.cs обращается к файлам System.ServiceModel.dll и System.ServiceModel.Web.dll.

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Модель веб-программирования HTTP WCF](wcf-web-http-programming-model.md)
