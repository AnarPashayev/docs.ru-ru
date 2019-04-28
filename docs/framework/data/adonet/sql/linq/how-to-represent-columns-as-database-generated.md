---
title: Практическое руководство. Как представить столбцы как сформированные базой данных
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2803697c668a8e1dbbeb426ea41b64878f70c145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903491"
---
# <a name="how-to-represent-columns-as-database-generated"></a>Практическое руководство. Как представить столбцы как сформированные базой данных
Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> свойство <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибут поля или свойства, представляющего столбец, созданный базой данных.  
  
 Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>Назначение поля или свойства, представляющего столбец, созданный базой данных  
  
1. Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. В качестве значения свойства задайте `true`.  
  
## <a name="see-also"></a>См. также

- [Модель объектов LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Практическое руководство. Настройка классов сущностей с помощью редактора кода](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
