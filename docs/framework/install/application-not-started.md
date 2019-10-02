---
title: Устранение неполадок при получении сообщения "Не удалось запустить это приложение"
description: Сведения о том, что делать, если отображается сообщение "Не удалось запустить это приложение".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401284"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Устранение неполадок при получении сообщения об ошибке "Не удалось запустить это приложение"

Для приложений, разработанных для .NET Framework, обычно требуется, чтобы на компьютере была установлена определенная версия .NET Framework. В некоторых случаях вы можете попытаться запустить приложение без установленной или ожидаемой версии .NET Framework. В результате этого часто выводится примерно такое диалоговое окно с сообщением об ошибке:

![Не удалось запустить это приложение.](media/application-not-started/app-could-not-be-started.png)

Это указывает на то, что выполняется одно из следующих условий:

- установка .NET Framework в системе повреждена;

- не удалось обнаружить версию .NET Framework, необходимую для приложения.

Чтобы устранить эту проблему и запустить приложение, сделайте следующее:

1. Скачайте [средство восстановления .NET Framework (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). Средство запускается автоматически после завершения скачивания.

1. Если средство восстановления .NET Framework рекомендует какое-либо дополнительное действие, подобное показанному на следующем рисунке, нажмите кнопку **Далее**.

   ![Рекомендованные изменения](media/application-not-started/repair-tool-recommended-changes.png)

1. В средстве восстановления .NET Framework отображается диалоговое окно, показанное на следующем рисунке, в котором указано, что изменения внесены. Не закрывайте диалоговое окно, пока выполняется повторная попытка запуска приложения. Запуск должен быть выполнен успешно, если средство восстановления .NET Framework обнаружило и устранило поврежденную установку .NET Framework.

   ![Рекомендованные изменения](media/application-not-started/repair-tool-changes-complete.png)

1. Если приложение успешно запускается, нажмите кнопку **Готово**. В противном случае нажмите кнопку **Далее**.

1. Если вы нажали кнопку **Далее**, в средстве восстановления .NET Framework отобразится диалоговое окно, как показано ниже. Нажмите кнопку **Готово**, чтобы отправить диагностические данные в корпорацию Майкрософт.

   ![Не удалось устранить проблему](media/application-not-started/repair-tool-no-resolution.png)

1. Если по-прежнему не удается запустить приложение, установите последнюю версию .NET Framework, поддерживаемую вашей версией Windows, как показано в следующей таблице.

   |Версия Windows|Установка .NET Framework|
   |---|---|
   |Юбилейное обновление Windows 10 или более поздние версии|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 с обновлением за ноябрь|[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345)|
   |Windows 8.1|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)|
   |Windows 7 SP1|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  .NET Framework 4.8, предустановленная в Windows 10 с обновлением за май 2019 г.

1. Попытайтесь запустить приложение.

1. В некоторых случаях отображается диалоговое окно, подобное приведенному ниже, с приглашением установить платформу .NET Framework 3.5. Выберите **Скачать и установить этот компонент**, чтобы установить .NET Framework 3.5, а затем запустите приложение еще раз.

   ![Не удалось устранить проблему](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>См. также

- [Требования к системе для .NET Framework](../get-started/system-requirements.md)
- [Руководство по установке .NET Framework](index.md)
- [Устранение неполадок с заблокированными установками и удалениями .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
