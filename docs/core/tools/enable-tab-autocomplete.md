---
title: Включение автодополнения клавишей TAB
description: В этой статье объясняется, как включить автодополнение клавишей TAB для .NET Core CLI в средах PowerShell, Bash и zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 0f29ba2ef1d419339a0e2dc44f67c93b326eb40d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182455"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="102fa-103">Автодополнение клавишей TAB для .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="102fa-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="102fa-104">Начиная с пакета SDK для .NET Core 2.0 среда .NET Core CLI поддерживает автодополнение по нажатию клавиши TAB.</span><span class="sxs-lookup"><span data-stu-id="102fa-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="102fa-105">В этой статье описывается, как включить автодополнение нажатием клавиши TAB для трех оболочек: PowerShell, Bash и zsh.</span><span class="sxs-lookup"><span data-stu-id="102fa-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="102fa-106">Другие оболочки могут иметь поддержку автодополнения.</span><span class="sxs-lookup"><span data-stu-id="102fa-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="102fa-107">Чтобы узнать, как настроить автодополнение, ознакомьтесь с документацией к этим оболочкам; использование автодополнения будет аналогичным, описанному в этой статье.</span><span class="sxs-lookup"><span data-stu-id="102fa-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="102fa-108">После установки автодополнение клавишей TAB для .NET Core CLI можно активировать, введя в командной строке `dotnet` и нажав клавишу TAB.</span><span class="sxs-lookup"><span data-stu-id="102fa-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="102fa-109">Текущая командная строка будет передана команде `dotnet complete`, а оболочка обработает результаты.</span><span class="sxs-lookup"><span data-stu-id="102fa-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="102fa-110">Вы можете проверить результаты без активации автодополнения клавишей TAB, передав что-либо непосредственно команде `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="102fa-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="102fa-111">Например:</span><span class="sxs-lookup"><span data-stu-id="102fa-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="102fa-112">Если команда не сработала, убедитесь, что установлен пакет SDK для .NET Core 2.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="102fa-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="102fa-113">Если он установлен, но команда все равно не работает, проверьте, что команда `dotnet` разрешается как минимум в версию пакета SDK для .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="102fa-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="102fa-114">Воспользуйтесь командой `dotnet --version`, чтобы узнать, к которой версии `dotnet` указывает текущий путь.</span><span class="sxs-lookup"><span data-stu-id="102fa-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="102fa-115">Дополнительные сведения см. в статье [Выбор версии .NET Core для использования](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="102fa-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="102fa-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="102fa-116">Examples</span></span>

<span data-ttu-id="102fa-117">Ниже приведено несколько примеров возможностей, которые предоставляет автодополнение клавишей TAB:</span><span class="sxs-lookup"><span data-stu-id="102fa-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="102fa-118">Входные данные</span><span class="sxs-lookup"><span data-stu-id="102fa-118">Input</span></span>                                | <span data-ttu-id="102fa-119">becomes</span><span class="sxs-lookup"><span data-stu-id="102fa-119">becomes</span></span>                                                                     | <span data-ttu-id="102fa-120">because</span><span class="sxs-lookup"><span data-stu-id="102fa-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="102fa-121">`add` является первой подкомандой в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="102fa-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="102fa-122">При автодополнении клавишей TAB подстроки сопоставляются и первой по алфавиту является `--help`.</span><span class="sxs-lookup"><span data-stu-id="102fa-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="102fa-123">После второго нажатия клавиши TAB подставляется следующее предложение.</span><span class="sxs-lookup"><span data-stu-id="102fa-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="102fa-124">Результаты возвращаются в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="102fa-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="102fa-125">Автодополнение клавишей TAB зависит от файла проекта.</span><span class="sxs-lookup"><span data-stu-id="102fa-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="102fa-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="102fa-126">PowerShell</span></span>

<span data-ttu-id="102fa-127">Чтобы добавить автодополнение клавишей TAB для .NET Core CLI в **PowerShell**, создайте или измените профиль, хранящийся в переменной `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="102fa-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="102fa-128">Дополнительные сведения см. в разделах [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) (Как создать свой профиль) и [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) (Профили и политика выполнения).</span><span class="sxs-lookup"><span data-stu-id="102fa-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="102fa-129">Добавьте в свой профиль представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="102fa-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="102fa-130">Bash</span><span class="sxs-lookup"><span data-stu-id="102fa-130">Bash</span></span>

<span data-ttu-id="102fa-131">Чтобы добавить автодополнение клавишей TAB для .NET Core CLI в **bash**, добавьте в свой файл `.bashrc` представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="102fa-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="102fa-132">Zsh</span><span class="sxs-lookup"><span data-stu-id="102fa-132">Zsh</span></span>

<span data-ttu-id="102fa-133">Чтобы добавить автодополнение клавишей TAB для .NET Core CLI в **zsh**, добавьте в свой файл `.zshrc` представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="102fa-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
