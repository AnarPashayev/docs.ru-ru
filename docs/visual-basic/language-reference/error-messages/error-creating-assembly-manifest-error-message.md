---
title: 'Ошибка при создании манифеста сборки: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 0f67b772bab3104c00510954d01b200aadfa9e8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803354"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="f9a51-102">Ошибка при создании манифеста сборки: \<сообщение об ошибке ></span><span class="sxs-lookup"><span data-stu-id="f9a51-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="f9a51-103">Компилятор Visual Basic вызывает компоновщик сборок (Al.exe, который также называется Alink) для создания сборки с манифестом.</span><span class="sxs-lookup"><span data-stu-id="f9a51-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="f9a51-104">Компоновщик сообщил об ошибке на этапе предварительного выпуска процедуры создания сборки.</span><span class="sxs-lookup"><span data-stu-id="f9a51-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="f9a51-105">Такая ситуация может возникнуть при наличии проблем с указанным файлом ключа или контейнером ключей.</span><span class="sxs-lookup"><span data-stu-id="f9a51-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="f9a51-106">Чтобы использовать для сборки полную подпись, необходимо предоставить допустимый файл ключа с информацией об открытом и закрытом ключах.</span><span class="sxs-lookup"><span data-stu-id="f9a51-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="f9a51-107">Чтобы использовать для сборки отложенную подпись, необходимо установить флажок **Только отложенная подпись** и предоставить допустимый файл ключа с информацией о ключах.</span><span class="sxs-lookup"><span data-stu-id="f9a51-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="f9a51-108">При использовании отложенной подписи для сборки наличие закрытого ключа не требуется.</span><span class="sxs-lookup"><span data-stu-id="f9a51-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="f9a51-109">Дополнительные сведения см. в разделе [Как Подписание сборки строгим именем](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="f9a51-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="f9a51-110">**Идентификатор ошибки:** BC30140</span><span class="sxs-lookup"><span data-stu-id="f9a51-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9a51-111">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f9a51-111">To correct this error</span></span>  
  
1. <span data-ttu-id="f9a51-112">Изучите приведенное сообщение об ошибке и обратитесь к разделу [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f9a51-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="f9a51-113">по ошибке AL1019 дополнительные пояснения и рекомендации</span><span class="sxs-lookup"><span data-stu-id="f9a51-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="f9a51-114">Если ошибка не устранена, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f9a51-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a51-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f9a51-115">See also</span></span>

- [<span data-ttu-id="f9a51-116">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="f9a51-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="f9a51-117">Страница "Подписывание" в конструкторе проектов</span><span class="sxs-lookup"><span data-stu-id="f9a51-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="f9a51-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="f9a51-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="f9a51-119">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="f9a51-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
