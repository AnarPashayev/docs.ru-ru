---
title: 106 ― CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: 4d2e9bd271c04a9e26150e7dddffc33963dfe0a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924180"
---
# <a name="106---cancelrequestrecord"></a>106 ― CancelRequestRecord
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|Идентификатор|106|  
|Ключевые слова|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|Уровень|Сведения|  
|Канал|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Описание  
 Это событие создается участником отслеживания ETW, когда действие внутри рабочего процесса создает запись cancelrequestedrecord.  
  
## <a name="message"></a>Сообщение  
 TrackRecord=CancelRequestedRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName=%7, ChildActivityName=%8, ChildActivityId=%9, ChildActivityInstanceId=%10, ChildActivityTypeName=%11, Annotations=%12, ProfileName=%13  
  
## <a name="details"></a>Подробные сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Идентификатор экземпляра для рабочего процесса.|  
|RecordNumber|xs:long|Порядковый номер созданной записи.|  
|EventTime|xs:dateTime|Время в формате UTC, когда было создано событие.|  
|name|xs:string|Имя действия, запросившего операцию отмены.|  
|ActivityId|xs:string|Идентификатор действия, запросившего операцию отмены.|  
|ActivityInstanceId|xs:string|Идентификатор экземпляра действия, запросившего операцию отмены.|  
|ActivityTypeName|xs:string|Тип действия, запросившего операцию отмены.|  
|ChildActivityName|xs:string|Имя отменяемого действия.|  
|ChildActivityId|xs:string|Идентификатор отменяемого действия.|  
|ChildActivityInstanceId|xs:string|Идентификатор экземпляра отменяемого действия.|  
|ChildActivityTypeName|xs:string|Тип отменяемого действия.|  
|Заметки|xs:string|Заметки, добавленные к этому событию.  Значения хранятся в XML-элемент в формате \<элементы >\< имя элемента = «annotationName» type="System.String" > annotationValue\</item > \< /items >.  Если не задано никаких заметок, строка содержит \<элементов / >. Размер событий ETW ограничен размером буфера ETW или максимальным размером полезных данных для события ETW. Если размер события превышает пределы трассировки событий Windows, то событие усекается путем отбрасывания заметок и замены значения заметок значением \<элементы >...  \< /items >.|  
|ProfileName|xs:string|Имя или профиль отслеживания, который привел к созданию этого события.|  
|HostReference|xs:string|Для служб, размещенных на веб-сайтах, это поле служит уникальным идентификатором службы в веб-иерархии.  Формат определяется как "виртуальный путь приложения имя веб-сайта&#124;виртуальный путь службы&#124;ServiceName" Пример: "По умолчанию веб-сайт/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService"|  
|Домен приложения|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|
