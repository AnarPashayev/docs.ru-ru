---
title: . (Доступ к членам) (язык Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 1db6be632da90eaa7a761bb213e395182ae42347
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250297"
---
# <a name="-member-access-entity-sql"></a>. (Доступ к членам) (язык Entity SQL)
Оператор "точка" (.) является [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператором доступа к члену. Оператор доступа к элементу можно использовать, чтобы выдавать значение свойства или поля экземпляра структурного типа концептуальной модели.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Аргументы  
 `expression`  
 Экземпляр структурного типа концептуальной модели.  
  
 `identifier`  
 Свойство или поле, принадлежащее экземпляру объекта.  
  
## <a name="remarks"></a>Примечания  
 Оператор «точка» (.) можно использовать для извлечения полей из записи подобно извлечению свойств сложного типа или типа сущности. Например, если «n» типа Name является элементом типа Name, а «p» является элементом типа Person, то «p.n» будет допустимым выражением доступа к элементу, которое выдаст значение типа Name.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](entity-sql-reference.md)
