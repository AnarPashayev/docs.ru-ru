---
title: Количество сбоев вызовов в секунду
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: aa8cd4c2d9f642b525b2b9ccb931c4f2101a5129
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421787"
---
# <a name="calls-failed-per-second"></a>Количество сбоев вызовов в секунду
Имя счетчика: Количество сбоев вызовов в секунду  
  
## <a name="description"></a>Описание  
 Количество вызовов с необработанными исключениями в данной операции в секунду.  
  
 Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Этого счетчика увеличивается при каждом обнаружении необработанного исключения в этой операции.  
  
## <a name="see-also"></a>См. также

- [Указание и обработка сбоев в контрактах и службах](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
