---
title: Образец технологии базовой сериализации
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 803f45db008dc6d12566868ba4a8c61642687d89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486387"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="7be97-102">Образец технологии базовой сериализации</span><span class="sxs-lookup"><span data-stu-id="7be97-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="7be97-103">Скачать образец</span><span class="sxs-lookup"><span data-stu-id="7be97-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="7be97-104">В этом образце демонстрируется возможность среды CLR выполнять сериализацию графа объекта в поток.</span><span class="sxs-lookup"><span data-stu-id="7be97-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="7be97-105">Для сериализации в примере могут использоваться классы <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> или <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="7be97-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="7be97-106">Связанный список, заполненный данными, сериализируется в поток файла или десериализируется из потока файла.</span><span class="sxs-lookup"><span data-stu-id="7be97-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="7be97-107">В любом случае этот список отображается для того, чтобы можно было видеть результаты.</span><span class="sxs-lookup"><span data-stu-id="7be97-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="7be97-108">Связанный список является списком типа `LinkedList`, который определен в этом примере.</span><span class="sxs-lookup"><span data-stu-id="7be97-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="7be97-109">Дополнительные сведения о сериализации см. в комментариях к исходному коду и в файлах build.proj.</span><span class="sxs-lookup"><span data-stu-id="7be97-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="7be97-110">Сборка образца с использованием командной строки</span><span class="sxs-lookup"><span data-stu-id="7be97-110">To build the sample using the Command Prompt</span></span>  
  
1. <span data-ttu-id="7be97-111">С помощью командной строки перейдите к одной из вложенных папок в каталоге Technologies\Serialization\Runtime Serialization\Basic, соответствующей выбранному языку.</span><span class="sxs-lookup"><span data-stu-id="7be97-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2. <span data-ttu-id="7be97-112">В командной строке введите **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** или **msbuild SerializationVB.sln**, в зависимости от выбранного языка программирования.</span><span class="sxs-lookup"><span data-stu-id="7be97-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="7be97-113">Сборка образца с использованием Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7be97-113">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="7be97-114">Откройте проводник и перейдите к одной из примера, соответствующей выбранному языку.</span><span class="sxs-lookup"><span data-stu-id="7be97-114">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="7be97-115">Дважды щелкните значок файла SerializationCS.sln, SerializationJSL.sln или SerializationVB.sln file, в зависимости от выбранного языка программирования, чтобы открыть файл в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7be97-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="7be97-116">В меню **Построение** выберите команду **Построить решение**.</span><span class="sxs-lookup"><span data-stu-id="7be97-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="7be97-117">По умолчанию сборка образца приложения помещается в подкаталог \bin или \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="7be97-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7be97-118">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="7be97-118">To run the sample</span></span>  
  
1. <span data-ttu-id="7be97-119">Перейдите в каталог, содержащий построенный исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="7be97-119">Navigate to the directory containing the built executable.</span></span>  
  
