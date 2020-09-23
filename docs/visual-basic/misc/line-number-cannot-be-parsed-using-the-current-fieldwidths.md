---
title: Разбор строки <number> с помощью текущего параметра FieldWidths невозможен
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_MalFormedFixedWidthLine
ms.assetid: 84e14245-dfdf-4b62-8b84-e83a31608899
ms.openlocfilehash: bd7c372f3cfee3babe4b3fdf190bf8ed87dab6db
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100377"
---
# <a name="line-number-cannot-be-parsed-using-the-current-fieldwidths"></a><span data-ttu-id="5b9c7-102">Разбор строки \<number> с помощью текущего параметра FieldWidths невозможен</span><span class="sxs-lookup"><span data-stu-id="5b9c7-102">Line \<number> cannot be parsed using the current FieldWidths</span></span>

<span data-ttu-id="5b9c7-103">Указанная строка не может быть проанализирована, так как ее поля имеют ширину, отличную от указанной.</span><span class="sxs-lookup"><span data-stu-id="5b9c7-103">The specified line cannot be parsed because its fields have widths other than those specified.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b9c7-104">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="5b9c7-104">To correct this error</span></span>  
  
- <span data-ttu-id="5b9c7-105">Настройте `FieldWidths` так, чтобы строка могла быть проанализирована правильно, или вставьте код обработки исключения, чтобы обработать строку.</span><span class="sxs-lookup"><span data-stu-id="5b9c7-105">Adjust `FieldWidths` so the line can be parsed correctly, or insert exception-handling code in order to handle the line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b9c7-106">См. также</span><span class="sxs-lookup"><span data-stu-id="5b9c7-106">See also</span></span>

- [<span data-ttu-id="5b9c7-107">Практическое руководство. Чтение из текстовых файлов различных форматов</span><span class="sxs-lookup"><span data-stu-id="5b9c7-107">How to: Read From Text Files with Multiple Formats</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="5b9c7-108">My. Computer. FileSystem. OpenTextFieldParser</span><span class="sxs-lookup"><span data-stu-id="5b9c7-108">My.Computer.FileSystem.OpenTextFieldParser</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A)
- [<span data-ttu-id="5b9c7-109">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="5b9c7-109">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="5b9c7-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="5b9c7-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
- [<span data-ttu-id="5b9c7-111">Свойство TextFieldParser.FieldWidths</span><span class="sxs-lookup"><span data-stu-id="5b9c7-111">TextFieldParser.FieldWidths Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A)
- [<span data-ttu-id="5b9c7-112">Метод TextFieldParser.SetFieldWidths</span><span class="sxs-lookup"><span data-stu-id="5b9c7-112">TextFieldParser.SetFieldWidths Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A)
