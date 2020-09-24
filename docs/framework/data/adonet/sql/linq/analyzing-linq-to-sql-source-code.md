---
title: Анализ исходного кода LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e39b1686269442044beb73bb7e572738832bec27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164588"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Анализ исходного кода LINQ to SQL

С помощью описанных ниже действий можно создать исходный код [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] из учебной базы данных "Northwind". Чтобы лучше понять, как сопоставлены различные элементы, можно сравнить элементы модели объектов с элементами базы данных.  
  
> [!NOTE]
> Разработчики, использующие Visual Studio, могут создавать этот код с помощью реляционного конструктора O/R.  
  
1. Если образец базы данных Northwind еще не установлен на компьютере разработчика, его можно загрузить бесплатно. Дополнительные сведения см. в статье [Загрузка образцов баз данных](downloading-sample-databases.md).  
  
2. Для создания файла с исходным кодом Visual Basic или C# используется программа командной строки SQLMetal. Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Ниже показаны команды, которые необходимо ввести в командной строке для создания файлов с исходным кодом Visual Basic и C#, включающих хранимые процедуры и функции.  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>См. также раздел

- [Ссылки](reference.md)
- [Основные сведения](background-information.md)
