---
title: свойство внешнего ключа
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 74117b30ca54f7c57bd970003fc6f5dcc54d553f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879088"
---
# <a name="foreign-key-property"></a>свойство внешнего ключа
Объект *свойство внешнего ключа* в Entity Data Model (EDM) является типом-примитивом [свойство](../../../../docs/framework/data/adonet/property.md) (или набор свойств примитивного типа) на [тип сущности](../../../../docs/framework/data/adonet/entity-type.md) , содержащий [ключ сущности](../../../../docs/framework/data/adonet/entity-key.md) другого типа сущности.  
  
 Свойство внешнего ключа схоже со столбцом внешнего ключа в реляционной базе данных. Так же, что столбцы внешнего ключа в реляционной базе данных используются для создания связей между строками в таблицах, свойства внешнего ключа в концептуальной модели используются для установления [ассоциации](../../../../docs/framework/data/adonet/association-type.md) между типами сущностей. Объект [ограничение ссылочной целостности](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) используется для определения связи между двумя типами сущностей, если один из типов имеет свойство внешнего ключа.  
  
## <a name="example"></a>Пример  
 На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`. Тип сущности `Book` имеет свойство `PublisherId`, которое ссылается на ключ сущности типа сущности `Publisher` при определении ограничения ссылочной целостности ассоциации `PublishedBy`.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "пример модели справочное ограничение")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) для определения концептуальных моделей. Следующий язык CSDL использует свойство внешнего ключа `PublisherId` для определения ограничения ссылочной целостности в ассоциации `PublishedBy`, приведенной ранее в концептуальной модели.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>См. также

- [Основные понятия модели EDM](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Сущностная модель данных](../../../../docs/framework/data/adonet/entity-data-model.md)
