---
title: Практическое руководство. Заполнение дерева XML из файловой системы (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34eec79e-7945-4ba8-9f74-d05bb8ec67f6
ms.openlocfilehash: 55c182134e0cc1a7472cfaa6bb4355e9457a6977
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789068"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-visual-basic"></a><span data-ttu-id="db540-102">Практическое руководство. Заполнение дерева XML из файловой системы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db540-102">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>
<span data-ttu-id="db540-103">Распространенным и полезным применением XML-деревьев является использование их в качестве иерархической структуры для хранения данных с именем и значением.</span><span class="sxs-lookup"><span data-stu-id="db540-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="db540-104">Можно заполнить дерево XML-данными, распределенными внутри иерархии, после чего выполнять по нему запросы, преобразования и, если необходимо, сериализацию.</span><span class="sxs-lookup"><span data-stu-id="db540-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="db540-105">В следующем сценарии многие виды семантических конструкций, присущих XML, например пространства имен и обработка пробельных символов, неважны.</span><span class="sxs-lookup"><span data-stu-id="db540-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="db540-106">Вместо этого XML-дерево используется как небольшая иерархическая база данных для одного пользователя, которая находится в памяти.</span><span class="sxs-lookup"><span data-stu-id="db540-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db540-107">Пример</span><span class="sxs-lookup"><span data-stu-id="db540-107">Example</span></span>  
 <span data-ttu-id="db540-108">В следующем примере происходит заполнение XML-дерева из локальной файловой системы при помощи рекурсии.</span><span class="sxs-lookup"><span data-stu-id="db540-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="db540-109">Затем выполняется запрос по дереву и вычисляется общий размер всех файлов в дереве.</span><span class="sxs-lookup"><span data-stu-id="db540-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```vb  
Module Module1  
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement  
        Dim di As DirectoryInfo = New DirectoryInfo(source)  
        Return <Dir Name=<%= di.Name %>>  
                   <%= From d In Directory.GetDirectories(source) _  
                       Select CreateFileSystemXmlTree(d) %>  
                   <%= From fi In di.GetFiles() _  
                       Select <File>  
                                  <Name><%= fi.Name %></Name>  
                                  <Length><%= fi.Length %></Length>  
                              </File> %>  
               </Dir>  
    End Function  
  
    Sub Main()  
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")  
        Console.WriteLine(fileSystemTree)  
        Console.WriteLine("------")  
        Dim totalFileSize As Long = _  
            ( _  
                From f In fileSystemTree...<File> _  
                Select CLng(f.<Length>(0)) _  
            ).Sum()  
        Console.WriteLine("Total File Size:{0}", totalFileSize)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="db540-110">Этот пример выводит данные примерно так:</span><span class="sxs-lookup"><span data-stu-id="db540-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
  
## <a name="see-also"></a><span data-ttu-id="db540-111">См. также</span><span class="sxs-lookup"><span data-stu-id="db540-111">See also</span></span>

- [<span data-ttu-id="db540-112">Дополнительные способы создания запросов (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db540-112">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
