---
title: Ошибка при загрузке библиотеки DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803471"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="126db-102">Ошибка при загрузке библиотеки DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="126db-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="126db-103">Это библиотека динамической компоновки (DLL) — это библиотека, указанный в `Lib` предложении `Declare` инструкции.</span><span class="sxs-lookup"><span data-stu-id="126db-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="126db-104">Среди возможных причин этой ошибки:</span><span class="sxs-lookup"><span data-stu-id="126db-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="126db-105">Файл не является исполняемой программой DLL.</span><span class="sxs-lookup"><span data-stu-id="126db-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="126db-106">Файл не является Библиотекой Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="126db-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="126db-107">DLL ссылается на другой библиотеке DLL, не существует.</span><span class="sxs-lookup"><span data-stu-id="126db-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="126db-108">DLL или DLL, на которую указывает ссылка отсутствует в каталоге, указанном в пути.</span><span class="sxs-lookup"><span data-stu-id="126db-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="126db-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="126db-109">To correct this error</span></span>  
  
- <span data-ttu-id="126db-110">Если файл источника текстовый файл и поэтому не исполняемый файл DLL, он должен будет компилироваться и собираться в форму исполняемого файла DLL.</span><span class="sxs-lookup"><span data-stu-id="126db-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="126db-111">Если файл не является Библиотекой Microsoft Windows, получите эквивалентное Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="126db-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="126db-112">Если библиотека DLL ссылается другая библиотека DLL, которая отсутствует, получите указанной библиотеке DLL и сделать его доступным.</span><span class="sxs-lookup"><span data-stu-id="126db-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="126db-113">Если DLL или DLL, на которую указывает ссылка не находится в каталоге, указанном в пути, переместите библиотеку DLL в каталог, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="126db-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126db-114">См. также</span><span class="sxs-lookup"><span data-stu-id="126db-114">See also</span></span>

- [<span data-ttu-id="126db-115">Оператор Declare</span><span class="sxs-lookup"><span data-stu-id="126db-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
