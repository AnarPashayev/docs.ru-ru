---
title: сложный тип
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786747"
---
# <a name="complex-type"></a>сложный тип
*Сложный тип* — это шаблон для определения насыщенных структурированных свойств [типов сущностей](entity-type.md) или других сложных типов. Каждый шаблон содержит следующие сведения.  
  
- Уникальное имя. (Обязательный атрибут).  
  
    > [!NOTE]
    > Имя сложного типа не может быть таким же, что и имя типа сущности внутри одного и того же пространства имени.  
  
- Данные в форме одного или нескольких [свойств](property.md). (Необязательно.)  
  
    > [!NOTE]
    > Свойство сложного типа может быть другим сложным типом.  
  
 Сложный тип похож на тип сущности тем, что сложный тип может содержать полезные данные в форме свойств примитивного типа или других сложных типов. Однако между сложными типами и типами сущности существуют некоторые ключевые различия.  
  
- Сложные типы не имеют идентификаторов и поэтому не могут существовать независимо. Сложные типы могут существовать только как свойства типов сущностей или других сложных типов.  
  
- Сложные типы не могут участвовать в [связях](association-type.md). Ни один из окончаний ассоциации не может быть сложным типом, поэтому [Свойства навигации](navigation-property.md) не могут быть определены для сложных типов.  
  
## <a name="example"></a>Пример  
 [Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](./ef/language-reference/csdl-specification.md)), для определения концептуальных моделей. Далее на языке CSDL определяется сложный тип, адрес со свойствами примитивного типа `StreetAddress`, `City`, `StateOrProvince`, `Country` и `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Чтобы определить сложный тип `Address` (показанный выше) как свойство типа сущности, необходимо объявить тип свойства в определении типа сущности. Далее на языке CSDL объявляется свойство `Address` в виде сложного типа в типе сущности (издателе).  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>См. также

- [Основные понятия модели EDM](entity-data-model-key-concepts.md)
- [Сущностная модель данных](entity-data-model.md)
