---
title: Создание исходного документа в формате Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 024b6c80cdedf38fd2dcee77562c0105df7bd033
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690105"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Создание исходного документа в формате Office Open XML (C#)

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

    using System;

    class Program {
        public static void Main(string[] args) {
            Console.WriteLine("Hello World");
        }
    }

    This example produces the following output:

    Hello World
    ```

3. Отформатируйте первую строку стилем «Заголовок 1».

4. Выделите строки, содержащие код C#. Первая строка начинается с ключевого слова `using`. Последняя строка содержит последнюю закрывающую фигурную скобку. Отформатируйте эти строки шрифтом courier. Создайте из них новый стиль и присвойте ему имя «Code».

5. Наконец, выделите всю строку, содержащую выходные данные, и отформатируйте ее стилем `Code`.

6. Сохраните документ с именем SampleDoc.docx.

    > [!NOTE]
    > Если используется Microsoft Word 2003, в раскрывающемся списке **Тип файла** выберите **Документ Word 2007**.
