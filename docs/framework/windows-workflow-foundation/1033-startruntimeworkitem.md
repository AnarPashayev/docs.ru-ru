---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924245"
---
# <a name="1033---startruntimeworkitem"></a>1033 - StartRuntimeWorkItem
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|ID|1033|  
|Ключевые слова|WFRuntime|  
|Уровень|Verbose|  
|Канал|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Описание  
 Указывает, что начинается выполнение RuntimeWorkItem.  
  
## <a name="message"></a>Сообщение  
 Начато выполнение рабочего элемента среды выполнения для действия «%1», DisplayName «%2», InstanceId «%3».  
  
## <a name="details"></a>Подробные сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|Действие|xs:string|Имя типа действия.|  
|DisplayName|xs:string|Отображаемое имя действия.|  
|InstanceId|xs:string|Идентификатор экземпляра действия.|  
|Домен приложения|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
