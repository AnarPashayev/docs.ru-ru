---
title: Средство поиска закрытых ключей (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929588"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Средство поиска закрытых ключей (FindPrivateKey.exe)

Эта программа командной строки предназначена для извлечения закрытого ключа из хранилища сертификатов. Например *FindPrivateKey.exe* можно использовать для определения расположения и имя файла закрытого ключа, связанного с конкретным сертификатом X.509 в хранилище сертификатов.

> [!IMPORTANT]
> Средство FindPrivateKey поставляется в качестве образца WCF. Дополнительные сведения о где найти образец и как создавать его, см. в разделе [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Синтаксис

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Примечания

В следующих таблицах описаны аргументы и параметры, которые можно использовать со средством Find Private Key (FindPrivateKey.exe).

|Аргумент|Описание|
|--------------|-----------------|
|`storeName`|Имя хранилища сертификатов.|
|`storeLocation`|Расположение хранилища сертификатов.|

|Параметр|Описание|
|------------|-----------------|
|`/n <` *Имя субъекта* `>`|Задает имя субъекта сертификата.|
|`/t <` *отпечаток* `>`|Задает отпечаток сертификата. Используйте Certmgr.exe для извлечения отпечатка сертификата.|
|`/f`|Выводит только имя файла.|
|`/d`|Выводит только каталог.|
|`/a`|Выводит абсолютное имя файла.|

## <a name="examples"></a>Примеры

Следующая команда извлекает закрытый ключ для John Doe:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Следующая команда извлекает закрытый ключ для локального компьютера:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```