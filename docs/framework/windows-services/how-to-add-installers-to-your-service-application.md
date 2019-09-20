---
title: Практическое руководство. Добавление установщиков в приложение-службу
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: 99e2376c50f0b47cc21002b2926818707188805e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053655"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Практическое руководство. Добавление установщиков в приложение-службу
В состав Visual Studio входят компоненты установки, которые могут устанавливать ресурсы, связанные с приложениями-службами. Компоненты установки регистрируют отдельную службу в целевой системе и сообщают диспетчеру служб об этой службе. При работе с приложением-службой можно выбрать ссылку в окне свойств для автоматического добавления соответствующих установщиков в проект.  
  
> [!NOTE]
> Значения свойств для службы копируются из класса службы в класс установщика. Обновляемые значения свойств в классе службы не обновляются автоматически в установщике.  
  
 При добавлении установщика в проект в нем создается класс (который по умолчанию называется `ProjectInstaller`), а в нем создаются экземпляры соответствующих компонентов установки. Этот класс служит центральной точкой для всех компонентов установки, которые требуются для проекта. Например, если добавить в приложение вторую службу и щелкнуть ссылку "Добавить установщик", второй класс установщика не будет создан. Вместо этого в существующий класс будет добавлен дополнительный необходимый компонент установки для второй службы.  
  
 Вам не нужно добавлять специальный код в установщики, чтобы обеспечить правильную установку службы. Тем не менее иногда может потребоваться изменить содержимое установщиков, если вам нужно добавить специальные функции в процесс установки.  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Добавление установщиков в приложение-службу  
  
1. В **обозревателе решений** откройте **конструктор** для службы, в которую нужно добавить компонент установки.  
  
2. Щелкните фон конструктора, чтобы выбрать саму службу, а не один из ее элементов.  
  
3. Щелкните правой кнопкой мыши в активном окне конструктора и выберите команду **Добавить установщик**.  
  
     В проект будут добавлены новый класс `ProjectInstaller` и два компонента установки <xref:System.ServiceProcess.ServiceProcessInstaller> и <xref:System.ServiceProcess.ServiceInstaller>, в которые будут скопированы значения свойств для службы.  
  
4. Щелкните компонент <xref:System.ServiceProcess.ServiceInstaller> и убедитесь, что для свойства <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> задано то же значение, что и для свойства <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> в службе.  
  
5. Чтобы определить, как будет запущена служба, щелкните компонент <xref:System.ServiceProcess.ServiceInstaller> и задайте для свойства <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> соответствующее значение.  
  
    |Значение|Результат|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Служба должна быть запущена вручную после установки. Дополнительные сведения см. в разделе [Практическое руководство. Запуск служб](how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Служба будет запускаться сама при перезагрузке компьютера.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Запуск службы невозможен.|  
  
6. Чтобы определить контекст безопасности, в котором будет запущена служба, щелкните компонент <xref:System.ServiceProcess.ServiceProcessInstaller> и задайте соответствующие значения свойств. Дополнительные сведения см. в разделе [Практическое руководство. Назначение службам контекста безопасности](how-to-specify-the-security-context-for-services.md).  
  
7. Переопределите все методы, для которых нужно выполнить дополнительную обработку.  
  
8. Повторите шаги 1–7 для каждой дополнительной службы в проекте.  
  
    > [!NOTE]
    > Для каждой дополнительной службы в проекте необходимо добавить в класс `ProjectInstaller` проекта дополнительный компонент <xref:System.ServiceProcess.ServiceInstaller>. Компонент <xref:System.ServiceProcess.ServiceProcessInstaller>, добавленный на шаге 3, работает со всеми отдельными установщиками служб в проекте.  
  
## <a name="see-also"></a>См. также

- [Знакомство с приложениями служб Windows](introduction-to-windows-service-applications.md)
- [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md)
- [Практическое руководство. Запуск служб](how-to-start-services.md)
- [Практическое руководство. Назначение службам контекста безопасности](how-to-specify-the-security-context-for-services.md)
