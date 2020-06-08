---
title: Распространенные задачи ввода-вывода
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 9474d6c0340583e285a6dc47933c602f799f121d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287431"
---
# <a name="common-io-tasks"></a>Распространенные задачи ввода-вывода
Пространство имен <xref:System.IO> предоставляет несколько классов, которые позволяют выполнять с файлами, каталогами и потоками различные действия, такие как чтение и запись. Дополнительные сведения см. в разделе [Файловый и потоковый ввод-вывод](index.md).  
  
## <a name="common-file-tasks"></a>Распространенные задачи с файлами  
  
|Для этого...|Раздел с примером|  
|-------------------|--------------------------------------|  
|Создание текстового файла|Метод <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Запись в текстовый файл|[Практическое руководство. Запись текста в файл](how-to-write-text-to-a-file.md)<br /><br /> [Практическое руководство. Запись данных в текстовый файл (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Чтение из текстового файла|[Практическое руководство. Считывание текста из файла](how-to-read-text-from-a-file.md)|  
|Добавление текста в файл|[Практическое руководство. Открытие файла журнала и добавление в него данных](how-to-open-and-append-to-a-log-file.md)<br /><br /> Метод <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Переименование или перемещение файла|Метод <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Удаление файла|Метод <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Копирование файла|Метод <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Получение сведений о размере файла|Свойство <xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>|  
|Получение атрибутов файла|Метод <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Установка атрибутов файла|Метод <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Определение существования файла|Метод <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Чтение из двоичного файла|[Практическое руководство. Считывание из нового файла данных и запись в этот файл](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Запись в двоичный файл|[Практическое руководство. Считывание из нового файла данных и запись в этот файл](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Извлечение расширения имени файла|Метод <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Извлечение полного пути к файлу|Метод <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Извлечение имени и расширения файла из пути|Метод <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Изменение расширения файла|Метод <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Распространенные задачи с каталогами  
  
|Для этого...|Раздел с примером|  
|-------------------|--------------------------------------|  
|Доступ к файлу в особой папке, например "Мои документы"|[Практическое руководство. Запись текста в файл](how-to-write-text-to-a-file.md)|  
|Создание каталога|Метод <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> Свойство <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>|  
|Создание подкаталога|Метод <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Переименование или перемещение каталога|Метод <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Копирование каталога|[Практическое руководство. Копирование каталогов](how-to-copy-directories.md)|  
|Удаление каталога|Метод <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Метод <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Просмотр файлов и подкаталогов в каталогах|[Практическое руководство. Перечисление каталогов и файлов](how-to-enumerate-directories-and-files.md)|  
|Определение размера каталога|Класс <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Определение существования каталога|Метод <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>См. также раздел

- [Файловый и потоковый ввод-вывод](index.md)
- [Составление потоков](composing-streams.md)
- [Asynchronous File I/O](asynchronous-file-i-o.md)
