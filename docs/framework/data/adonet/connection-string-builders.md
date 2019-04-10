---
title: Построители строк подключения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 17ef057fccbea48da698e0ecfa5c789e125adbb0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226889"
---
# <a name="connection-string-builders"></a><span data-ttu-id="698ed-102">Построители строк подключения</span><span class="sxs-lookup"><span data-stu-id="698ed-102">Connection String Builders</span></span>
<span data-ttu-id="698ed-103">В более ранних версиях [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]компиляции Проверка строк подключения с объединенная строка значений не выполнена, чтобы автоматически созданный во время выполнения неверное ключевое слово <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="698ed-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="698ed-104">Каждый из поставщиков данных платформы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] поддерживал различный синтаксис ключевых слов строк соединения, что делало ручное построение допустимых строк соединения затруднительным.</span><span class="sxs-lookup"><span data-stu-id="698ed-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="698ed-105">Для решения этой проблемы в [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 появились новые построители строк подключения для каждого поставщика данных платформы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="698ed-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="698ed-106">Каждый поставщик данных включает класс построителя строк соединения со строгой типизацией, наследованный от класса <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="698ed-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="698ed-107">В следующей таблице перечислены поставщики данных платформы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] и связанные с ними классы построителей строк соединения.</span><span class="sxs-lookup"><span data-stu-id="698ed-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="698ed-108">Поставщик</span><span class="sxs-lookup"><span data-stu-id="698ed-108">Provider</span></span>|<span data-ttu-id="698ed-109">Класс ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="698ed-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="698ed-110">Атаки путем внедрения данных в строку подключения</span><span class="sxs-lookup"><span data-stu-id="698ed-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="698ed-111">Атака путем внедрения данных в строку соединения может произойти при использовании динамического объединения строк для построения строк соединения, основанных на входных данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="698ed-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="698ed-112">Если строка не проверяется, а вредоносный текст или символы не экранируются, злоумышленник может получить потенциальный доступ к конфиденциальным данным или другим ресурсам сервера.</span><span class="sxs-lookup"><span data-stu-id="698ed-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="698ed-113">Например, злоумышленник может осуществить атаку, установив точку с запятой и добавив дополнительное значение.</span><span class="sxs-lookup"><span data-stu-id="698ed-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="698ed-114">Строка соединения анализируется с помощью алгоритма «по последнему значению», и допустимое значение заменяется вредоносными данными.</span><span class="sxs-lookup"><span data-stu-id="698ed-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="698ed-115">Классы построителей строк соединения созданы для устранения предположений и защиты от синтаксических ошибок и уязвимостей системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="698ed-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="698ed-116">Они предоставляют методы и свойства, соответствующие известным парам «ключ-значение», разрешенным каждым поставщиком данных.</span><span class="sxs-lookup"><span data-stu-id="698ed-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="698ed-117">Каждый класс поддерживает фиксированную коллекцию синонимов и может переводить синоним в соответствующее общеизвестное ключевое имя.</span><span class="sxs-lookup"><span data-stu-id="698ed-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="698ed-118">Выполняются проверки на допустимые пары «ключ-значение», и недопустимая пара вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="698ed-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="698ed-119">Кроме того, внедренные значения обрабатываются безопасным образом.</span><span class="sxs-lookup"><span data-stu-id="698ed-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="698ed-120">В следующем примере демонстрируется обработка с помощью объекта <xref:System.Data.SqlClient.SqlConnectionStringBuilder> дополнительного значения для параметра `Initial Catalog`.</span><span class="sxs-lookup"><span data-stu-id="698ed-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="698ed-121">Выход показывает, что объект <xref:System.Data.SqlClient.SqlConnectionStringBuilder> правильно выполняет обработку параметра путем экранирования дополнительного значения, заключенного в двойные кавычки, вместо того чтобы добавить его в строку соединения в качестве новой пары «ключ-значение».</span><span class="sxs-lookup"><span data-stu-id="698ed-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="698ed-122">Построение строк соединения из файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="698ed-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="698ed-123">Если некоторые элементы строки соединения известны заранее, их можно сохранить в файле конфигурации и во время выполнения получить для построения полной строки соединения.</span><span class="sxs-lookup"><span data-stu-id="698ed-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="698ed-124">Например, в отличие от имени сервера, имя базы данных может быть известно заранее.</span><span class="sxs-lookup"><span data-stu-id="698ed-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="698ed-125">Также можно принудительно задать ввод пользователем имени и пароля во время выполнения, чтобы исключить возможность внедрения других значений в строку соединения.</span><span class="sxs-lookup"><span data-stu-id="698ed-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="698ed-126">Один из перегруженных конструкторов для построителя строки соединения принимает в качестве аргумента значение типа <xref:System.String>, что позволяет использовать частичную строку соединения, которую впоследствии пользователь может дополнить.</span><span class="sxs-lookup"><span data-stu-id="698ed-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="698ed-127">Частичную строку соединения можно сохранить в файле конфигурации и получить во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="698ed-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="698ed-128">Пространство имен <xref:System.Configuration> обеспечивает программный доступ к файлам конфигурации, предоставляя класс <xref:System.Web.Configuration.WebConfigurationManager> для веб-приложений и класс <xref:System.Configuration.ConfigurationManager> для приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="698ed-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="698ed-129">Дополнительные сведения о работе со строками подключения и файлы конфигурации, см. в разделе [строки подключения и файлы конфигурации](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="698ed-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="698ed-130">Пример</span><span class="sxs-lookup"><span data-stu-id="698ed-130">Example</span></span>  
 <span data-ttu-id="698ed-131">В этом примере демонстрируется получение частичной строки соединения из файла конфигурации и ее завершение путем установки свойств <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> и <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> для объекта <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="698ed-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="698ed-132">Файл конфигурации определяется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="698ed-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="698ed-133">Для запуска кода необходимо задать в проекте ссылку на библиотеку `System.Configuration.dll`.</span><span class="sxs-lookup"><span data-stu-id="698ed-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="698ed-134">См. также</span><span class="sxs-lookup"><span data-stu-id="698ed-134">See also</span></span>

- [<span data-ttu-id="698ed-135">Строки подключения</span><span class="sxs-lookup"><span data-stu-id="698ed-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="698ed-136">Конфиденциальность и безопасность данных</span><span class="sxs-lookup"><span data-stu-id="698ed-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [<span data-ttu-id="698ed-137">Управляемые поставщики ADO.NET и центр разработчиков DataSet</span><span class="sxs-lookup"><span data-stu-id="698ed-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
