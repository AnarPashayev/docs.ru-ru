---
title: Выражения инициализации
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 109be8ef2bf41326fcab5896ecdc359859683345
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250673"
---
# <a name="initialization-expressions"></a>Выражения инициализации
Выражения инициализации инициализируют новый объект. Поддерживается большинство выражений инициализации, в том числе большинство новых выражений инициализации языков C# 3.0 и Visual Basic 9.0. Следующие типы могут быть инициализированы и возвращены запросом LINQ to Entities:  
  
- Коллекция, которая включает ноль или больше типизированных объектов сущностей, или проекция сложных типов, которая определена в концептуальной модели.  
  
- Типы CLR, поддерживаемые [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
- Встроенные коллекции.  
  
- Анонимные типы.  
  
 В следующем примере с синтаксисом выражения запроса показана инициализация анонимного типа:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Следующий пример с синтаксисом запроса на основе метода показывает инициализацию анонимного типа:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Также поддерживается инициализация определяемого пользователем класса. Поддерживается модель инициализации языков C# 3.0 и Visual Basic 9.0 и предполагается, что метод считывания и метод задания свойства симметричны. В следующем примере синтаксис выражения запроса показывает пользовательский класс, инициализируемый в запросе:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 В следующем примере синтаксис запроса на основе метода показывает пользовательский класс, инициализируемый в запросе:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>См. также

- [Выражения в запросах LINQ to Entities](expressions-in-linq-to-entities-queries.md)
