---
title: Обеспечение безопасности данных
description: Объявите данные о состоянии как закрытые или внутренние переменные, чтобы ограничить доступ к ним. Доступ к таким данным по-прежнему можно получить с помощью отражения, сериализации и отладки.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291049"
---
# <a name="securing-state-data"></a><span data-ttu-id="db184-104">Обеспечение безопасности данных</span><span class="sxs-lookup"><span data-stu-id="db184-104">Securing State Data</span></span>
<span data-ttu-id="db184-105">Приложения, работающие с конфиденциальными данными или принимающие любые решения по организации безопасности, должны сохранять эти данные под своим непосредственным управлением и не должны позволять потенциально вредоносному коду напрямую получать доступ к данным.</span><span class="sxs-lookup"><span data-stu-id="db184-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="db184-106">Лучшим способом защиты данных в памяти является объявление этих данных как закрытых или внутренних переменных (с областью, ограниченной той же сборкой).</span><span class="sxs-lookup"><span data-stu-id="db184-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="db184-107">Однако не следует забывать, что даже к этим данным применяются права доступа.</span><span class="sxs-lookup"><span data-stu-id="db184-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="db184-108">С помощью механизмов отражения код с высоким доверием, способный ссылаться на ваш объект, может получать и устанавливать закрытые члены.</span><span class="sxs-lookup"><span data-stu-id="db184-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="db184-109">С помощью сериализации код с высоким доверием может эффективно получать и устанавливать закрытые члены, если он имеет доступ к соответствующим данным в сериализованной форме объекта.</span><span class="sxs-lookup"><span data-stu-id="db184-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="db184-110">Эти данные могут считываться в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="db184-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="db184-111">Убедитесь, что ни один из ваших собственных методов или свойств не предоставляет непреднамеренно эти значения.</span><span class="sxs-lookup"><span data-stu-id="db184-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db184-112">См. также</span><span class="sxs-lookup"><span data-stu-id="db184-112">See also</span></span>

- [<span data-ttu-id="db184-113">Правила написания безопасного кода</span><span class="sxs-lookup"><span data-stu-id="db184-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
