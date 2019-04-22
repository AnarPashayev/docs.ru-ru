---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 16bfea37a5742ac5aaaabfacdcf03a2b5bedb6db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819285"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Указывает ли 64-разрядный исполняемый файл или исполняемый файл, помеченный атрибутом [/Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) параметр компилятора поддерживает технологию Address Space макета Randomization (ASLR) с высокой энтропией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Аргументы  
 `+` &#124; `-`  
 Необязательный параметр. Параметр — off по умолчанию или если вы укажите `-highentropyva-`. Параметр — Если вы укажите `-highentropyva` или `-highentropyva+`.  
  
## <a name="remarks"></a>Примечания  
 Если этот параметр указан, совместимым версиям ядра Windows можно использовать более высокие степени энтропии, когда ядро случайный выбор из своего структуры адресного пространства процесса в рамках ASLR. Если ядро использует более высокие степени энтропии, большее количество адресов может быть выделено для областей памяти как стеки и кучи. Из-за этого сложнее подобрать расположение определенной области памяти.  
  
 При включен этот параметр, целевой исполняемый файл и все модули, на которых она зависит, должен быть способен обработать значения указателя, размер которых превышает 4 гигабайта (ГБ), если эти модули выполняются как 64-разрядных процессов.  
  
## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)
- [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
