---
title: Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: aa97ae420a0a289979fe86db373c635361dc6475
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874642"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="a168f-102">Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс</span><span class="sxs-lookup"><span data-stu-id="a168f-102">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="a168f-103">Либо класс, указанный вами в вызове функции `GetObject` или `CreateObject`, не предоставил интерфейс программирования, либо вы изменили проект с .DLL на .EXE или наоборот.</span><span class="sxs-lookup"><span data-stu-id="a168f-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a168f-104">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a168f-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a168f-105">Просмотрите документацию по приложению, которое создало данный объект, чтобы узнать об ограничениях на использование автоматизации с объектом такого класса.</span><span class="sxs-lookup"><span data-stu-id="a168f-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="a168f-106">Если вы изменили проект с .DLL на .EXE или наоборот, необходимо вручную отменить регистрацию старого проекта .DLL или .EXE.</span><span class="sxs-lookup"><span data-stu-id="a168f-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a168f-107">См. также</span><span class="sxs-lookup"><span data-stu-id="a168f-107">See also</span></span>

- [<span data-ttu-id="a168f-108">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="a168f-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="a168f-109">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="a168f-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
