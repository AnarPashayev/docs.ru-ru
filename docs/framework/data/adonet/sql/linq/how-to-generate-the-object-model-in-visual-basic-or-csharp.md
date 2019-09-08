---
title: Практическое руководство. создать модель объектов на языке Visual Basic или C#
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 07df915b5c826c7b82f2aaf16fcc22da0361d5f6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781916"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Практическое руководство. Создание объектной модели в Visual Basic или C\#
В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектная модель используемого языка программирования сопоставляется с реляционной базой данных. Доступны два средства для автоматического создания Visual Basic или C# модели из метаданных существующей базы данных.  
  
- При использовании Visual Studio можно использовать реляционный конструктор объектов для создания объектной модели. Реляционный конструктор [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектов (R) предоставляет богатый пользовательский интерфейс, помогающий в создании объектной модели. Дополнительные сведения см. [в разделе средства LINQ to SQL в Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Средство командной строки SQLMetal. Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Если существующие базы данных отсутствуют и необходимо создать базу данных из объектной модели, можно создать объектную модель с помощью редактора кода и метода <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Дополнительные сведения см. в разделе [Как Динамическое создание базы](how-to-dynamically-create-a-database.md)данных.  
  
 Документация для реляционного конструктора объектов содержит примеры создания Visual Basic или C# объектной модели с помощью реляционного конструктора объектов (r). Ниже приведены примеры использования программы командной строки SQLMetal. Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Пример  
 Командная строка SQLMetal, показанная в следующем примере, создает Visual Basic код в качестве объектной модели на основе атрибутов образца базы данных Northwind. Также отображаются хранимые процедуры и функции.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Пример  
 С помощью команды программы SQLMetal, представленной в следующем примере, создается код C# для основанной на атрибутах объектной модели базы данных "Northwind". Также отображаются хранимые процедуры и функции и имена таблиц автоматически преобразуются в имена во множественном числе.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию](programming-guide.md)
- [Модель объектов LINQ to SQL](the-linq-to-sql-object-model.md)
- [Обучение с использованием пошаговых руководств](learning-by-walkthroughs.md)
- [Практическое руководство. Настройка классов сущностей с помощью редактора кода](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Сопоставление, основанное на атрибутах](attribute-based-mapping.md)
- [SqlMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Внешнее сопоставление](external-mapping.md)
- [Загрузка примеров баз данных](downloading-sample-databases.md)
- [Создание модели объектов](creating-the-object-model.md)
