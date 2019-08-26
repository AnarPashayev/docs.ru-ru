---
title: Практическое руководство. Чтение данных объекта из XML-файла (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 1d6ec71b9e408e1536063fc3d8f1badc0f38551e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590736"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="522ab-102">Практическое руководство. Чтение данных объекта из XML-файла (C#)</span><span class="sxs-lookup"><span data-stu-id="522ab-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="522ab-103">В этом примере демонстрируется считывание данных объекта, которые ранее были записаны в XML-файл с помощью класса <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="522ab-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="522ab-104">Пример</span><span class="sxs-lookup"><span data-stu-id="522ab-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="522ab-105">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="522ab-105">Compiling the Code</span></span>  
 <span data-ttu-id="522ab-106">Замените имя файла "c:\temp\SerializationOverview.xml" на имя файла, в котором содержатся сериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="522ab-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="522ab-107">Дополнительные сведения о сериализации данных см. в разделе [Практическое руководство. Запись данных объекта в XML-файл (C#)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="522ab-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="522ab-108">У класса должен быть открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="522ab-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="522ab-109">Десериализуются только открытые свойства и поля.</span><span class="sxs-lookup"><span data-stu-id="522ab-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="522ab-110">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="522ab-110">Robust Programming</span></span>  
 <span data-ttu-id="522ab-111">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="522ab-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="522ab-112">В сериализуемом классе нет открытого конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="522ab-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="522ab-113">Данные в файле не являются данными из класса, который десериализуется.</span><span class="sxs-lookup"><span data-stu-id="522ab-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="522ab-114">Файл не существует (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="522ab-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="522ab-115">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="522ab-115">.NET Framework Security</span></span>  
 <span data-ttu-id="522ab-116">Всегда проверяйте входные данные и никогда не десериализуйте данные из непроверенных источников.</span><span class="sxs-lookup"><span data-stu-id="522ab-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="522ab-117">Созданный заново объект выполняется на локальном компьютере с разрешениями кода, который его десериализовал.</span><span class="sxs-lookup"><span data-stu-id="522ab-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="522ab-118">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="522ab-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522ab-119">См. также</span><span class="sxs-lookup"><span data-stu-id="522ab-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="522ab-120">Практическое руководство. Запись данных объекта в XML-файл (C#)</span><span class="sxs-lookup"><span data-stu-id="522ab-120">How to: Write Object Data to an XML File (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="522ab-121">Сериализация (C#)</span><span class="sxs-lookup"><span data-stu-id="522ab-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="522ab-122">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="522ab-122">C# Programming Guide</span></span>](../../index.md)
