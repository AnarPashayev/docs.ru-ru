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
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Указано недопустимое имя для журнала событий
Для журнала событий было указано недопустимое имя. Обычно это является результатом недопустимых символов в имени, пустого имени файла или слишком длинного имени файла.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Если указанное имя содержит более восьми символов, убедитесь, что отсутствует конфликт с именами других журналов событий. При определении уникальности имени оцениваются только первые восемь символов.  
  
- Если указывается путь, убедитесь, что он анализируется правильно.  
  
- Проверьте имя на наличие недопустимых символов. Символы, которые нельзя использовать в имени файла: `<`, `>`, `:`, `"`, `/`, `\`и `|`.  
  
## <a name="see-also"></a>См. также

- [Практическое руководство. Анализ путей к файлам](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Практическое руководство. Переименование файла](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
