---
title: Практическое руководство. Создание службы программным способом
description: Узнайте, как создать службу программным способом, самостоятельно настроив наследование и другие элементы инфраструктуры.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
ms.openlocfilehash: ab153b89272323a1a7a71181559f4f4eee082640
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270515"
---
# <a name="how-to-write-services-programmatically"></a>Практическое руководство. Создание службы программным способом

Если вы решили не использовать шаблон проекта "Служба Windows", для создания собственной службы вам придется настроить наследование и другие элементы инфраструктуры самостоятельно. Создавая службу программным способом, вам необходимо выполнить несколько действий, которые в случае с шаблоном выполняются автоматически.  
  
- Для класса службы необходимо настроить наследование от класса <xref:System.ServiceProcess.ServiceBase>.  
  
- Для проекта службы необходимо создать метод `Main`, который определяет запускаемые службы и вызывает для них метод <xref:System.ServiceProcess.ServiceBase.Run%2A>.  
  
- Необходимо переопределить процедуры <xref:System.ServiceProcess.ServiceBase.OnStart%2A> и <xref:System.ServiceProcess.ServiceBase.OnStop%2A> и добавить код, который они должны выполнять.  
  
### <a name="to-write-a-service-programmatically"></a>Создание службы программным способом  
  
1. Создайте пустой проект, а затем создайте ссылку на необходимые пространства имен.  
  
    1. В окне **Обозреватель решений** щелкните правой кнопкой мыши узел **Ссылки** и выберите пункт **Добавить ссылку**.  
  
    2. На вкладке **.NET Framework** найдите **System.dll** и щелкните **Выбрать**.  
  
    3. Найдите **System.ServiceProcess.dll** и щелкните **Выбрать**.  
  
    4. Нажмите кнопку **ОК**.  
  
2. Добавьте класс и настройте для него наследование от <xref:System.ServiceProcess.ServiceBase>.  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Настройте класс службы, добавив следующий код:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Создайте для класса метод `Main` и с его помощью определите службы, которые будет содержать класс. `userService1` — имя класса.  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Переопределите метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A> и укажите обработку, которая должна выполняться при запуске службы.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Переопределите все прочие методы, для которых нужно задать определенную обработку, и напишите код, благодаря которому служба будет понимать, что нужно делать в каждом случае.  
  
7. Добавить установщики, необходимые для приложения службы. Дополнительные сведения см. в разделе [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).  
  
8. Скомпилируйте проект, выбрав в меню **Сборка** пункт **Собрать решение**.  
  
    > [!NOTE]
    > Не нажимайте клавишу F5 для запуска проекта — таким способом нельзя запустить проект службы.  
  
9. Создайте проект установки и настраиваемые действия для установки службы. Пример см. в разделе [Пошаговое руководство. Создание приложения служб Windows в конструкторе компонентов](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Установите службу. Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>См. также

- [Знакомство с приложениями служб Windows](introduction-to-windows-service-applications.md)
- [Практическое руководство. Создание служб Windows](how-to-create-windows-services.md)
- [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md)
- [Практическое руководство. Запись сведений о службах в журнал](how-to-log-information-about-services.md)
- [Пошаговое руководство: Создание приложения служб Windows в конструкторе компонентов](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
