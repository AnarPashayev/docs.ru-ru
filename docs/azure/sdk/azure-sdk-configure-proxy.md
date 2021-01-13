---
title: Настройка прокси-сервера при использовании пакета Azure SDK для .NET
description: Определение прокси-сервера для пакета Azure SDK для .NET с использованием переменных среды HTTP[S]_PROXY
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700952"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a>Настройка прокси-сервера при использовании пакета Azure SDK для .NET

Если вашей организации требуется использовать прокси-сервер для доступа к ресурсам в Интернете, для использования пакета Azure SDK для .NET необходимо настроить переменную среды со сведениями о прокси-сервере.  

## <a name="configuration-using-environment-variables"></a>Настройка с использованием переменных среды

В зависимости от того, использует ли прокси-сервер протокол HTTP или HTTPS, необходимо настраивать соответственно переменную среды `HTTP_PROXY` или `HTTPS_PROXY`. URL-адрес прокси сервера имеет вид `http[s]://[username:password@]<ip_address_or_hostname>:<port>/`, где комбинация `username:password` является необязательной. IP-адрес или имя узла, номер порта и учетные данные для прокси-сервера вы можете получить у администратора сети.

В следующих примерах показано, как настроить соответствующие переменные среды в средах командной оболочки (Windows) и bash (Linux/Mac).  После настройки соответствующей переменной среды пакет Azure SDK для .NET будет использовать прокси-сервер во время выполнения.

### <a name="cmd"></a>[cmd](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[bash](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
