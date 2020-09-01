---
description: -publicsign (параметры компилятора C#)
title: -publicsign (параметры компилятора C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124816"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="977d0-103">-publicsign (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="977d0-103">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="977d0-104">Этот параметр указывает компилятору на необходимость применения открытого ключа, но фактически не подписывает сборку.</span><span class="sxs-lookup"><span data-stu-id="977d0-104">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="977d0-105">Кроме того, параметр **-publicsign** задает в сборке бит, который сообщает среде выполнения, что файл подписан.</span><span class="sxs-lookup"><span data-stu-id="977d0-105">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="977d0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="977d0-106">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="977d0-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="977d0-107">Arguments</span></span>

<span data-ttu-id="977d0-108">Нет.</span><span class="sxs-lookup"><span data-stu-id="977d0-108">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="977d0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="977d0-109">Remarks</span></span>

<span data-ttu-id="977d0-110">С параметром **-publicsign** необходимо использовать параметр [-keyfile](keyfile-compiler-option.md) или [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="977d0-110">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="977d0-111">Каждый из параметров **keyfile** и **keycontainer** определяет открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="977d0-111">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="977d0-112">Параметры **-publicsign** и **-delaysign** — взаимоисключающие.</span><span class="sxs-lookup"><span data-stu-id="977d0-112">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="977d0-113">При таком подписывании в сборку добавляется открытый ключ. Кроме того, в сборке устанавливается флаг "подписано", хотя фактически сборка не подписывается закрытым ключом. Такой подход иногда называют "фиктивным подписыванием" или "подписыванием OSS".</span><span class="sxs-lookup"><span data-stu-id="977d0-113">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="977d0-114">Он полезен на проектах с открытым исходным кодом: людям нужно создавать сборки, которые будут совместимы с выпущенными "полностью подписанными" сборками, но у них нет доступа к закрытому ключу, который использовался для подписывания сборок.</span><span class="sxs-lookup"><span data-stu-id="977d0-114">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="977d0-115">Так как потребителям практически никогда не нужно проверять, полностью ли подписана сборка, создаваемые сообществами сборки можно использовать практические во всех случаях, в которых может использоваться полностью подписанная сборка.</span><span class="sxs-lookup"><span data-stu-id="977d0-115">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="977d0-116">Установка параметра компилятора в CSPROJ-файле</span><span class="sxs-lookup"><span data-stu-id="977d0-116">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="977d0-117">Откройте CSPROJ-файл проекта и добавьте следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="977d0-117">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="977d0-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="977d0-118">See also</span></span>

- [<span data-ttu-id="977d0-119">-delaysign (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="977d0-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="977d0-120">-keyfile (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="977d0-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="977d0-121">-keycontainer (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="977d0-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="977d0-122">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="977d0-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="977d0-123">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="977d0-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
