---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774261"
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|ID|4210|  
|Ключевые слова|WFInstanceStore|  
|Уровень|Предупреждение|  
|Канал|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Описание  
 Указывает, что было перехвачено исключение SQL.  
  
## <a name="message"></a>Сообщение  
 Обнаружено исключение SQL с номером %1, сообщение %2.  
  
## <a name="details"></a>Подробные сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|Номер ошибки SQL.|  
|ExceptionMessage|xs:string|Текст сообщения из исключения SQL.|  
|Домен приложения|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
