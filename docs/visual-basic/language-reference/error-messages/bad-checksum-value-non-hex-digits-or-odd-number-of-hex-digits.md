---
title: Неверное значение контрольной суммы, не шестнадцатеричные цифры или нечетное число шестнадцатеричных цифр
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 81156fd7b1c9957486bcdd898c90a2bad2945829
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340312"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="28579-102">Неверное значение контрольной суммы, не шестнадцатеричные цифры или нечетное число шестнадцатеричных цифр</span><span class="sxs-lookup"><span data-stu-id="28579-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="28579-103">Значение контрольной суммы содержит недопустимые шестнадцатеричные цифры или содержит нечетное число цифр.</span><span class="sxs-lookup"><span data-stu-id="28579-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="28579-104">Когда среда ASP.NET создает исходный файл Visual Basic (с расширением VB), она вычисляет контрольную сумму и помещает ее в скрытый исходный файл под идентификатором `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="28579-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="28579-105">Это также может сделать и пользователь, создающий файл VB, однако лучше оставить выполнение этого процесса внутренним механизмам.</span><span class="sxs-lookup"><span data-stu-id="28579-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="28579-106">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="28579-106">By default, this message is a warning.</span></span> <span data-ttu-id="28579-107">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="28579-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="28579-108">**Идентификатор ошибки:** BC42033</span><span class="sxs-lookup"><span data-stu-id="28579-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28579-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="28579-109">To correct this error</span></span>  
  
1. <span data-ttu-id="28579-110">Если ASP.NET создает исходный файл Visual Basic, перезапустите сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="28579-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2. <span data-ttu-id="28579-111">Если предупреждение продолжает выводиться после перезапуска, переустановите ASP.NET и повторите попытку сборки.</span><span class="sxs-lookup"><span data-stu-id="28579-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3. <span data-ttu-id="28579-112">Если предупреждение не пропадает или вы не используете ASP.NET, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="28579-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28579-113">См. также</span><span class="sxs-lookup"><span data-stu-id="28579-113">See also</span></span>

- [<span data-ttu-id="28579-114">Обзор ASP.NET</span><span class="sxs-lookup"><span data-stu-id="28579-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="28579-115">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="28579-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
