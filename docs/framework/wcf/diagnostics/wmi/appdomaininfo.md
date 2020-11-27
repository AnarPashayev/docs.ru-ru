---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: c5c44f4d8f6d93443802d5e1950c4d850976c5b6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291132"
---
# <a name="appdomaininfo"></a>AppDomainInfo

Сведения о домене приложения  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Методы  

 Класс AppDomainInfo не определяет никакие методы.  
  
## <a name="properties"></a>Свойства  

 Класс AppDomainInfo имеет следующие свойства.  
  
### <a name="appdomainid"></a>AppDomainId  

 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Идентификатор домена приложения.  
  
### <a name="isdefault"></a>IsDefault  

 Тип данных: boolean  
  
 Тип доступа: только для чтения  
  
 Указывает, является ли домен приложения доменом приложения, используемым по умолчанию.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  

 Тип данных: boolean  
  
 Тип доступа: чтение/запись  
  
 Значение, указывающее, заносятся ли в журнал неправильные сообщения.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  

 Тип данных: boolean  
  
 Тип доступа: чтение/запись  
  
 Значение, указывающее, трассируются ли сообщения на уровне службы (перед шифрованием и преобразованиями, связанными с транспортом).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  

 Тип данных: boolean  
  
 Тип доступа: чтение/запись  
  
 Значение, указывающее, трассируются ли сообщения на уровне транспорта.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  

 Тип данных: массив TraceListener  
  
 Тип доступа: только для чтения  
  
 Коллекция прослушивателей трассировки, которые ожидают передачи данных источнику трассировки System.Wmi.MessageLogging.  
  
### <a name="name"></a>name  

 Тип данных: строка  
  
 Тип доступа: только для чтения  
  
 Имя домена приложения.  
  
### <a name="performancecounters"></a>PerformanceCounters  

 Тип данных: строка  
  
 Тип доступа: только для чтения  
  
 Область активных счетчиков производительности в домене приложения.  
  
### <a name="processid"></a>ProcessId  

 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Идентификатор процесса.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  

 Тип данных: строка  
  
 Тип доступа: только для чтения  
  
 Путь к конфигурации службы.  
  
### <a name="tracelevel"></a>TraceLevel  

 Тип данных: строка  
  
 Тип доступа: чтение/запись  
  
 Уровень трассировки источника трассировки System.Wmi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  

 Тип данных: массив TraceListener  
  
 Тип доступа: только для чтения  
  
 Коллекция прослушивателей, ожидающих передачи данных от источника трассировки System.ServiceModel.  
  
## <a name="requirements"></a>Требования  
  
|MOF|Объявлено в файле Servicemodel.mof.|  
|---------|-----------------------------------|  
|Пространство имен|Определено в root\ServiceModel.|
