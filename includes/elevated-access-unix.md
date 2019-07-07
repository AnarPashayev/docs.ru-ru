---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540121"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="a9dff-101">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="a9dff-101">Install the global tool</span></span>

<span data-ttu-id="a9dff-102">Ресурсы пакета следует установить в защищенном расположении с помощью параметра `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a9dff-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="a9dff-103">Это позволяет изолировать среду пользователя с ограниченным доступом от среды с повышенными правами.</span><span class="sxs-lookup"><span data-stu-id="a9dff-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="a9dff-104">`/usr/local/share/dotnet-tools` создается с разрешением `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="a9dff-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="a9dff-105">Если каталог уже существует, используйте команду `ls -l`, чтобы убедиться в том, что у пользователя с ограниченным доступом нет разрешения на изменение каталога.</span><span class="sxs-lookup"><span data-stu-id="a9dff-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="a9dff-106">Если такое разрешение есть, запретите доступ с помощью команды `sudo chmod o-w -R /usr/share/dotnet-tools`.</span><span class="sxs-lookup"><span data-stu-id="a9dff-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="a9dff-107">Запуск глобального средства</span><span class="sxs-lookup"><span data-stu-id="a9dff-107">Run the global tool</span></span>

<span data-ttu-id="a9dff-108">**Способ 1**. Используйте полный путь с sudo:</span><span class="sxs-lookup"><span data-stu-id="a9dff-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="a9dff-109">**Способ 2**. Добавьте символьную ссылку на средство (одна на средство):</span><span class="sxs-lookup"><span data-stu-id="a9dff-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="a9dff-110">Запустите средство с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="a9dff-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="a9dff-111">Удаление глобального средства</span><span class="sxs-lookup"><span data-stu-id="a9dff-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="a9dff-112">Если вы добавили символьную ссылку, ее также нужно удалить:</span><span class="sxs-lookup"><span data-stu-id="a9dff-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
