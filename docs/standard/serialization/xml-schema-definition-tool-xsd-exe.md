---
title: XML Schema Definition Tool (Xsd.exe)
description: Инструмент создания XML-сериализатора создает сборку XML-сериализации для типов в указанной сборке, улучшающую производительность XmlSerializer при запуске.
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: a66ebfee3a461bb800e61e4f1d789f497da2f9d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676612"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>XML Schema Definition Tool (Xsd.exe)

Инструмент определения схемы XML (Xsd.exe) создает схему XML или классы CLR из файлов XDR, XML и XSD либо из классов в сборке среды выполнения.

Инструмент определения схемы XML (Xsd.exe) обычно можно найти по следующему пути:\
_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{версия}\\bin\\NETFX {версия} Tools\\_

## <a name="syntax"></a>Синтаксис

Запустите инструмент из командной строки.

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> Для нормальной работы инструментов .NET Framework необходимо правильно настроить переменные среды `Path`, `Include` и `Lib`. Эти переменные среды устанавливаются с помощью программы SDKVars.bat, расположенной в каталоге \<SDK>\\\<version>\Bin. Программу SDKVars.bat следует выполнять в каждой командной оболочке.

## <a name="argument"></a>Аргумент

|Аргумент|Описание|
|--------------|-----------------|
|*file.extension*|Задает входной файл, который необходимо преобразовать. Следует указать одно из следующих расширений: XDR, XML, XSD, DLL или EXE.<br /><br /> Если указать файл схемы XDR (расширение XDR), Xsd.exe преобразует схему XDR в схему XSD. Имя выходного файла аналогично имени схемы XDR, но имеет расширение XSD.<br /><br /> Если указать XML-файл (расширение XML), Xsd.exe определяет схему по данным в файле и создает схему XSD. Имя выходного файла аналогично имени XML-файла, но имеет расширение XSD.<br /><br /> Если указать файл схемы XML (расширение XSD), Xsd.exe создает исходный код для объектов среды выполнения, соответствующих схеме XML.<br /><br /> Если указать файл сборки среды выполнения (расширение EXE или DLL), Xsd.exe создает схемы для одного или нескольких типов в этой сборке. Чтобы указать типы, для которых необходимо создать схемы, можно использовать параметр `/type`. Выходным схемам присваиваются имена schema0.xsd, schema1.xsd и т. д. Xsd.exe создает несколько схем, только если указанные типы задают пространство имен с использованием настраиваемого атрибута `XMLRoot`.|

## <a name="general-options"></a>Общие параметры

