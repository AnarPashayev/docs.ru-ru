---
title: 'Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность'
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287557"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность

Чтобы обеспечить возврат клиентскому приложению самого актуального содержимого, в результате взаимодействия политики кэша клиента и требований к повторной проверке сервера всегда применяется наиболее консервативная политика кэша. Все примеры в этом разделе иллюстрируют политику кэша для ресурса, который кэшируется 1 января и срок действия которого истекает 4 января.  
  
 В приведенных ниже примерах показана политика кэша, полученная в результате сочетания значений максимального возраста (`maxAge`) и минимальной актуальности (`minFresh`).  
  
- Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` не указано, содержимое повторно проверяется 3 января.  
  
- Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` равным 1 дню, то в соответствии с `maxAge` содержимое будет актуальным до 3 января. Согласно `minFresh` содержимое будет актуально до 3 января. Поэтому его необходимо будет проверить повторно 3 января.  
  
- Если политика кэша задает значение `maxAge` равным 2 дням и значение `minFresh` равным 2 дням, то в соответствии с `maxAge` содержимое будет актуальным до 3 января. Согласно `minFresh` содержимое будет актуально до 2 января. Поэтому его необходимо будет проверить повторно 2 января.  
  
## <a name="see-also"></a>См. также раздел

- [Управление кэшем для сетевых приложений](cache-management-for-network-applications.md)
- [Политика кэша](cache-policy.md)
- [Политики кэша на основе расположения](location-based-cache-policies.md)
- [Политики кэша на основе времени](time-based-cache-policies.md)
- [Настройка кэширования в сетевых приложениях](configuring-caching-in-network-applications.md)
- [Взаимодействие с политикой кэша: максимальный возраст и устаревание](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
