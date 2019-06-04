---
title: Данные FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 4edd03a38f8f5df6cb4fb9c2446f966dfe601564
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490074"
---
# <a name="filestream-data"></a><span data-ttu-id="a9c54-102">Данные FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="a9c54-102">FILESTREAM Data</span></span>

<span data-ttu-id="a9c54-103">Для двоичных данных (BLOB), хранящихся в столбце varbinary(max), появился новый атрибут хранилища FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="a9c54-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="a9c54-104">До появления FILESTREAM для хранения двоичных данных была необходима специальная обработка.</span><span class="sxs-lookup"><span data-stu-id="a9c54-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="a9c54-105">Неструктурированные данные, например текстовые документы, изображения и видеоролики, зачастую хранятся вне базы данных, что затрудняет работу с ними.</span><span class="sxs-lookup"><span data-stu-id="a9c54-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="a9c54-106">Для работы с данными FILESTREAM через SqlClient необходимо установить .NET Framework 3.5 с пакетом обновления 1 (SP1) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="a9c54-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="a9c54-107">При указании для столбца varbinary(max) атрибута FILESTREAM сервер SQL Server сохраняет данные не в файле базы данных, а в файловой системе NTFS на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a9c54-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="a9c54-108">Хотя эти данные хранятся отдельно, для работы с ними можно использовать те же инструкции Transact-SQL, что и для данных varbinary(max), хранящихся в базе данных.</span><span class="sxs-lookup"><span data-stu-id="a9c54-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="a9c54-109">Поддержка атрибута FILESTREAM в SqlClient</span><span class="sxs-lookup"><span data-stu-id="a9c54-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="a9c54-110">Поставщик данных .NET Framework для SQL Server, <xref:System.Data.SqlClient>, поддерживает чтение и запись данных FILESTREAM с помощью <xref:System.Data.SqlTypes.SqlFileStream> класс, определенный в <xref:System.Data.SqlTypes> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="a9c54-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="a9c54-111">Класс `SqlFileStream` является производным от класса <xref:System.IO.Stream>, который содержит методы для чтения и записи потоков данных.</span><span class="sxs-lookup"><span data-stu-id="a9c54-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="a9c54-112">При чтении из потока данные передаются в структуру данных, например в массив байтов.</span><span class="sxs-lookup"><span data-stu-id="a9c54-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="a9c54-113">При записи данные передаются из структуры данных в поток.</span><span class="sxs-lookup"><span data-stu-id="a9c54-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="a9c54-114">Создание таблицы SQL Server</span><span class="sxs-lookup"><span data-stu-id="a9c54-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="a9c54-115">Приведенная ниже инструкция Transact-SQL создает таблицу employees и вставляет в нее строку данных.</span><span class="sxs-lookup"><span data-stu-id="a9c54-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="a9c54-116">После включения атрибута FILESTREAM эту таблицу можно использовать в приведенных ниже примерах кода.</span><span class="sxs-lookup"><span data-stu-id="a9c54-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="a9c54-117">Ссылки на ресурсы в электронной документации по SQL Server приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="a9c54-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="a9c54-118">Пример Чтение, перезапись и вставка данных FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="a9c54-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="a9c54-119">В приведенном ниже образце демонстрируется чтение данных из потока FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="a9c54-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="a9c54-120">В коде определяется логический путь к файлу, свойству `FileAccess` присваивается значение `Read`, а свойству `FileOptions` - значение `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="a9c54-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="a9c54-121">Затем в коде считываются в буфер байты данных из потока SqlFileStream.</span><span class="sxs-lookup"><span data-stu-id="a9c54-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="a9c54-122">Эти байты данных затем выводятся в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a9c54-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="a9c54-123">В приведенном ниже образце также демонстрируется запись данных в поток FILESTREAM с перезаписью всех существующих данных.</span><span class="sxs-lookup"><span data-stu-id="a9c54-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="a9c54-124">В коде определяется логический путь к файлу, создается поток `SqlFileStream`, свойству `FileAccess` присваивается значение `Write`, а свойству `FileOptions` - значение `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="a9c54-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="a9c54-125">В поток `SqlFileStream` записывается один байт, заменяющий все данные в файле.</span><span class="sxs-lookup"><span data-stu-id="a9c54-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="a9c54-126">В этом примере кода также демонстрируется запись данных в поток FILESTREAM с использованием метода Seek для добавления данных в конец файла.</span><span class="sxs-lookup"><span data-stu-id="a9c54-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="a9c54-127">В коде определяется логический путь к файлу, создается поток `SqlFileStream`, свойству `FileAccess` присваивается значение `ReadWrite`, а свойству `FileOptions` - значение `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="a9c54-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="a9c54-128">Для поиска конца файла в коде используется метод Seek, после чего в конец файла добавляется один байт.</span><span class="sxs-lookup"><span data-stu-id="a9c54-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

<span data-ttu-id="a9c54-129">Другой пример, см. в разделе [способы хранения и получения двоичных данных в столбце файлового потока](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="a9c54-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="a9c54-130">Ресурсы электронной документации по SQL Server</span><span class="sxs-lookup"><span data-stu-id="a9c54-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="a9c54-131">Полная документация по FILESTREAM содержится в следующих разделах документации по SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9c54-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="a9c54-132">Раздел</span><span class="sxs-lookup"><span data-stu-id="a9c54-132">Topic</span></span>|<span data-ttu-id="a9c54-133">Описание</span><span class="sxs-lookup"><span data-stu-id="a9c54-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="a9c54-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a9c54-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="a9c54-135">Приводятся сведения о том, когда необходимо использовать хранилище FILESTREAM; также описывается интеграция ядра СУБД SQL Server и файловой системы NTFS.</span><span class="sxs-lookup"><span data-stu-id="a9c54-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="a9c54-136">Создание клиентских приложений для данных FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="a9c54-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="a9c54-137">Описание функций Windows API для работы с данными FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="a9c54-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="a9c54-138">FILESTREAM и другими компонентами SQL Server</span><span class="sxs-lookup"><span data-stu-id="a9c54-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="a9c54-139">Приводятся общие сведения, рекомендации и ограничения при использовании данных FILESTREAM совместно с другими возможностями SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9c54-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a9c54-140">См. также</span><span class="sxs-lookup"><span data-stu-id="a9c54-140">See also</span></span>

- [<span data-ttu-id="a9c54-141">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a9c54-141">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="a9c54-142">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a9c54-142">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="a9c54-143">Управление доступом для кода и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a9c54-143">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="a9c54-144">Двоичные данные и данные большого объема SQL Server</span><span class="sxs-lookup"><span data-stu-id="a9c54-144">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="a9c54-145">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a9c54-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
