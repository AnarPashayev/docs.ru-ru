---
title: Практическое руководство. Как указать поля закрытого хранения
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 843b7ae8dbddb76e0e5fa33d3594a5655dbf1a37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902724"
---
# <a name="how-to-specify-private-storage-fields"></a>Практическое руководство. Как указать поля закрытого хранения
Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> свойство <xref:System.Data.Linq.Mapping.DataAttribute> атрибут для назначения имени базового поля хранения.  
  
 Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>Задание имени базового поля хранения  
  
1. Добавьте свойство <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. Укажите имя поля в качестве значения свойства <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
## <a name="see-also"></a>См. также

- [Модель объектов LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Практическое руководство. Настройка классов сущностей с помощью редактора кода](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
