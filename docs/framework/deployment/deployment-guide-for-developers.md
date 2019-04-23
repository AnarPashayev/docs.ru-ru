---
title: Руководство по развертыванию .NET Framework для разработчиков
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f71cebc164e7b324dc847c67d3e0e49e856c11c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306538"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Руководство по развертыванию .NET Framework для разработчиков
В этом разделе приводятся сведения для разработчиков, которые планируют установить любую версию платформы с NET Framework 4.5 по [!INCLUDE[net_current](../../../includes/net-current-version.md)] вместе со своими приложениями.

Ссылки для загрузки см. в подразделе [Распространяемые пакеты](#redistributable-packages). Можно также загрузить перераспределяемые пакеты и языковые пакеты со следующих страниц Центра загрузки Microsoft:

- .NET Framework 4.7.2 для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=863262) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- .NET Framework 4.7.1 для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=852095) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET Framework 4.7 для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=825299) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=780597) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=671729) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/?LinkId=528222) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET Framework 4.5.2 для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/p/?LinkId=397703) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET Framework 4.5.1 для всех операционных систем ([веб-установщик](https://go.microsoft.com/fwlink/p/?LinkId=310158) или [автономный установщик](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Важные примечания:

> [!NOTE]
> Фраза "[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] и доработанные версии" относится к версии [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] и всем последующим версиям.

- Версии .NET Framework с [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] по [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] — это обновления на месте для [!INCLUDE[net_current](../../../includes/net-current-version.md)]. Это означает, что они используют ту же версию среды выполнения, но версии сборок обновлены и включают новые типы и члены.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] и ее точечные выпуски представляют собой инкрементные расширения возможностей [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. При установке [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или доработанных выпусков в системе, где уже установлена платформа [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], сборки версии 4 заменяются более новыми версиями.

- Если вы ссылаетесь на [внештатный пакет](../get-started/the-net-framework-and-out-of-band-releases.md) Майкрософт в своем приложении, сборка будет включена в пакет приложения.

- Для установки [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] и ее точечных выпусков требуются права администратора.

- Платформа [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] входит в состав [!INCLUDE[win8](../../../includes/win8-md.md)] и [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], поэтому развертывать ее вместе с приложением на этих операционных системах не нужно. Аналогично, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] входит в состав [!INCLUDE[win81](../../../includes/win81-md.md)] и Windows Server 2012 R2. Платформа .NET Framework 4.5.2 не включена ни в какую операционную систему. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] входит в состав Windows 10, [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] — в состав ноябрьского обновления Windows Update 10, [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] — в состав юбилейного обновления Windows 10 Anniversary Update.  .NET Framework 4.7 входит в состав обновления Windows 10 Creators Update, .NET Framework 4.7.1 — в состав Windows 10 Fall Creators Update, а .NET Framework 4.7.2 — в обновления Windows 10 за октябрь и за апрель 2018 г. Полный список требований к оборудованию и программному обеспечению см. в разделе [Требования к системе для .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- Начиная с [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]пользователи могут просматривать список запущенных приложений .NET Framework во время установки и легко закрывать их. Это помогает избежать перезапуска системы, вызываемого установкой .NET Framework. См. раздел [Уменьшение перезапусков системы](../../../docs/framework/deployment/reducing-system-restarts.md).

- При удалении [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или одного из вспомогательных выпусков этой платформы также удаляются более ранние файлы [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] . Если требуется вернуться к [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], необходимо переустановить приложение со всеми обновлениями. (См. раздел [Установка платформы .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).)

- Распространяемый пакет платформы .NET Framework 4.5 был обновлен 9 октября 2012 г., чтобы устранить проблему, связанную с неправильной отметкой времени в цифровом сертификате, которая вызывала преждевременное истечение срока действия цифровой подписи в файлах, создаваемых и подписываемых Microsoft. Если вы ранее установили распространяемый пакет платформы .NET Framework 4.5 от 16 августа 2012 г., рекомендуется обновить установленную копию до последнего распространяемого пакета из [Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=245484). Дополнительные сведения об этой проблеме см. в статье [Советы по безопасности (Microsoft) (2749655)](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

 Сведения о способах развертывания платформы .NET Framework и ее системных зависимостей по сети см. в разделе [Руководство по развертыванию для администраторов](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Варианты развертывания приложения
 Когда приложение готово к публикации на веб-сервере или в другом централизованном расположении, откуда пользователи смогут его устанавливать, можно выбрать один из нескольких методов развертывания. Некоторые из этих методов предусмотрены в Visual Studio. В таблице ниже перечислены варианты развертывания приложения с указанием распространяемого пакета .NET Framework, соответствующего каждому варианту. Помимо этого, можно написать для приложения собственную программу установки; дополнительные сведения см. в подразделе [Привязка установки .NET Framework к установке приложения](#chaining).

|Стратегия развертывания приложения|Доступные методы развертывания|Используемый распространяемый пакет .NET Framework|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Установка из Интернета|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Набор инструментов WiX](#wix)<br />- [Установка вручную](#installing_manually)|[Web installer](#redistributable-packages)|
|Установка с диска|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Набор инструментов WiX](#wix)<br />- [Установка вручную](#installing_manually)|[Offline installer](#redistributable-packages)|
|Установка из локальной сети (для корпоративных приложений)|- [ClickOnce](#clickonce-deployment)|[Веб-установщик](#redistributable-packages) (см. ограничения в [ClickOnce](#clickonce-deployment) ) или [автономный установщик](#redistributable-packages)|

## <a name="redistributable-packages"></a>Распространяемые пакеты
 Платформа .NET Framework доступна в виде двух распространяемых пакетов: веб-установщик (загрузчик) и автономный установщик (автономный распространяемый пакет). В следующей таблице приводится сравнение этих двух пакетов.

||веб-установщик|автономный установщик|
|-|-------------------|-----------------------|
|Файл загрузки|.NET Framework 4.7.2: <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4.7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Требуется подключение к интернету?|Да|Нет|
|Размер загрузки|Меньший (включает только установщик для целевой платформы) *|Больший*|
|Языковые пакеты|Включены**|[Устанавливаются отдельно](#chain_langpack), если только не используется пакет, предназначенный для всех ОС|
|Метод развертывания|Поддерживает все методы:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Установка вручную](#installing_manually)<br />- [Пользовательская установка (привязка)](#chaining)|Поддерживает все методы:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Установка вручную](#installing_manually)<br />- [Пользовательская установка (привязка)](#chaining)|
|Расположение загрузки для развертывания ClickOnce|Центр загрузки Майкрософт:<br /><br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Собственный сервер или Центр загрузки Майкрософт:<br /><br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Автономный установщик больше, так как он содержит компоненты для всех целевых платформ. По завершении работы программы установки операционная система Windows кэширует только использовавшийся установщик. Если удалить автономный установщик после установки, используемое место на диске будет таким же, как при использовании веб-установщика. Если средство, используемое для создания программы установки приложения (например, [InstallAware](#installaware-deployment) или [InstallShield](#installshield-deployment)), предусматривает папку для файлов установки, которая удаляется после установки, автономный установщик может быть удален автоматически путем помещения его в папку установки.

 ** При использовании веб-установщика с пользовательской установкой можно использовать параметры языка по умолчанию на основе заданного пользователем параметра многоязычного пользовательского интерфейса (MUI) или задать другой языковой пакет с помощью параметра `/LCID` в командной строке. Примеры см. в подразделе [Привязка с использованием пользовательского интерфейса .NET Framework по умолчанию](#chaining_default) .

## <a name="deployment-methods"></a>Методы развертывания
 Существует четыре метода развертывания:

- Можно задать зависимость от платформы .NET Framework. Указать платформу .NET Framework в качестве необходимого компонента при установке приложения можно одним из следующих способов:

    - использовать [развертывание ClickOnce](#clickonce-deployment) (предусмотрено в Visual Studio);

    - создать [проект InstallAware](#installaware-deployment) (бесплатный выпуск доступен для пользователей Visual Studio);

    - создать [проект InstallShield](#installshield-deployment) (предусмотрено в Visual Studio);

    - использовать [набор инструментов Windows Installer XML (WiX)](#wix).

- Можно предложить пользователям [установить .NET Framework вручную](#installing_manually).

- Можно привязать процесс установки .NET Framework к установке приложения (создать цепочку) и решить, как подойти к интерфейсу установки .NET Framework:

    - [использовать пользовательский интерфейс по умолчанию](#chaining_default)— дать установщику .NET Framework возможность предоставить свой пользовательский интерфейс;

    - [настроить пользовательский интерфейс](#chaining_custom) для представления унифицированного интерфейса установки, а также для отслеживания хода установки .NET Framework.

 Эти методы развертывания подробно рассмотрены в следующих подразделах.

## <a name="setting-a-dependency-on-the-net-framework"></a>Установка зависимости от .NET Framework
Если для развертывания приложения используется ClickOnce, InstallAware, InstallShield или WiX, можно добавить зависимость от .NET Framework, чтобы платформу можно было установить в ходе установки приложения.

### <a name="clickonce-deployment"></a>развертывание ClickOnce
 Развертывание ClickOnce доступно для проектов, созданных при помощи Visual Basic и Visual C#, но недоступно для Visual C++.

 Чтобы выбрать развертывание ClickOnce и добавить зависимость от .NET Framework, выполните в Visual Studio следующие действия.

1. Откройте проект приложения, который требуется опубликовать.

2. В обозревателе решений откройте контекстное меню своего проекта и выберите **Свойства**.

3. Выберите область **Публикация** .

4. Нажмите кнопку **Необходимые компоненты** .

5. Убедитесь, что в диалоговом окне **Необходимые компоненты** установлен флажок **Создать программу установки для необходимых компонентов** .

6. В списке необходимых компонентов найдите и выберите версию .NET Framework, которую вы использовали для сборки своего проекта.

7. Выберите вариант с указанием расположения источника для необходимых компонентов и нажмите кнопку **ОК**.

     При предоставлении URL-адреса в качестве расположения загрузки .NET Framework можно указать либо Центр загрузки Microsoft, либо свой сайт. При размещении распространяемого пакета на своем сервере этот пакет должен представлять собой автономный установщик, а не веб-установщик. Ссылку на веб-установщик можно дать только на Центр загрузки Microsoft. URL-адрес может также указывать диск, на котором распространяется приложение.

8. В диалоговом окне **Страницы свойств** выберите **ОК**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>Развертывание InstallAware
InstallAware позволяет создавать пакеты для приложения Windows (APPX), установщика Windows (MSI), машинного кода (EXE) и App-V (Application Virtualization) из одного источника. Вы можете легко [добавить любую версию .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) в установку. При необходимости настройте установку, [изменив скрипты по умолчанию](https://www.installaware.com/msicode.htm). Например, InstallAware предварительно устанавливает сертификаты в Windows 7, без которых установка .NET Framework 4.7 завершается сбоем. Дополнительные сведения об InstallAware см. на сайте [InstallAware для установщика Windows](https://www.installaware.com/).

### <a name="installshield-deployment"></a>Развертывание InstallShield
 Чтобы выбрать развертывание InstallShield и добавить зависимость от .NET Framework выполните в Visual Studio следующие действия.

1. В строке меню Visual Studio выберите **Файл**, **Создать**, **Проект**.

2. В левой области диалогового окна **Новый проект** выберите **Другие типы проектов**, **Установка и развертывание**, **InstallShield LE**.

3. В поле **Имя** введите имя для своего проекта и выберите **ОК**.

4. Если вы впервые создаете проект установки и развертывания, выберите **Go to InstallShield** (Перейти к InstallShield) или **Включение InstallShield Limited Edition**, чтобы скачать InstallShield Limited Edition для вашей версии Microsoft Visual Studio. Перезапустите Visual Studio.

5. Перейдите к мастеру **Помощник по проектам** и пункт **Файлы приложения** , чтобы добавить выходной элемент проекта. С помощью этого мастера можно настроить и другие атрибуты проекта.

6. Перейдите в окно **Требования установки** и выберите операционные системы и версию платформы .NET Framework, которую необходимо установить.

7. Откройте контекстное меню для проекта установки и выберите **Сборка**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Развертывание с помощью Windows Installer XML (WiX)
 Набор инструментов Windows Installer XML (WiX) собирает установочные пакеты Windows из исходного кода XML. WiX поддерживает среду командной строки, которая может быть интегрирована в процесс сборки для сборки пакетов установки MSI и MSM. С помощью WiX можно [указать .NET Framework в качестве необходимого компонента](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)или [создать формирователь цепочки](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) для полного управления развертыванием .NET Framework. Дополнительные сведения о WiX см. на веб-сайте [набора инструментов Windows Installer XML (WiX)](http://wixtoolset.org/) .

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Установка платформы .NET Framework вручную
 В некоторых случаях автоматически устанавливать .NET Framework вместе с приложением может быть нецелесообразно. В этом случае можно обязать пользователей установить платформу .NET Framework самостоятельно. Распространяемый пакет доступен в [двух пакетах](#redistributable-packages). В процессе установки дайте пользователям указания о том, как найти и установить .NET Framework.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Привязка установки .NET Framework к установке приложения
 При создании для приложения собственной программы установки можно привязать процесс установки .NET Framework к процессу установки приложения (создать цепочку). При привязке существует два варианта пользовательского интерфейса для установки .NET Framework:

- использование пользовательского интерфейса по умолчанию, предоставляемого установщиком .NET Framework;

- создание собственного пользовательского интерфейса для установки .NET Framework для единообразия с программой установки приложения.

 Оба метода позволяют использовать как веб-установщик, так и автономный установщик. У каждого пакета есть свои преимущества:

- при использовании веб-установщика процесс установки .NET Framework принимает решение, какой требуется установочный пакет, и загружает из Интернета и устанавливает только этот пакет;

- при использовании автономного установщика можно включить в распространяемый носитель полный набор пакетов установки .NET Framework, чтобы пользователям не нужно было во время установки загружать никакие дополнительные файлы из Интернета.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Привязка с использованием пользовательского интерфейса .NET Framework по умолчанию
 Чтобы автоматически привязать процесс установки .NET Framework и дать установщику платформы .NET Framework возможность предоставить пользовательский интерфейс, добавьте в свою программу установки следующую команду:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Например, если исполняемая программа — программа Contoso.exe и требуется автоматически установить автономный распространяемый пакет [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] , используйте следующую команду:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Можно использовать дополнительные параметры командной строки для настройки установки. Например:

- Чтобы предоставить пользователю возможность закрыть работающие приложения .NET Framework для минимизации перезапусков системы, установите пассивный режим и используйте параметр `/showrmui` следующим образом:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Эта команда позволяет диспетчеру перезапуска выводить окно сообщения, которое дает пользователям возможность закрыть приложения .NET Framework, прежде чем устанавливать платформу .NET Framework.

- При использовании веб-установщика можно использовать параметр `/LCID` для указания языкового пакета. Например, чтобы привязать веб-установщик [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] к программе установки Contoso и установить японский языковой пакет, добавьте в процесс установки приложения следующую команду:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Если параметр `/LCID` опущен, программа установки установит языковой пакет, соответствующий параметру MUI пользователя.

    > [!NOTE]
    > Даты выпусков языковых пакетов могут быть разными. Если требуемый языковой пакет отсутствует в центре загрузки, программа установки установит .NET Framework без языкового пакета. Если .NET Framework уже установлена на компьютере пользователя, программа установки установит только языковой пакет.

 Полный список параметров см. в подразделе [Параметры командной строки](#command-line-options) .

 Стандартные коды возврата см. в подразделе [Коды возврата](#return-codes) .

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Привязка с использованием настраиваемого пользовательского интерфейса
 При наличии собственного пакета установки может иметь смысл автоматически запускать и отслеживать установку .NET Framework, отображая при этом собственное представление хода выполнения установки. В этом случае убедитесь, что в вашем коде предусмотрено следующее:

- Проверка [требований к оборудованию и программному обеспечению для .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- [Определение](#detect_net) наличия нужной версии .NET Framework на компьютере пользователя.

    > [!IMPORTANT]
    > При определении наличия нужной версии платформы .NET Framework на компьютере следует проверить, установлена ли требуемая версия *или* более поздняя версия, а не установлена ли требуемая версия. Другими словами, следует определить следующее: раздел выпуска, полученный из реестра, больше или равен разделу выпуска требуемой версии, а *не* равен ли он разделу выпуска требуемой версии.

- [Определение](#detecting-the-language-packs) наличия нужных языковых пакетов на компьютере пользователя.

- Если требуется контроль над развертыванием, запустите процесс установки .NET Framework в автоматическом режиме и отслеживайте его (см. статью [Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- При развертывании автономного установщика [привяжите языковые пакеты отдельно](#chain_langpack).

- Настройка развертывания с помощью [параметров командной строки](#command-line-options). Например, если при привязке веб-установщика .NET Framework требуется переопределить языковый пакет по умолчанию, используйте параметр `/LCID` , как описано в предыдущем подразделе.

- [Устранение неполадок](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Обнаружение .NET Framework
 Если установка выполнена успешно, установщик .NET Framework записывает разделы реестра. Можно узнать, какая версия установлена ([!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или более поздняя), проверив папку `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` в реестре на наличие значения `DWORD` с именем `Release`. (Обратите внимание, что папка "NET Framework Setup" не начинается с точки.) Наличие данного раздела указывает, что на компьютере установлена [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или более поздняя версия. Значение `Release` показывает, какая версия .NET Framework установлена.

> [!IMPORTANT]
> При попытке определить наличие конкретной версии необходимо проверить значение,  **большее или равное** значению ключевого слова release.

|Версия|Значение DWORD "Release"|
|-------------|--------------------------------|
|Платформа .NET Framework 4.7.2, установленная в Windows 10 с обновлением за апрель 2018 г. и в Windows Server, версия 1803|461808|
|Платформа .NET Framework 4.7.2, установленная на остальных версиях ОС, кроме Windows 10 с обновлением за апрель 2018 г. и Windows Server, версия 1803. Сюда также относится обновление Windows 10 за октябрь 2018 г. |461814|
|Платформа .NET Framework 4.7.1, установленная в Windows 10 Fall Creators Update и в Windows Server, версия 1709|461308|
|Платформа .NET Framework 4.7.1, установленная на остальных версиях ОС, кроме Windows 10 Fall Creators Update и Windows Server, версия 1709|461310|
|.NET Framework 4.7 установлена в обновлении Windows 10 Creators Update|460798|
|.NET Framework 4.7 установлена во всех версиях ОС, за исключением обновления Windows 10 Creators Update|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] установлена в выпуске Windows 10 Anniversary Edition и Windows Server 2016|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] установлена во всех версиях операционной системы, отличных от Windows 10 Anniversary Edition и Windows Server 2016|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] установлено в Windows 10 с ноябрьским обновлением|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] установлена во всех версиях ОС, за исключением Windows 10 с ноябрьским обновлением|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] установлена в Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] установлена во всех версиях операционной системы, отличных от Windows 10|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] устанавливается вместе с [!INCLUDE[win81](../../../includes/win81-md.md)] или Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] устанавливается в [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Обнаружение языковых пакетов
 Проверить, установлен ли указанный языковой пакет, можно, проверив папку HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* реестра на наличие значения DWORD с именем `Release`. (Обратите внимание, что папка "NET Framework Setup" не начинается с точки.) Параметр *LCID* задает код языка; список кодов см. на странице [поддерживаемых языков](#supported-languages).

 Например, чтобы проверить, установлен ли уже японский полный языковой пакет (LCID=1041), проверьте следующие значения в реестре:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Чтобы определить, установлен ли окончательный выпуск языкового пакета для определенной версии .NET Framework с 4.5 по 4.7.2, проверьте значение DWORD раздела RELEASE, описанное в предыдущем разделе ([Обнаружение .NET Framework](#detect_net)).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Привязка языковых пакетов к установке приложения
 Платформа .NET Framework предоставляет набор автономных исполняемых файлов языковых пакетов, содержащих локализованные ресурсы для конкретных языков и региональных параметров. Эти пакеты можно загрузить в центре загрузки корпорации Майкрософт:

- [Языковые пакеты .NET Framework 4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863258)

- [Языковые пакеты .NET Framework 4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Языковые пакеты .NET Framework 4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [Языковые пакеты .NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [Языковые пакеты .NET Framework 4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Языковые пакеты .NET Framework 4.6](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [Языковые пакеты .NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [Языковые пакеты .NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Языковые пакеты .NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Языковые пакеты не содержат компоненты платформы .NET Framework, необходимые для запуска приложения, поэтому перед установкой языкового пакета необходимо установить .NET Framework с помощью веб-установщика или автономного установщика.

 Начиная с [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], имена пакетов имеют вид NDP <`version`>-KB<`number`>-x86-x64-AllOS-<`culture`>.exe, где `version` — номер версии платформы .NET Framework, `number` — номер статьи базы знаний Майкрософт, а `culture` означает [страну или регион](#supported-languages). Пример одного из этих пакетов — `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Имена пакетов, перечислены в разделе [Redistributable Packages](#redistributable-packages) ранее в этой статье.

 Чтобы установить языковой пакет с помощью автономного установщика .NET Framework , необходимо привязать его к установке приложения. Например, для развертывания автономного установщика [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] с японским языковым пакетом используйте следующую команду:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>
```

 Привязывать языковые пакеты при использовании веб-установщика не обязательно: программа установки установит языковой пакет, соответствующий параметру MUI пользователя. Если требуется установить другой язык, можно использовать параметр `/LCID` для задания языкового пакета.

 Полный список параметров командной строки см. в подразделе [Параметры командной строки](#command-line-options) .

### <a name="troubleshooting"></a>Устранение неполадок

#### <a name="return-codes"></a>Коды возврата
 В следующей таблице перечислены наиболее распространенные коды возврата установщика распространяемого пакета .NET Framework. Коды возврата одинаковы для всех версий установщика. Ссылки на подробные сведения см. в следующем подразделе.

|Код возврата|Описание:|
|-----------------|-----------------|
|0|Установка успешно завершена.|
|1602|Установка отменена пользователем.|
|1603|Во время установки произошла неустранимая ошибка.|
|1641|Для завершения установки необходима перезагрузка. Сообщение указывает на успешное завершение действия.|
|3010|Для завершения установки необходима перезагрузка. Сообщение указывает на успешное завершение действия.|
|5100|Компьютер пользователя не отвечает системным требованиям.|

#### <a name="download-error-codes"></a>Коды ошибок загрузки
 Ознакомьтесь со следующими ресурсами:

- [Коды ошибок Background Intelligent Transfer Service (BITS)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Коды ошибок моникера URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Коды ошибок WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Другие коды ошибок
 Ознакомьтесь со следующими ресурсами:

- [Коды ошибок установщика Windows](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Коды результатов агента обновления Windows](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Удаление .NET Framework
 Начиная с [!INCLUDE[win8](../../../includes/win8-md.md)] удалить платформу [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или одну из ее доработанных версий можно с помощью пункта **Включение или отключение компонентов Windows** на панели управления. В более ранних версиях Windows удалить платформу [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или одну из ее доработанных версий можно с помощью пункта **Установка и удаление программ** на панели управления.

> [!IMPORTANT]
> Для Windows 7 и более ранних операционных систем при удалении [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 или 4.7.2 файлы [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] не восстанавливаются, как и при удалении [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] не восстанавливаются файлы [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Чтобы вернуться к более старой версии, необходимо переустановить платформу со всеми обновлениями.

## <a name="appendix"></a>Приложение

### <a name="command-line-options"></a>Параметры командной строки
 В следующей таблице перечислены параметры, которые можно использовать при связывании распространяемого пакета [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] с программой установки приложения.

|Параметр|Описание|
|------------|-----------------|
|**/CEIPConsent**|Перезаписывает поведение по умолчанию и отправляет анонимные сведения об установке в корпорацию Microsoft для совершенствования процедуры развертывания в будущем. Этот параметр можно использовать, только если программа установки запрашивает согласие пользователя и только если пользователь разрешает отправлять анонимную статистку в корпорацию Microsoft.|
|**/chainingpackage** `packageName`|Указывает имя исполняемого файла, осуществляющего привязку. Эти сведения отправляются в корпорацию Microsoft в качестве анонимной статистики для совершенствования процедуры развертывания в будущем.<br /><br /> Если в имени пакета присутствуют пробелы, в качестве разделителей необходимо использовать двойные кавычки (например, **/chainingpackage "Lucerne Publishing"**). Пример привязываемого пакета см. в разделе [Getting Progress Information from an Installation Package](https://go.microsoft.com/fwlink/?LinkId=181926) в библиотеке MSDN.|
|**/LCID**  `LCID`<br /><br /> где параметр `LCID` задает код языка (список кодов см. на странице [поддерживаемых языков](#supported-languages)).|Устанавливает языковой пакет, определенный параметром `LCID` , и обеспечивает принудительное отображение пользовательского интерфейса на этом языке (если не включен автоматический режим).<br /><br /> Для веб-установщика этот параметр обеспечивает установку (привязку) языкового пакета из Интернета. **Примечание.**  Используйте этот параметр только с веб-установщиком.|
|**/log** `file` &#124; `folder`|Задает расположение файла журнала. Значение по умолчанию — временная папка для процесса, а имя файла по умолчанию основано на пакете. Если файл имеет расширение .txt, создается текстовый журнал. Если указано любое другое расширение или никакого расширения, создается журнал в формате HTML.|
|**/msioptions**|Задает параметры для передачи элементам MSI и MSP; например: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Запрещает программе установки автоматически перезагружать компьютер. При использовании этого параметра привязываемое приложение должно захватить код возврата и обработать перезагрузку (см. раздел [Получение сведений о ходе выполнения из пакета установки](https://go.microsoft.com/fwlink/?LinkId=179606) в библиотеке MSDN).|
|**/passive**|Задает пассивный режим. Отображает индикатор выполнения, чтобы показать, что установка выполняется, но не выводит никаких приглашений и сообщений об ошибках. В этом режиме, при объединении в цепочку с программой установки, привязываемый пакет должен обрабатывать [коды возврата](#return-codes).|
|**/pipe**|Создает канал связи, чтобы привязываемый пакет мог получать информацию о ходе выполнения.|
|**/promptrestart**|Только пассивный режим; если программе установки необходима перезагрузка, она выводит соответствующий запрос для пользователя. При использовании этого параметра требуется вмешательство пользователя, если необходима перезагрузка.|
|**/q**|Включает автоматический режим.|
|**/repair**|Включение функции исправления.|
|**/serialdownload**|Обеспечивает, что установка происходит только после загрузки пакета.|
|**/showfinalerror**|Задает пассивный режим. Отображает ошибки только в том случае, если установка не выполнена успешно. При использовании этого параметра в случае ошибки установки требуется вмешательство пользователя.|
|**/showrmui**|Используется только с параметром **/passive** . Выводит окно сообщения, в котором пользователю предлагается закрыть работающие в данный момент приложения .NET Framework. Это окно сообщения ведет себя одинаково как в пассивном, так и не в пассивном режиме.|
|**/uninstall**|Удаляет распространяемый пакет .NET Framework.|

### <a name="supported-languages"></a>Поддерживаемые языки
В следующей таблице перечислены языковые пакеты .NET Framework, доступные для платформы [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] и ее точечных выпусков.

|LCID|Язык — страна/регион|culture|
|----------|--------------------------------|-------------|
|1025|Арабский — Саудовская Аравия|ar|
|1028|Китайский (традиционное письмо)|zh-Hant|
|1029|Чешский|cs|
|1030|Датский|da|
|1031|Немецкий (Германия)|de|
|1032|Греческий|el|
|1035|Финский|fi|
|1036|Французский (Франция)|fr|
|1037|Иврит|he|
|1038|Венгерский|hu|
|1040|Итальянский (Италия)|it|
|1041|Японский|ja|
|1042|Корейский|ko|
|1043|Голландский (Нидерланды)|nl|
|1044|Норвежский (Букмол)|Нет|
|1045|Польский|pl|
|1046|Португальский (Бразилия)|pt-BR|
|1049|Русский|ru|
|1053|Шведский|sv|
|1055|Турецкий|tr|
|2052|Китайский (упрощенное письмо)|zh-Hans|
|2070|Португальский (Португалия)|pt-PT|
|3082|Испанский (Испания, современная сортировка)|es|

## <a name="see-also"></a>См. также

- [Руководство по развертыванию для администраторов](../../../docs/framework/deployment/guide-for-administrators.md)
- [Требования к системе](../../../docs/framework/get-started/system-requirements.md)
- [Установка .NET Framework для разработчиков](../../../docs/framework/install/guide-for-developers.md)
- [Устранение неполадок с заблокированными установками и удалениями .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Уменьшение числа перезагрузок при установке платформы .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)
- [Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
