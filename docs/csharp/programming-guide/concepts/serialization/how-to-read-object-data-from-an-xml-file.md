---
title: Чтение данных объекта из XML-файла (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: e2365d1260d3f6e239f294b2af3399c2fb659575
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241881"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Чтение данных объекта из XML-файла (C#)
В этом примере демонстрируется считывание данных объекта, которые ранее были записаны в XML-файл с помощью класса <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Пример  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Компиляция кода  
Замените имя файла "c:\temp\SerializationOverview.xml" на имя файла, в котором содержатся сериализованные данные. Дополнительные сведения о сериализации данных см. в руководстве по [записи данных объекта в XML-файл (C#)](./how-to-write-object-data-to-an-xml-file.md).
  
 У класса должен быть открытый конструктор без параметров.  
  
 Десериализуются только открытые свойства и поля.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При следующих условиях возможно возникновение исключения:  
  
- В сериализуемом классе нет открытого конструктора без параметров.  
  
- Данные в файле не являются данными из класса, который десериализуется.  
  
- Файл не существует (<xref:System.IO.IOException>).  
  
## <a name="net-security"></a>Безопасность .NET  
 Всегда проверяйте входные данные и никогда не десериализуйте данные из непроверенных источников. Созданный заново объект выполняется на локальном компьютере с разрешениями кода, который его десериализовал. Следует проверять все входные данные перед использованием их в приложении.  
  
## <a name="see-also"></a>См. также

- <xref:System.IO.StreamWriter>
- [Практическое руководство. Запись данных объекта в XML-файл (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Сериализация (C#)](./index.md)
- [Руководство по программированию на C#](../../index.md)
