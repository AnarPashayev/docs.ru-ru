---
title: Создание исходного документа Open XML Office (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 83cb7d0a325e11c9669f1331e57bed7bf09f27c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333695"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Создание исходного документа Open XML Office (Visual Basic)
В этом разделе показано создание документа Office Open XML WordprocessingML, который используется в примерах этого учебника. Если следовать приведенным ниже инструкциям, выходные данные будут соответствовать выходным данным каждого примера.  
  
 Тем не менее примеры в этом учебнике работают с любым допустимым документом WordprocessingML.  
  
 Чтобы создать документ, который используется в этом учебнике, необходимо иметь установленный выпуск 2007 системы Microsoft Office или более поздней версии либо Microsoft Office 2003 с пакетом обеспечения совместимости Microsoft Office для форматов файлов Word, Excel и PowerPoint 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Создание документа WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Создание документа WordprocessingML  
  
1. Создайте документ Microsoft Word.  
  
2. Вставьте в новый документ следующий текст.  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. Отформатируйте первую строку стилем «Заголовок 1».  
  
4. Выберите строки, содержащие код Visual Basic. Первая строка начинается с ключевого слова `Imports`. Последняя строка — «End Class». Отформатируйте эти строки шрифтом courier. Создайте из них новый стиль и присвойте ему имя «Code».  
  
5. Наконец, выделите всю строку, содержащую выходные данные, и отформатируйте ее стилем `Code`.  
  
6. Сохраните документ с именем SampleDoc.docx.  
  
    > [!NOTE]
    >  Если используется Microsoft Word 2003, в раскрывающемся списке **Тип файла** выберите **Документ Word 2007**.  
  
## <a name="see-also"></a>См. также

- [Учебник. Управление содержимым в документе WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
