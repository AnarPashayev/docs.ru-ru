---
title: Счетчики производительности операций
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916205"
---
# <a name="operation-performance-counters"></a>Счетчики производительности операций
При просмотре с помощью системного монитора (Perfmon.exe) счетчики производительности операций находятся под объектом производительности `ServiceModelOperation 4.0.0.0`. Каждая операция содержит отдельный экземпляр. Следовательно, если указанный контракт имеет 10 операций, 10 экземпляров счетчика операций связаны с этим контрактом. Экземпляры объекта именуются по следующей схеме:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Этот счетчик позволяет измерить, как используется вызов и насколько успешно выполняется операция.  
  
> [!CAUTION]
>  Длина имени экземпляра счетчика производительности ограничена. Имя экземпляра счетчика службы Windows Communication Foundation (WCF) превышает максимальную длину, WCF заменяет часть имени экземпляра значение хэша.  
  
## <a name="see-also"></a>См. также

- [Счетчики производительности](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
