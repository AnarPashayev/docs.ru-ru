---
title: Практическое руководство. Запись данных объекта в XML-файл (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 5da79d68bf7e1c955cb6edededb3914bd9c898e5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590686"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Практическое руководство. Запись данных объекта в XML-файл (C#)
Показывает, как записать объект из класса в XML-файл с помощью класса <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Пример  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В сериализуемом классе должен быть открытый конструктор без параметров.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При следующих условиях возможно возникновение исключения:  
  
- В сериализуемом классе нет открытого конструктора без параметров.  
  
- Файл существует и является файлом только для чтения (<xref:System.IO.IOException>).  
  
- Слишком длинный путь (<xref:System.IO.PathTooLongException>).  
  
- Диск заполнен (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 В этом примере создается файл (если файл отсутствует). Если приложению требуется создать файл, оно должно иметь доступ к каталогу для создания файлов (`Create`). Если файл уже существует, то приложению достаточно иметь лишь доступ для записи файлов (`Write`), т. е. меньшие привилегии. Безопаснее создавать файл во время развертывания, если это возможно, а также предоставлять доступ `Read` к отдельному файлу вместо доступа `Create` к папке.  
  
## <a name="see-also"></a>См. также

- <xref:System.IO.StreamWriter>
- [Практическое руководство. Чтение данных объекта из XML-файла (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Сериализация (C#)](./index.md)