2. <span data-ttu-id="7be97-120">В командной строке введите **Serialization.exe** вместе с необходимыми значениями параметров.</span><span class="sxs-lookup"><span data-stu-id="7be97-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7be97-121">В данном образце выполняется построение консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="7be97-121">This sample builds a console application.</span></span> <span data-ttu-id="7be97-122">Чтобы просмотреть выводимые им данные, необходимо запустить его в командной строке.</span><span class="sxs-lookup"><span data-stu-id="7be97-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7be97-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="7be97-123">Remarks</span></span>  
 <span data-ttu-id="7be97-124">Образец приложения принимает параметры командной строки, указывающие, какой тест следует выполнить.</span><span class="sxs-lookup"><span data-stu-id="7be97-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="7be97-125">Чтобы выполнить сериализацию списка из 10 узлов в файл с именем **Test.xml** с помощью модуля форматирования SOAP, используйте параметры **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="7be97-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="7be97-126">Пример.</span><span class="sxs-lookup"><span data-stu-id="7be97-126">For Example:</span></span>  
  
 <span data-ttu-id="7be97-127">**Serialize.exe -sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="7be97-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="7be97-128">Чтобы десериализировать файл **Test.xml** из предыдущего примера, используйте параметры **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="7be97-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="7be97-129">Пример.</span><span class="sxs-lookup"><span data-stu-id="7be97-129">For Example:</span></span>  
  
 <span data-ttu-id="7be97-130">**Serialize.exe -dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="7be97-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="7be97-131">В двух приведенных выше примерах параметр командной строки "x" означает использование сериализации XML SOAP.</span><span class="sxs-lookup"><span data-stu-id="7be97-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="7be97-132">Вместо этого можно использовать "b" для двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="7be97-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="7be97-133">Если необходимо испытать сериализацию с очень большим числом узлов, может потребоваться перенаправить выходные данные с консоли в файл.</span><span class="sxs-lookup"><span data-stu-id="7be97-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="7be97-134">Пример.</span><span class="sxs-lookup"><span data-stu-id="7be97-134">For Example:</span></span>  
  
 <span data-ttu-id="7be97-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="7be97-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="7be97-136">В следующем маркированном списке кратко описываются технологии и классы, используемые в этом образце.</span><span class="sxs-lookup"><span data-stu-id="7be97-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
- <span data-ttu-id="7be97-137">Сериализация во время выполнения</span><span class="sxs-lookup"><span data-stu-id="7be97-137">Runtime Serialization</span></span>  
  
    - <span data-ttu-id="7be97-138"><xref:System.Runtime.Serialization.IFormatter> Используется для ссылки на <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> или <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> объекта.</span><span class="sxs-lookup"><span data-stu-id="7be97-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    - <span data-ttu-id="7be97-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Используется для сериализации связанного списка в поток в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="7be97-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="7be97-140">Двоичный модуль форматирования использует формат, который понятен только типу <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="7be97-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="7be97-141">Однако данные являются краткими.</span><span class="sxs-lookup"><span data-stu-id="7be97-141">However, the data is concise.</span></span>  
  
    - <span data-ttu-id="7be97-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Используется для сериализации связанного списка в поток формата SOAP.</span><span class="sxs-lookup"><span data-stu-id="7be97-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="7be97-143">SOAP является стандартным форматом.</span><span class="sxs-lookup"><span data-stu-id="7be97-143">SOAP is a standard format.</span></span>  
  
- <span data-ttu-id="7be97-144">Потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="7be97-144">Stream I/O</span></span>  
  
    - <span data-ttu-id="7be97-145"><xref:System.IO.Stream> Используется для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="7be97-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="7be97-146">Особый тип потока, который используется в этом примере, является типом <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="7be97-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="7be97-147">Однако сериализация может быть использована с любым типом, производным от <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="7be97-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    - <span data-ttu-id="7be97-148"><xref:System.IO.File> Используется для создания объектов <xref:System.IO.FileStream> для чтения и создания файлов на диске.</span><span class="sxs-lookup"><span data-stu-id="7be97-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    - <span data-ttu-id="7be97-149"><xref:System.IO.FileStream> Используется для сериализации и десериализации связанных списков.</span><span class="sxs-lookup"><span data-stu-id="7be97-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be97-150">См. также</span><span class="sxs-lookup"><span data-stu-id="7be97-150">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="7be97-151">Базовая сериализация</span><span class="sxs-lookup"><span data-stu-id="7be97-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="7be97-152">Двоичная сериализация</span><span class="sxs-lookup"><span data-stu-id="7be97-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="7be97-153">Управление сериализацией XML с использованием атрибутов</span><span class="sxs-lookup"><span data-stu-id="7be97-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="7be97-154">Введение в сериализацию XML</span><span class="sxs-lookup"><span data-stu-id="7be97-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="7be97-155">Сериализация</span><span class="sxs-lookup"><span data-stu-id="7be97-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="7be97-156">Сериализация XML и SOAP</span><span class="sxs-lookup"><span data-stu-id="7be97-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
