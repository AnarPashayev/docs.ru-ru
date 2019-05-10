---
title: Указано недопустимое имя для журнала событий
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 05f37239510482de218847f069dc74cbef91f398
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609168"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="0f08d-102">Указано недопустимое имя для журнала событий</span><span class="sxs-lookup"><span data-stu-id="0f08d-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="0f08d-103">Для журнала событий было указано недопустимое имя.</span><span class="sxs-lookup"><span data-stu-id="0f08d-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="0f08d-104">Обычно это является результатом недопустимых символов в имени, пустого имени файла или слишком длинного имени файла.</span><span class="sxs-lookup"><span data-stu-id="0f08d-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f08d-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="0f08d-105">To correct this error</span></span>  
  
- <span data-ttu-id="0f08d-106">Если указанное имя содержит более восьми символов, убедитесь, что отсутствует конфликт с именами других журналов событий.</span><span class="sxs-lookup"><span data-stu-id="0f08d-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="0f08d-107">При определении уникальности имени оцениваются только первые восемь символов.</span><span class="sxs-lookup"><span data-stu-id="0f08d-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="0f08d-108">Если указывается путь, убедитесь, что он анализируется правильно.</span><span class="sxs-lookup"><span data-stu-id="0f08d-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="0f08d-109">Проверьте имя на наличие недопустимых символов.</span><span class="sxs-lookup"><span data-stu-id="0f08d-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="0f08d-110">Символы, которые нельзя использовать в имени файла: `<`, `>`, `:`, `"`, `/`, `\`и `|`.</span><span class="sxs-lookup"><span data-stu-id="0f08d-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f08d-111">См. также</span><span class="sxs-lookup"><span data-stu-id="0f08d-111">See also</span></span>

- [<span data-ttu-id="0f08d-112">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="0f08d-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="0f08d-113">Практическое руководство. Переименование файла</span><span class="sxs-lookup"><span data-stu-id="0f08d-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
