---
title: Пример связывания запросов (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 8685db7461a1ce97c7a9c0045ed842fa4ac1a1f6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486197"
---
# <a name="chaining-queries-example-c"></a>Пример связывания запросов (C#)
Этот пример основан на предыдущем примере и показывает, что происходит при соединении в цепочку двух запросов, использующих отложенное выполнение и отложенное вычисление.  
  
## <a name="example"></a>Пример  
 В этом примере представлен другой метод расширения, `AppendString`, который добавляет указанную строку в каждую строку исходной коллекции, а затем выдает новые строки.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 В этом примере выводятся следующие данные:  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 В этом примере видно, что каждый метод расширения работает поочередно с каждым элементом исходной коллекции.  
  
 Этот пример показывает, что даже при соединении в цепочку двух запросов, формирующих коллекции, промежуточные коллекции не материализуются. Вместо этого каждый элемент передается от одного отложенного метода к другому. Это приводит к использованию намного меньшего объема памяти, чем при подходе, который сначала принимает один массив строк, затем создает второй массив строк, преобразованных в символы верхнего регистра, и наконец создает третий массив строк, где каждая строка имеет добавленные к ней восклицательные знаки.  
  
 Следующий раздел учебника иллюстрирует промежуточную материализацию:  
  
- [Промежуточная материализация (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>См. также

- [Учебник. Объединение запросов в цепочки (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
