---
title: Сведения о реализации протокола служб данных WCF
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: a9b996671f2d8b57593f80fb13e966c5f03a2801
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190394"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Сведения о реализации протокола служб данных WCF

## <a name="odata-protocol-implementation-details"></a>Сведения о реализации протокола OData  

Open Data Protocol (OData) требует, чтобы служба данных, реализующая протокол, предустановила определенный минимальный набор функциональных возможностей. Эти функциональные возможности описаны в документах протокола в терминах «должен» и «требуется». Другие необязательные функции описаны в разделе «май». В этой статье описываются необязательные функции, которые в настоящее время не реализуются WCF Data Services.
  
### <a name="support-for-the-format-query-option"></a>Поддержка параметра запроса $format  

 Протокол OData поддерживает как нотацию JavaScript (JSON), так и веб-каналы Atom, а OData предоставляет `$format` параметр системного запроса, позволяющий клиенту запрашивать формат веб-канала ответа. Этот системный параметр запроса, если он поддерживается службой данных, должен переопределять значение заголовка Accept запроса. WCF Data Services поддерживает возврат обоих веб-каналов: JSON и Atom. Однако реализация по умолчанию не поддерживает параметр запроса `$format` и использует только значение заголовка Accept для определения формата ответа. Бывают случаи, когда службе данных необходимо поддерживать параметр запроса `$format`, например когда клиенты не могут задать заголовок Accept. В этом случае необходимо расширить службы данных для обработки этого параметра в URI.
  
## <a name="wcf-data-services-behaviors"></a>Поведение служб данных WCF  

 Следующие WCF Data Services поведения не определяются протоколом OData явным образом.  
  
### <a name="default-sorting-behavior"></a>Порядок сортировки по умолчанию  

 Если запрос, отправляемый в службу данных, включает системный параметр запроса `$top` или `$skip` и не включает системный параметр запроса `$orderby`, возвращаемый канал сортируется по ключевым свойствам в порядке возрастания. Это происходит потому, что упорядочение необходимо для правильного разбиения результатов на страницы. Для этого служба данных добавляет к запросу выражение упорядочения. Этот способ также используется в том случае, если в службе данных включено разбиение по страницам, управляемое сервером. Дополнительные сведения см. [в разделе Настройка службы данных](configuring-the-data-service-wcf-data-services.md). Чтобы управлять порядком возвращаемого веб-канала, необходимо включить его `$orderby` в URI запроса.  
  
## <a name="see-also"></a>См. также

- [Определение служб данных WCF](defining-wcf-data-services.md)
- [Библиотека клиентов служб данных WCF](wcf-data-services-client-library.md)