|Параметр|Описание|
|------------|-----------------|
|**/h\[elp\]**|Отображает синтаксис команд и параметров программы.|
|**/o\[utputdir\]:** _directory_|Задает каталог выходных файлов. Этот аргумент отображается только один раз. Значением по умолчанию является текущий каталог.|
|**/?**|Отображает синтаксис команд и параметров программы.|
|**/p\[arameters\]:** _file.xml_|Считывает параметры различных режимов операций из указанного XML-файла. Краткая форма: `/p:`. Дополнительные сведения см. в разделе [Примечания](#remarks).|

## <a name="xsd-file-options"></a>Параметры файла XSD

 Для файлов XSD следует указать только один из следующих параметров.

|Параметр|Описание|
|------------|-----------------|
|**/c\[lasses\]**|Создает классы, соответствующие указанной схеме. Чтобы считать данные XML в объект, используйте метод <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType>.|
|**/d\[ataset\]**|Создает классы, которые являются производными класса <xref:System.Data.DataSet> и соответствуют указанной схеме. Чтобы считать данные XML в производный класс, используйте метод <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType>.|

 Для файлов XSD также можно указать любой из следующих параметров.

|Параметр|Описание|
|------------|-----------------|
|**/e\[lement\]:** _элемент_|Определяет элемент в схеме, для которого создается код. По умолчанию все элементы имеют тип. Этот аргумент можно задать несколько раз.|
|**/enableDataBinding**|Реализует интерфейс <xref:System.ComponentModel.INotifyPropertyChanged> для всех созданных типов для обеспечения привязки данных. Краткая форма: `/edb`.|
|**/enableLinqDataSet**|(Сокращенная форма: `/eld`.) Указывает, что созданный набор данных можно запросить с помощью LINQ to DataSet. Этот параметр используется только при указании параметра /dataset. Дополнительные сведения см. в разделах [Общие сведения о LINQ to DataSet](../../framework/data/adonet/linq-to-dataset-overview.md) и [Запрос к типизированным объектам DataSet](../../framework/data/adonet/querying-typed-datasets.md). Общие сведения об использовании LINQ см. в разделе [LINQ — C#](../../csharp/programming-guide/concepts/linq/index.md) или [LINQ — Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**/f\[ields\]**|Создает поля вместо свойств. По умолчанию создаются свойства.|
|**/l\[anguage\]:** _язык_|Задает используемый язык программирования. Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#). Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|
|**/n\[amespace\]:** _пространство_имен_|Определяет пространство имен среды выполнения для создаваемых типов. Пространство имен по умолчанию — `Schemas`.|
|**/nologo**|Отключает баннер.|
|**/order**|Создает явные идентификаторы порядка для всех примитивных членов.|
|**/o\[ut\]:** _имя_каталога_|Задает выходной каталог, в котором следует разместить файлы. Значением по умолчанию является текущий каталог.|
|**/u\[ri\]:** _URI_|Определяет универсальный код ресурса (URI) для элементов схемы, для которого создается код. Этот универсальный код ресурса, если имеется, применяется ко всем элементам, заданным параметром `/element`.|

## <a name="dll-and-exe-file-options"></a>Параметры файлов DLL и EXE

|Параметр|Описание|
|------------|-----------------|
|**/t\[ype\]:** _имя_типа_|Задает имя типа, для которого следует создать схему. Можно указать несколько аргументов типа. Если *имя_типа* не указывает пространство имен, Xsd.exe сопоставляет все типы в сборке с указанным типом. Если *имя_типа* задает пространство имен, сопоставляется только этот тип. Если *имя_типа* заканчивается знаком звездочки (\*), средство сопоставляет все типы, которые начинаются со строки, предшествующей знаку звездочки (\*). Если параметр `/type` не задан, Xsd.exe создает схемы для всех типов в сборке.|

## <a name="remarks"></a>Примечания

В следующей таблице показаны операции, выполняемые Xsd.exe.

| | |
|------------|-----------------|
|XDR в XSD|Создает схему XML из файла схемы XDR. XDR является более ранним форматом схемы, основанной на XML.|
|XML в XSD|Создает схему XML из XML-файла.|
|XSD в DataSet|Создает классы CLR <xref:System.Data.DataSet> из файла схемы XSD. Создаваемые классы представляют собой объектную модель с широкими функциональными возможностями для обычных данных XML.|
|XSD в классы|Создает классы среды выполнения из файла схемы XSD. Созданные классы можно использовать совместно с <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> для чтения и записи кода XML, соответствующего схеме.|
|Классы в XSD| Создает схему XML из типа или типов в файле сборки среды выполнения. Созданная схема определяет формат XML, используемый <xref:System.Xml.Serialization.XmlSerializer>.|

 Xsd.exe позволяет управлять только схемами XML, которые соответствуют языку определения схемы XML (XSD), предложенному консорциумом World Wide Web Consortium (W3C). Дополнительные сведения о предложенном определении схемы XML или стандарте XML см. в <https://w3.org>.

## <a name="setting-options-with-an-xml-file"></a>Установка параметров с помощью XML-файла

С помощью параметра `/parameters` можно задать один XML-файл, который содержит различные параметры. Задаваемые параметры зависят от способа использования инструмента XSD.exe. Варианты включают в себя создание схем, файлов кода или создание файлов кода, содержащих функции `DataSet`. Например, можно задать элемент `<assembly>` как имя исполняемого файла (расширение EXE) или файла библиотеки типов (расширение DLL) при создании схемы, но не при создании файла кода. В следующем примере XML показано, как использовать элемент `<generateSchemas>` с указанным исполняемым файлом:

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Если предыдущий XML содержится в файле с именем GenerateSchemas.xml, используйте параметр `/parameters`, введя следующий текст в командной строке и нажав клавишу **ВВОД**:

```console
 xsd /p:GenerateSchemas.xml
```

С другой стороны, при создании схемы для одного типа, найденного в сборке, можно использовать следующий XML:

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Но чтобы использовать предыдущий код, в командной строке следует также указать имя сборки. В командной строке введите следующую команду (допустим, имя XML-файла — GenerateSchemaFromType.xml):

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

Для элемента `<generateSchemas>` следует указать только один из следующих параметров.

|Элемент|Описание|
|-------------|-----------------|
|\<assembly>|Определяет сборку, из которой создается схема.|
|\<type>|Определяет тип, найденный в сборке, для которого создается схема.|
|\<xml>|Задает XML-файл, для которого создается схема.|
|\<xdr>|Определяет файл XDR, для которого создается схема.|

Чтобы создать файл кода, используйте элемент `<generateClasses>`. В следующем примере создается файл кода. Обратите внимание, что также отображаются два атрибута, с помощью которых можно задать язык программирования и пространство имен создаваемого файла.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Параметры, которые можно задать для элемента `<generateClasses>`, включают в себя следующие.

|Элемент|Описание|
|-------------|-----------------|
|\<element>|Определяет элемент в файле XSD, для которого создается код.|
|\<schemaImporterExtensions>|Определяет тип, унаследованный от класса <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>.|
|\<schema>|Определяет файл схемы XML, для которой создается код. С помощью нескольких элементов \<schema> можно задать несколько файлов схемы XML.|

В следующей таблице представлены атрибуты, которые также можно использовать с элементом `<generateClasses>`.

|Атрибут|Описание|
|---------------|-----------------|
|язык|Задает используемый язык программирования. Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#). Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|namespace|Задает пространство имен созданного кода. Пространство имен должно соответствовать стандартам CLR (например, отсутствие пробелов или обратной косой черты).|
|options|Одно из следующих значений: `none`, `properties` (создает свойства вместо открытых полей), `order` или `enableDataBinding` (см. параметры `/order` и `/enableDataBinding` в предыдущем разделе параметров файла XSD).|

 Также предусмотрена возможность управления созданием кода `DataSet` с использованием элемента `<generateDataSet>`. Приведенный ниже XML-код указывает, что созданный код использует структуры `DataSet` (например, класс <xref:System.Data.DataTable>), чтобы создать код Visual Basic для указанного элемента. Созданные структуры DataSet поддерживают запросы LINQ.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Параметры, которые можно задать для элемента `<generateDataSet>`, включают в себя следующие.

|Элемент|Описание|
|-------------|-----------------|
|\<schema>|Определяет файл схемы XML, для которой создается код. С помощью нескольких элементов \<schema> можно задать несколько файлов схемы XML.|

 В следующей таблице представлены атрибуты, которые можно использовать с элементом `<generateDataSet>`.

|Атрибут|Описание|
|---------------|-----------------|
|enableLinqDataSet|Указывает, что созданный набор данных можно запросить с помощью LINQ to DataSet. Значением по умолчанию является false.|
|язык|Задает используемый язык программирования. Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#). Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|namespace|Задает пространство имен созданного кода. Пространство имен должно соответствовать стандартам CLR (например, отсутствие пробелов или обратной косой черты).|

 Существуют атрибуты, которые можно задать для элемента верхнего уровня `<xsd>`. Эти параметры можно использовать с любым из дочерних элементов (`<generateSchemas>`, `<generateClasses>` или `<generateDataSet>`). Следующий код XML создает код для элемента с именем "IDItems" в выходном каталоге с именем "MyOutputDirectory".

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

В следующей таблице представлены атрибуты, которые также можно использовать с элементом `<xsd>`.

|Атрибут|Описание|
|---------------|-----------------|
|output|Имя каталога, в который сохраняется созданная схема или файл кода.|
|nologo|Отключает баннер. Задайте `true` или `false`.|
|help|Отображает синтаксис команд и параметров программы. Задайте `true` или `false`.|

## <a name="examples"></a>Примеры

 Следующая команда создает схему XML из `myFile.xdr` и сохраняет ее в текущий каталог.

```console
xsd myFile.xdr
```

Следующая команда создает схему XML из `myFile.xml` и сохраняет ее в указанный каталог.

```console
xsd myFile.xml /outputdir:myOutputDir
```

Следующая команда создает набор данных, соответствующий определенной схеме на языке C# и сохраняет его как `XSDSchemaFile.cs` в текущий каталог.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

Следующая команда создает схемы XML для всех типов в сборке `myAssembly.dll` и сохраняет их как `schema0.xsd` в текущий каталог.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>См. также

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [Инструменты](../../framework/tools/index.md)
- [Командные строки](../../framework/tools/developer-command-prompt-for-vs.md)
- [Общие сведения о LINQ to DataSet](../../framework/data/adonet/linq-to-dataset-overview.md)
- [Запрос к типизированным объектам DataSet](../../framework/data/adonet/querying-typed-datasets.md)
- [Встроенный язык запросов LINQ (C#)](../../csharp/programming-guide/concepts/linq/index.md)
- [Встроенный язык запросов LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
