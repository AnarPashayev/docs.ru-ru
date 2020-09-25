---
title: Поставщик Entity Framework (службы данных WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: cb7bd7e793f73fc34057150ee5217dba6653237e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172649"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Поставщик Entity Framework (службы данных WCF)

Как и WCF Data Services, Entity Framework ADO.NET основывается на EDM, который является типом модели отношений сущностей. Entity Framework преобразует операции в свою реализацию EDM, которая называется *концептуальной моделью*, в эквивалентные операции с источником данных. Это делает Entity Framework идеальным поставщиком для служб данных, основанных на реляционных данных, и любой базы данных с поставщиком данных, поддерживающим Entity Framework, можно использовать с WCF Data Services. Список источников данных, которые в настоящее время поддерживают Entity Framework, см. в разделе [поставщики Entity Framework](/ef/ef6/fundamentals/providers/).
  
 В концептуальной модели контейнер сущностей является корнем службы. Прежде чем данные могут быть предоставлены службой данных, необходимо определить концептуальную модель Entity Framework. Дополнительные сведения см. [в разделе инструкции. Создание службы данных с помощью источника данных ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 WCF Data Services поддерживает модель оптимистичного параллелизма, позволяя определить маркер параллелизма для сущности. Этот маркер параллелизма, включающий одно или несколько свойств сущности, используется службой данных для определения, произошло ли изменение в запрашиваемых, обновляемых или удаляемых данных. Когда значения маркера, полученные из eTag в запросе, отличаются от текущих значений сущности, служба данных вызывает исключение. Чтобы указать, что свойство является частью маркера параллелизма, необходимо применить атрибут `ConcurrencyMode="Fixed"` в модели данных, определенной поставщиком Entity Framework. Маркер параллелизма не может содержать ключевое свойство или свойство навигации. Дополнительные сведения см. [в разделе Обновление службы данных](updating-the-data-service-wcf-data-services.md).  
  
 Дополнительные сведения о Entity Framework см. в разделе [Общие сведения о Entity Framework](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>См. также раздел

- [Поставщики служб данных](data-services-providers-wcf-data-services.md)
- [Поставщик отражения](reflection-provider-wcf-data-services.md)
- [EDM (модель данных с использованием сущностей)](../adonet/entity-data-model.md)
