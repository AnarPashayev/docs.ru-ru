---
title: Пример FindPrivateKey - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490771"
---
# <a name="findprivatekey-sample"></a>Пример FindPrivateKey

Определение расположения и имени файла закрытого ключа, связанного с заданным сертификатом X.509, в хранилище сертификатов может представлять собой достаточно сложную задачу. Средство FindPrivateKey.exe упрощает этот процесс.

> [!IMPORTANT]
> FindPrivateKey - это образец, который необходимо скомпилировать перед началом использования. См. в разделе [для сборки проекта FindPrivateKey](#to-build-the-findprivatekey-project) разделе приведены инструкции о том, как построить инструмент FindPrivateKey.

Сертификаты X.509 устанавливаются администратором или любым пользователем компьютера. Тем не менее сертификат может осуществляться службой, запущенной с другой учетной записью. Например запись СЕТЕВОЙ службы.

У такой учетной записи может не быть доступа к файлу закрытого ключа, поскольку изначально сертификат был установлен другой учетной записью. Средство FindPrivateKey позволяет определить расположение файла закрытого ключа заданного сертификата X.509. Если расположение файла закрытого ключа заданного сертификата X.509 известно, можно добавлять или удалять разрешения на доступ к этому файлу.

Примеры, которые используют сертификаты для безопасности используют средство FindPrivateKey в *Setup.bat* файл. После обнаружения файла закрытого ключа, можно использовать другие средства, такие как *Cacls.exe* присвоить достаточные права доступа на файл.

При выполнении службы Windows Communication Foundation (WCF) с учетной записью пользователя, например резидентно размещенного исполняемого файла, убедитесь, что учетная запись имеет доступ только для чтения к файлу. При выполнении службы WCF в группе Internet Information Services (IIS) учетные записи по умолчанию, которые служба будет выполняться, NETWORK SERVICE в IIS 7 и более ранних версий или удостоверение пула приложений IIS 7.5 и более поздними версиями. Дополнительные сведения см. в разделе [удостоверения пула приложений](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Примеры

При доступе к сертификат, для которого у процесса нет права на чтения, появится сообщение об исключении примерно в следующем примере:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

В этом случае использовать средство FindPrivateKey найти файл закрытого ключа и задайте права доступа для процесса, под которой работает служба. Например это можно сделать с помощью средства Cacls.exe, как показано в следующем примере:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Построение проекта FindPrivateKey

Чтобы загрузить проект, посетите [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Откройте проводник и перейдите к *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* папку в каталоге, где установлен пример.

2. Дважды щелкните значок файла с расширением SLN, чтобы открыть файл в Visual Studio.

3. В **построения** меню, выберите **Перестроить решение**.

4. Построении решения создается файл: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Соглашения-записи командной строки

 «[*параметр*]» представляет необязательный набор параметров.

 «{*параметр*}» представляет обязательный набор параметров.

 "*параметр1* &#124; *параметр2*" представляет выбор между наборами параметров.

 "\<*значение*>» представляет значение параметра ввода.

## <a name="usage"></a>Использование

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Где:

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Если параметры не указаны в командной строке, то отображается этот текст справки.

## <a name="examples"></a>Примеры

Этот пример находит имя файла сертификата с именем субъекта «CN = localhost», в личном хранилище текущего пользователя.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Этот пример находит имя файла сертификата с именем субъекта «CN = localhost», в личное хранилище текущего пользователя и выходные данные полный путь к каталогу.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Этот пример находит имя файла сертификата с отпечатком "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" в хранилище "Личное" на локальном компьютере.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
